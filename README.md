# Week 4 Starter: Math Agent

A ReAct agent that solves questions using tool calls.

## Setup

1. Install [uv](https://docs.astral.sh/uv/getting-started/installation/) if you don't have it.

2. Copy `.env.example` to `.env` and add your API key:
   ```bash
   cp .env.example .env
   ```
   Then edit `.env` and replace `your-key-here` with your key from [Google AI Studio](https://aistudio.google.com/apikey).

   To use a different provider, change the `MODEL` variable in `agent.py` and set the matching key in `.env`.

3. Make sure `.env` is in your `.gitignore` so you don't commit your key.

## Run

```bash
uv run agent.py
```

uv will install dependencies automatically on first run.

The agent will work through each question in `math_questions.md` and print the ReAct trace (Reason / Act / Result) for each one.

## Files

- `agent.py` - the ReAct agent (this is the file you'll modify)
- `calculator.py` - calculator tool
- `products.json` - product catalog with prices
- `math_questions.md` - the questions the agent solves
- `.env.example` - template for your API key

## Demo Video

Watch the demo here: https://youtu.be/VcmiOrkoxYo

## Final Implementation Notes

- The `product_lookup` tool is now fully implemented in `agent.py` as required by the assignment. It reads `products.json`, looks up the product name exactly as provided, and returns the price as a string or a helpful message listing available products if not found.
- The `@agent.tool_plain` decorator is used directly above the function, and the implementation uses `json` from the existing import.
- No changes were made to `calculator_tool`, `load_questions`, `main`, or the system prompt except as required for the new tool.
- `.env` and API keys are not modified or included in the codebase.
- To run the agent and see the ReAct trace for each question, use:
  ```bash
  uv run agent.py
  ```
- The agent will automatically use both the calculator and product lookup tools as needed to answer questions in `math_questions.md`.
