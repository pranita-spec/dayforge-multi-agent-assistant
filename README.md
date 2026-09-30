# DayForge — AI Multi-Agent Workday Automator

A chat-based personal assistant that runs your inbox and calendar through a team of AI agents. You tell it what you need in plain language, a master agent works out what the request involves, and specialist agents for email and calendar carry it out.

**Built with:** n8n · Google Gemini 2.5 Flash · Gmail · Google Calendar · AI Agent tools · Conversation memory

---

## The Problem
Professionals lose time jumping between email and calendar for small, repetitive tasks: checking availability, replying to a thread, drafting a message, moving a meeting. Each one is quick on its own, but together they eat into the day.

## What It Does
1. **Chat trigger:** The user sends a request in plain language, e.g. *"Find a free slot tomorrow afternoon and email Rahul to confirm."*
2. **Master orchestrator:** A Gemini-powered agent with memory understands the request and decides which specialist agent (or both) should handle it.
3. **Email agent:** Handles Gmail through 5 tools: send, reply, forward, draft and delete.
4. **Calendar agent:** Handles Google Calendar through its tools: get events, check availability, create, update and delete events, plus a date and time tool for relative dates like "next Monday".
5. **Response:** The orchestrator combines the results and replies to the user in the chat.

Each agent keeps its own conversation memory, so follow-up requests like *"move that meeting to 4 pm"* work without repeating context.

## Architecture
![Workflow diagram](diagram.png)

**Pattern:** hierarchical multi-agent. The master agent routes, and the sub-agents execute.

## Key Design Decisions
- **Separation of responsibilities:** each agent has a narrow set of tools, which keeps prompts short and reduces wrong tool calls.
- **Agents as tools:** the email and calendar agents are exposed to the orchestrator as tools, so new specialists can be added without changing the core flow.
- **AI-filled tool parameters:** recipients, subjects, times and event details are filled in by the model from the conversation.

## Files
- `dayforge.json` — n8n workflow export (credentials replaced with placeholders)
- `diagram.png` — architecture diagram

## Setup
1. Import `dayforge.json` into n8n.
2. Connect your own Gmail, Google Calendar and Google Gemini credentials.
3. Open the chat and send a request.

---
Built by **Pranita Priya**, n8n & AI Automation Builder
