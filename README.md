# 🤖 AutoStream AI Customer Support Chatbot

An intelligent customer support chatbot for **AutoStream** — a video automation SaaS platform. Built with Python, OpenAI GPT-4o-mini, and LangGraph, it handles pricing queries, policy questions, and lead capture.

---

## ✨ Features

- 🧠 **Intent Detection** — Identifies greetings, pricing queries, policy questions, and high-intent purchase signals
- 📚 **RAG (Retrieval-Augmented Generation)** — Returns instant answers from a structured knowledge base
- 💬 **LLM Fallback** — Uses GPT-4o-mini for general questions not covered by the knowledge base
- 🎯 **Lead Capture Flow** — Collects name, email, and platform when a user shows purchase intent
- 🔁 **Retry with Exponential Backoff** — Handles OpenAI rate limits gracefully

---

## 🗂️ Project Structure

```
AutoStream-Chatbot/
├── Final_Assignment.ipynb   # Main Jupyter Notebook
├── requirements.txt         # Python dependencies
├── .gitignore               # Files to exclude from Git
└── README.md                # Project documentation
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/AutoStream-Chatbot.git
cd AutoStream-Chatbot
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Add Your OpenAI API Key

Open `Final_Assignment.ipynb` and replace the placeholder:

```python
client = OpenAI(api_key="YOUR_OPENAI_API_KEY_HERE")
```

> ⚠️ **Never commit your real API key to GitHub!**

### 4. Run the Notebook

Open in Jupyter or Google Colab and run all cells.

---

## 🧠 How It Works

```
User Input
    │
    ▼
Intent Detection (rule-based keyword matching)
    │
    ├── greeting   → "Hi! Ask me anything about AutoStream 😊"
    ├── pricing    → Returns plans from Knowledge Base
    ├── policy     → Returns refund/support policy
    ├── high_intent → Triggers Lead Capture Flow
    │                    └── Collects Name → Email → Platform
    └── general    → Calls GPT-4o-mini via OpenAI API
```

---

## 💰 Knowledge Base (Sample)

| Plan  | Price      | Videos     | Resolution | Extras        |
|-------|------------|------------|------------|---------------|
| Basic | $29/month  | 10/month   | 720p       | —             |
| Pro   | $79/month  | Unlimited  | 4K         | AI Captions   |

**Policies:**
- Refund: No refunds after 7 days
- Support: 24/7 support on Pro plan only

---

## 📦 Dependencies

- `openai` — GPT-4o-mini API calls
- `langgraph` — Agent state graph management
- `python-dotenv` *(optional)* — For managing API keys via `.env`

---

## ⚠️ Known Issue & Fix

The notebook has a bug in intent detection:

```python
# BUG: "which" triggers greeting intent
if any(word in text.lower() for word in ["hi", "hello", "hey", "hy"]):
```

> Fix: Use whole-word matching or restructure conditions to avoid partial matches.

---

## 🛡️ Security Note

- **Do NOT push your OpenAI API key** to GitHub.
- Use environment variables or a `.env` file instead:

```python
import os
from dotenv import load_dotenv
load_dotenv()
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
```

---

## 📄 License

MIT License — feel free to use and modify.
