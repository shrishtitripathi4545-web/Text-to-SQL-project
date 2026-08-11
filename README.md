# Text-to-SQL Chatbot

## Overview
A conversational interface that lets you query a database in plain English instead of writing SQL by hand. Type a question like "how many customers churned last quarter?" and the app translates it into a real SQL query, runs it, and returns the answer in natural language — with the generated SQL shown alongside it for transparency.

## Motivation
As someone with a strong SQL background, I wanted to explore how LLMs handle schema-aware query generation — specifically, how reliably a model can translate ambiguous natural language into correct, executable SQL, and where it tends to get things wrong.

## Tech Stack
- **Language:** Python
- **LLM orchestration:** LangChain (SQL Toolkit / SQL Agent)
- **LLM provider:** Groq (fast inference, free tier)
- **Database:** SQLite
- **Interface:** Streamlit

## How It Works
1. The app connects to a SQLite database and reads its schema (table names, columns, relationships).
2. A user question is passed to the LLM along with the schema as context.
3. LangChain's SQL agent generates a candidate SQL query, executes it against the database, and returns the result.
4. Both the natural-language answer and the underlying SQL query are displayed, so the query is auditable rather than a black box.

## Dataset
[Fill in — e.g., "Adapted to run against the Telco customer churn dataset (customers, contracts, churn_status tables) instead of the original demo database, to test the agent on schema and business questions I'm already familiar with."]

## Setup & Run
```bash
git clone <your-repo-url>
cd text-to-sql-project
pip install -r requirements.txt
```
Add your Groq API key (get one free at console.groq.com) to a `.env` file:
```
GROQ_API_KEY=your_key_here
```
Then run:
```bash
streamlit run app.py
```

## What I Adapted
- [Fill in once done — e.g., swapped database, added SQL display toggle, changed prompt template for better accuracy on a specific query type]

## Limitations
- Struggles with highly ambiguous or multi-step questions requiring joins across several tables
- Accuracy depends heavily on how descriptive the schema/column names are

## Future Work
- Add query result caching for repeated questions
- Extend to support MySQL/PostgreSQL in addition to SQLite
