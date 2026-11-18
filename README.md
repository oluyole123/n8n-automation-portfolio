# n8n Automation Portfolio

Production-style AI and automation workflows built with [n8n](https://n8n.io). Each workflow is exported as JSON in the [`workflows`](./workflows) folder with credentials and sensitive values replaced by placeholders.

## Workflows

### 1. USA LawRipple
Daily briefing on new US federal laws. Runs every morning at 9 AM Florida time, pulls new laws from the Federal Register API, and uses AI models via OpenRouter to normalize each law and analyze its downstream "ripple" effects. It formats the result and sends it to Telegram.
**Tools:** n8n, Federal Register API, OpenRouter, Telegram

### 2. Tender and Grant Proposal Pipeline
Turns an incoming tender or grant opportunity into a draft proposal. A webhook receives the opportunity, checks whether it was already seen, and loads the company profile and proposal library. AI extracts the requirements, scores the fit, and decides whether it is worth pursuing. Good fits get an AI-drafted proposal, a task list, and a CSV export. Poor fits are logged as skipped.
**Tools:** n8n, AI agents with structured output, data tables, webhooks

### 3. Canada Grad School Fee Waivers, Scholarships and Funding to Telegram
A weekly research agent. It builds search queries, uses an AI agent to search the web for application fee waivers, scholarships, and funding, then parses, de-duplicates, and formats the results and sends them to Telegram.
**Tools:** n8n, AI agent with web search, Telegram

### 4. RAG Knowledge Base using Supabase (PDF Retriever)
A question-answering system over uploaded PDFs. One flow ingests a PDF, splits the text, creates OpenAI embeddings, and stores them in a Supabase vector store. A second flow takes a question by webhook, retrieves the most relevant chunks, and answers with GPT-4o mini, with a fallback handler for failures.
**Tools:** n8n, Supabase vector store, OpenAI embeddings, GPT-4o mini, webhooks

### 5. Supabase Outreach
Automated daily lead outreach. It finds contacts with Hunter.io domain search, pulls queued leads from Supabase, and claims each lead so nobody is emailed twice. New leads get an email from Gmail, and each record is marked sent or failed.
**Tools:** n8n, Hunter.io, Supabase, Gmail

### 6. Insurance Claims Triage
Handles incoming insurance claims end to end. A webhook receives a claim, which is validated and checked for duplicates. The workflow looks up the policy, uses AI to extract claim facts, scores and routes the claim, saves it, adds it to a review queue, and logs every step. Depending on the result, it drafts an evidence request email or a policy hold email in Gmail.
**Tools:** n8n, AI structured extraction, data tables, Gmail, webhooks

### 7. AI Automation Intern Entry (USA, Canada, Australia, NZ, Ireland)
A job alert bot. Every morning at 8 AM WAT it pulls listings from the RemoteOK, Remotive, and Arbeitnow APIs, merges them, filters for entry-level and intern AI automation roles, and sends matches to Telegram.
**Tools:** n8n, public job APIs, Telegram

### 8. EasyKOL Scrubber
Cleans and de-duplicates influencer (KOL) lists. A webhook accepts an uploaded Excel file, the workflow reads the spreadsheet, a code step cleans and filters the rows, valid rows are saved to Supabase with automatic de-duplication, and the cleaned data is returned to the caller as a CSV file.
**Tools:** n8n, webhooks, Supabase, spreadsheet and CSV conversion

## How to import a workflow

1. Open a file in the `workflows` folder and click **Download raw file**.
2. In n8n, create a new workflow, open the three-dot menu, and choose **Import from file**.
3. Connect your own credentials in each node that needs them.

## Notes

- Credentials, API keys, tokens, webhook URLs, chat IDs, and email addresses have been removed or replaced with placeholders such as `YOUR_API_KEY`.
- Some workflows need accounts with the services listed above (Supabase, OpenRouter, Hunter.io, and so on).

## Contact

**Benjamin Ikuemuya**
Email: ikuemuyabenjamin@gmail.com
LinkedIn: [benjamin-ikuemuya](https://www.linkedin.com/in/benjamin-ikuemuya-744a05260)
