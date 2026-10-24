# Edgar — SEC EDGAR Financial Statements API + MCP Server for AI Agents

Edgar is a free SEC EDGAR data API and Model Context Protocol (MCP) server for AI agents. It turns hard-to-use SEC filings data into clean, agent-ready tools and REST endpoints: standardized financial statements and metrics for US public companies, straight from their SEC filings.

**Free, no API key. 5 MCP tools.**

- **MCP endpoint (streamable HTTP):** https://edgar.morningbrief.link/mcp
- **REST base:** https://edgar.morningbrief.link — endpoints under `/v1/`
- **Product page:** https://morningbrief.link/edgar/
- **Docs:** https://morningbrief.link/docs
- **Hub:** https://morningbrief.link
- **MCP Registry listing:** `link.morningbrief/edgar`

> This repository is a discovery stub. Edgar runs remotely — there is nothing to install or self-host here, and no worker source code is included.

## Datasets

- Company directory — 8,000+ US public companies (ticker, CIK, name, SIC industry)
- Financial statements — standardized income, balance sheet and cash flow figures from SEC XBRL filings
- Metric history — revenue, net income, EPS and more, period by period
- Rankings — companies ranked by any reported metric
- Industries — company counts and browsing by SIC industry

Data is SEC-only, as reported in each company's filings. When a filing restates an earlier year, the restated figure wins. When the SEC doesn't have a figure, Edgar says so instead of guessing — no data beats misleading data. Financial coverage loads progressively, largest companies first.

## All 5 MCP tools

**Companies & financials (SEC EDGAR)**

| Tool | What it does |
|------|--------------|
| `search_companies` | Search the company directory by name/ticker text or SIC industry |
| `get_company` | One company's directory record and loaded financial coverage, by ticker or CIK |
| `get_financials` | Standardized financial statements for one company |
| `get_metric_history` | Time series of one metric (e.g. revenue) for one company |
| `list_financial_concepts` | Concept keys available for metric queries and rankings |

## Connect via MCP

Add Edgar to any MCP client with this config:

```json
{
  "mcpServers": {
    "edgar": {
      "url": "https://edgar.morningbrief.link/mcp"
    }
  }
}
```

Claude Code CLI:

```bash
claude mcp add --transport http edgar https://edgar.morningbrief.link/mcp
```

Any MCP client, and ChatGPT custom connectors, can use the same URL: `https://edgar.morningbrief.link/mcp`

## REST examples

```bash
curl "https://edgar.morningbrief.link/v1/companies/search?q=nvidia"
curl "https://edgar.morningbrief.link/v1/financials/leaders?concept=revenue&limit=5"
curl "https://edgar.morningbrief.link/v1/financials/metric?ticker=NVDA&concept=revenue"
```

Full documentation: https://morningbrief.link/docs

## The Morning Brief API family

Edgar is one of three free, no-key data APIs from [Morning Brief](https://morningbrief.link):

- **Magpie** — USDA farm market data (grain, fertilizer, WASDE, export sales): https://ag.morningbrief.link
- **Farmland** — USDA land values & cash rents: https://land.morningbrief.link
- **Edgar** — SEC company financials: https://edgar.morningbrief.link
