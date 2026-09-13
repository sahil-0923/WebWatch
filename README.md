# 🌐 WebWatch — Self-Hosted Web Page Change Detection & Alerting

**WebWatch** is a powerful, privacy-first, self-hosted web monitoring tool that automatically detects changes on websites and sends instant real-time alerts.

Monitor price changes, stock availability, content edits, PDF changes, and JSON APIs with granular filters, visual element selection, and optional AI-powered summaries.

---

## ✨ Features

- 🎯 **Visual Element Selection** — Click and target specific elements, CSS selectors, or XPath without coding.
- 🤖 **AI-Powered Summaries & Smart Filters** — Connect OpenAI, Claude, Gemini, or local models (Ollama, vLLM) for plain-English diff summaries and noise reduction.
- 📦 **Restock & Price Tracking** — Built-in price extraction with custom triggers (e.g. alert when price drops below $50).
- 🔔 **Multi-Channel Notifications** — 90+ notification services supported via [Apprise](https://github.com/caronc/apprise) (Discord, Slack, Telegram, Email, Webhooks, Pushbullet, Teams, etc.).
- 📑 **PDF & Document Tracking** — Track text, filesize, and checksum changes inside PDF documents.
- ⚡ **JSON & API Monitoring** — Extract and evaluate structured data using `JSONPath` or `jq`.
- 🕒 **Custom Scheduling & Timezones** — Run checks on custom cron schedules, business hours only, or specific weekdays.
- 🔒 **100% Self-Hosted & Privacy-Focused** — All your watch URLs, history diffs, and credentials remain strictly on your own hardware.

---

## 🚀 Quick Start & Local Setup

### Option 1: Native Python (Windows / Linux / macOS)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/<YOUR_USERNAME>/WebWatch.git
   cd WebWatch
   ```

2. **Set up a Python Virtual Environment:**
   ```bash
   # Windows (PowerShell)
   python -m venv venv
   .\venv\Scripts\Activate.ps1

   # Linux / macOS
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Start the WebWatch server:**
   ```bash
   python changedetection.py -d ./datastore -p 5000 -C
   ```

5. **Open in your browser:**
   Navigate to **[http://localhost:5000](http://localhost:5000)**.

---

### Option 2: Docker / Docker Compose

Run using Docker Compose:

```bash
docker compose up -d
```

Or using standalone Docker:

```bash
docker run -d \
  --name webwatch \
  --restart always \
  -p 5000:5000 \
  -v webwatch-data:/datastore \
  ghcr.io/dgtlmoon/changedetection.io:latest
```

---

## ⚙️ Configuration & Capabilities

### 🤖 AI Change Detection & Summaries
Connect your preferred LLM provider in **Settings → AI / LLM**:
- **Cloud Providers**: OpenAI (GPT-4o), Anthropic (Claude), Google Gemini Flash.
- **Local / Self-Hosted**: Ollama, vLLM, LM Studio, llama.cpp via OpenAI-compatible endpoints.

### 🔔 Notification Examples
In any watch's **Notification** settings, configure URLs like:
```text
discord://webhook_id/webhook_token
slack://TokenA/TokenB/TokenC
tgram://bot_token/chat_id
mailto://user:pass@smtp.example.com?to=alerts@example.com
json://yourserver.com/api/webhook
```

### 🧩 API Access
WebWatch provides a complete REST API:
- Manage watches, tags, and notifications programmatically.
- Access API documentation directly inside the settings dashboard.
- Authenticate requests using the `x-api-key` header.

---

## 🛡️ Attribution

This project is derived from the open-source [changedetection.io](https://github.com/dgtlmoon/changedetection.io) project.
