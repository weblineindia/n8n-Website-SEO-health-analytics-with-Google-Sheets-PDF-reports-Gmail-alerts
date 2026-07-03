# Automated SEO Health Monitoring & Reporting

This workflow automatically monitors the SEO health of websites stored in a Google Sheet. It fetches each website’s HTML, analyzes key SEO metrics (title, meta description, H1 count, canonical, robots, performance score, etc.) and updates results back into Google Sheets. If performance is poor (<50), it sends an alert email. For healthy sites, it generates a detailed PDF report and stores it in Google Drive.

## Who’s It For

- Digital marketing teams
- SEO agencies
- Website administrators who want automated SEO health checks
- Businesses with multiple websites or landing pages to monitor

## How It Works

1. **Daily Trigger** – Runs every day at 9 AM.
2. **Fetch Website List** – Reads website URLs from Google Sheets.
3. **Crawl Websites** – Uses HTTP requests to fetch each website’s HTML.
4. **SEO Analysis** – Extracts SEO-related metadata (title, meta description, H1, etc.).
5. **Health Check** – Scores SEO performance based on predefined rules.
6. **Decision Node** – If score < 50 → Send alert email; else → Generate full SEO report.
7. **Update Logs** – Logs results back into Google Sheets.
8. **Generate PDF Reports** – Converts HTML reports into PDFs via [PDF.co](http://PDF.co) API.
9. **Save to Drive** – Stores the PDF reports in Google Drive for long-term access.

## How to Set Up

1. Open n8n and import the workflow.
2. Configure your **Google Sheets** credentials and specify the sheet containing your website URLs.
3. Add your **Gmail** account to allow automated alert emails.
4. Set up your **Google Drive** credentials for storing PDF reports.
5. Obtain an **API key from [PDF.co](http://PDF.co)** and configure the HTTP Request node.
6. Adjust the **Schedule Trigger** to the time that works best (default: 9 AM daily).
7. Test the workflow with a sample domain list.

## Requirements

- **[**n8n Account (Self-hosted or Cloud)**](https://n8n.partnerlinks.io/om1efg2qgvwi)**
- Google Sheets account (to store website URLs and logs)
- Gmail account (for sending alerts)
- Google Drive account (to save SEO reports)
- [PDF.co](http://PDF.co) API Key (for HTML → PDF conversion)

## How to Customize

- **Change performance threshold**: Modify the IF node condition (default <50).
- **Custom SEO rules**: Edit the **SEO Health Check** Function node to add/remove checks (e.g., missing schema tags, page load times).
- **Different output storage**: Replace Google Drive with Dropbox, S3 or OneDrive.
- **Alternate notification channels**: Swap Gmail with Slack, Microsoft Teams or Telegram.

## Add-Ons

- Send Slack/Teams notifications for low scores.
- Add PageSpeed Insights API for performance scoring.
- Generate weekly summary reports per domain.
- Integrate with Notion/Confluence to log SEO health history.

## Use Case Examples

- An SEO agency monitors **100+ client websites** daily and sends alerts when a site has poor SEO signals.
- A company’s **marketing manager** gets a daily SEO health PDF report stored in Drive.
- A SaaS product team automatically logs performance changes for each release.

## Common Troubleshooting

| **Issue** | **Possible Cause** | **Solution** |
|-----------|--------------------|--------------|
| Workflow fails at **HTTP Crawl** | Website blocks requests / timeout | Increase timeout in Set Config node or add retry logic. |
| Always returns `https://example.com` | Missing canonical / OG tags in HTML | Enhanced code now infers from JSON-LD or domain detection. Update analyzer. |
| PDF not generated | Invalid API key or wrong endpoint in **PDF.co** node | Verify **PDF.co** API key and endpoint URL. |
| Email not sending | Gmail credentials not set or blocked | Reconnect Gmail in n8n credentials manager. |
| Google Sheet not updating | Wrong column mapping in Update Sheet node | Check node mapping: domain column vs performance/date columns. |
| Google Drive upload fails | Missing folder permissions | Ensure correct Drive folder ID and credentials. |

## Need Help?

If you need help customizing this workflow, integrating advanced SEO monitoring, or extending it with reporting dashboards and third-party SEO tools, our **WeblineIndia** team is ready to assist. Explore our **[Process Automation Solutions](https://www.weblineindia.com/process-automation-solutions.html)** or connect with our **[n8n workflow development experts](https://www.weblineindia.com/hire-n8n-developers/)** to build, customize, and scale your business automation with confidence.
