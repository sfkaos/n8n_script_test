# 🧪 n8n Technical Challenge: Scrape LinkedIn for Account Managers at Deloitte

## 📍 Overview

The goal is to demonstrate your ability to:

- Orchestrate flows using n8n
- Automate login and authenticated scraping with Puppeteer
- Extract structured data from real-world, JavaScript-heavy websites (LinkedIn)

---

## 🎯 Your Task

Build an **n8n workflow** that performs the following steps:

1. **Webhook Input**

Starts with a `Webhook` node that accepts a POST request with:

```json
{
  "email": "your-linkedin-email@example.com",
  "password": "your-linkedin-password",
  "company": "Deloitte"
}
```

2. **Login with Puppeteer**

Uses Puppeteer (inside an `Execute Command` node or external script) to:

- Open a headless browser (using a free account at [Browserless.io](https://www.browserless.io))
  - [Browserless documentation](https://docs.browserless.io/baas/start)
- Navigate to [https://www.linkedin.com/login](https://www.linkedin.com/login)
- Log in with the credentials provided

3. **Search LinkedIn**

After successful login, perform a search on LinkedIn for:

```
account manager Deloitte
```

Navigate to the “People” tab of the results.

4. **Scrape Results**

Extract the **first 10 people** in the search results, collecting:

- Full Name
- Headline (e.g., "Account Director at Deloitte")
- Profile URL

5. **Return JSON**

Return the scraped data back through the webhook as a structured JSON array like:

```json
[
  {
    "name": "Jane Doe",
    "headline": "Senior Account Manager at Deloitte",
    "profileUrl": "https://www.linkedin.com/in/janedoe/"
  },
  ...
]
```

---

## 📦 Deliverables

Please submit the following:

1. ✅ Exported n8n workflow file (`.json`)
2. ✅ Any external Puppeteer scripts (e.g., `linkedinSearch.js`)
3. ✅ A brief README or comment block explaining:

   - Any assumptions made
   - Issues encountered (e.g., captchas, bot protection)
   - How the workflow could be extended or generalized

---

## ⏱ Time Limit

You should aim to complete this challenge in **under 60 minutes**.

---

## ✅ Evaluation Criteria

| Criteria                                              | Points |
| ----------------------------------------------------- | ------ |
| Reliable LinkedIn login with Puppeteer                | 20     |
| Navigation to People search results                   | 20     |
| Scrapes correct structured data                       | 25     |
| Returns clean JSON output                             | 15     |
| Workflow clarity and modularity                       | 15     |
| Bonus: Search term input support or scroll/pagination | +5     |

---

## ⚠️ Notes

- This test uses LinkedIn.com — you may use your own LinkedIn account or a new free account for testing.
- Be mindful of LinkedIn's rate limits, captchas, or anti-bot measures. For this test, a short burst of scraping is fine.
- If you encounter blockers (e.g., captcha walls), include a short explanation of what you'd do in production to handle them (e.g., proxy rotation, session reuse, Puppeteer stealth plugins, etc.)

---

## 🙌 Good Luck!

This task is meant to simulate real-world challenges you'd solve on the job. We’re excited to see how you approach it!
