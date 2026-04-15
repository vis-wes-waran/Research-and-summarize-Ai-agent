Here is a professional and clean **README.md** tailored for your project. It breaks down the architecture, setup, and usage in a way that is easy for others to follow.

---

# 🤖 AI Research Assistant & Emailer

An automated pipeline built with **LangChain** and **Groq- gpt-oss-120b
** that researches academic papers on **arXiv**, generates beginner-friendly summaries, and automatically emails the results to a specified recipient.

---

## 🚀 Overview

This agent acts as an end-to-end research assistant. By combining Large Language Models (LLMs) with specialized tools, it can:
1.  **Search:** Query the arXiv database for specific scientific papers.
2.  **Analyze:** Synthesize complex technical papers into simple summaries.
3.  **Communicate:** Send the final report via email using SMTP.

---

## 🛠️ Architecture

The project utilizes the **LangChain AgentExecutor** framework to manage a reasoning loop:
* **LLM:** OpenAI GPT-4o (or GPT-4).
* **Tools:**
    * `tool_arxiv_search`: Connects to the Arxiv API to fetch paper metadata and abstracts.
    * `send_mail`: A custom Python tool using `smtplib` and `MIMEText`.
* **Prompting:** Uses the `openai-functions-agent` logic for reliable tool calling.

---

## 📋 Prerequisites

* **Python 3.8+**
* **Groq API Key**
* **Gmail App Password:** To use the email tool, you must enable 2-Step Verification on your Gmail account and generate an **[App Password](https://support.google.com/accounts/answer/185833?hl=en)**.

---

## ⚙️ Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/ai-research-emailer.git
   cd ai-research-emailer
   ```

2. **Install dependencies:**
   ```bash
   pip install langchain langchain-openai langchain-community arxiv
   ```

---

## 📄 Code Structure

The core logic is divided into three sections:

### 1. The Email Tool
Uses `smtplib` to connect to Gmail's SMTP server. 
> **Note:** The sender's credentials must be configured within the function or pulled from environment variables.

### 2. The Research Tool
Wraps `ArxivAPIWrapper` to handle rate-limiting and query the scientific database.

### 3. The Agent Agent
Combines the tools into an `AgentExecutor` that follows a strict sequence:
1. `arXiv Search` $\rightarrow$ 2. `Summarization` $\rightarrow$ 3. `Email Delivery`.

---

## 🖥️ Usage

Simply run the script. The agent is prompted to research the **VGG16** paper and email the summary:

```python
agent_executor.invoke({
    "input": "Search for the VGG16 paper, summarize it, and email it to nostalgic1235@gmail.com"
})
```

---

## ⚠️ Security Warning

**Never**  hardcode your actual Gmail password or API keys in the `README.md` or the source code. Always use:
* **Environment Variables:** `os.getenv("EMAIL_PASS")`
* **Secret Management:** `.env` files (added to `.gitignore`)

---

## 📜 License

This project is licensed under the MIT License. Feel free to use and modify it for your own research automation!
