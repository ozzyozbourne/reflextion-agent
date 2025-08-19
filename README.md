# Reflexion Agent with LangGraph 🦜🕸️

Implementation of a sophisticated Reflexion agent using LangGraph and LangChain, designed to generate high-quality responses through self-reflection and iterative improvement.

This project demonstrates advanced AI agent capabilities using LangGraph's state-of-the-art control flow mechanisms for self-reflection and response refinement.

```mermaid
---
config:
  flowchart:
    curve: linear
---
graph LR;
        __start__([<p>__start__</p>]):::first
        draft(draft)
        execute_tools(execute_tools)
        revise(revise)
        __end__([<p>__end__</p>]):::last
        __start__ --> draft;
        draft --> execute_tools;
        execute_tools --> revise;
        revise -.-> draft;
        revise -.-> execute_tools;
        revise -.-> __end__;
        classDef default fill:#f2f0ff,line-height:1.2
        classDef first fill-opacity:0
        classDef last fill:#bfb6fc
```
## Features

- **Self-Reflection**: Implements sophisticated reflection mechanisms for response improvement
- **Iterative Refinement**: Uses a graph-based approach to iteratively enhance responses
- **Production-Ready**: Built with scalability and real-world applications in mind
- **Integrated Search**: Leverages Tavily search for enhanced response accuracy
- **Structured Output**: Uses Pydantic models for reliable data handling

## Architecture

The agent uses a graph-based architecture with the following components:

- **Entry Point**: `draft` node for initial response generation
- **Processing Nodes**: `execute_tools` and `revise` for refinement
- **Maximum Iterations**: 2 (configurable)
- **Chain Components**: First responder and revisor using GPT-4
- **Tool Integration**: Tavily Search for web research

## Environment Variables

To run this project, you will need to add the following environment variables to your .env file:

```bash
OPENAI_API_KEY=your_openai_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here
LANGCHAIN_API_KEY=your_langchain_api_key_here  # Optional, for tracing
LANGCHAIN_TRACING_V2=true                      # Optional
LANGCHAIN_PROJECT=reflexion agent               # Optional
```

> **Important Note**: If you enable tracing by setting `LANGCHAIN_TRACING_V2=true`, you must have a valid LangSmith API key set in `LANGCHAIN_API_KEY`. Without a valid API key, the application will throw an error. If you don't need tracing, simply remove or comment out these environment variables.

## Run Locally

Clone the project:

```bash
git clone <repository-url>
cd reflexion-agent
```

Install dependencies:

```bash
poetry install
```

Start the agent:

```bash
poetry run python main.py
```

## Development Setup

1. Get your API keys:
   - [OpenAI Platform](https://platform.openai.com/) for GPT-4 access
   - [Tavily](https://tavily.com/) for search functionality
   - [LangSmith](https://smith.langchain.com/) (optional) for tracing

2. Copy the example environment file:
   ```bash
   cp .env.example .env
   ```

3. Edit `.env` with your API keys

## Running Tests

To run tests, use the following command:

```bash
poetry run pytest . -s -v
```

## Acknowledgements

This project builds upon:
- [LangGraph](https://langchain-ai.github.io/langgraph/tutorials/reflexion/reflexion/) for agent control flow
- [LangChain](https://github.com/langchain-ai/langchain) for LLM interactions
- [Tavily API](https://tavily.com/) for web search capabilities
