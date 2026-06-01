# @veyralabs/shopify-suite

Two Claude Code skills covering the full Shopify stack - one for developers, one for merchants.

## Skills

### shopify-dev

Shopify development across all layers: Liquid themes, JSON templates, section schemas, app development with Remix, Storefront and Admin GraphQL APIs, CLI workflows, checkout extensions, and Hydrogen headless.

Fetches live Shopify documentation via Context7 before answering API or version-sensitive questions. Shopify deprecates APIs every quarter.

Modes: `theme` / `app` / `api` / `cli` / `hydrogen` / `debug`

### shopify-store

Store audit and optimization. Detects available data source automatically:

**Mode A - MCP Connected:** Reads real store data via [shopify-mcp](https://github.com/GeLi2001/shopify-mcp) - products, collections, orders, installed apps, metafields. Full audit with actual numbers.

**Mode B - Public extraction:** Uses Scrapling on the public storefront when MCP is not configured. Extracts navigation, loaded scripts (app detection), product page markup, meta tags, structured data, canonical URLs.

Audits 6 dimensions: product catalog, collection architecture, navigation, SEO, app stack, conversion signals.

## Installation

```bash
npx @veyralabs/skills install shopify-suite
```

Or install individually:

```bash
npx @veyralabs/skills install shopify-dev
npx @veyralabs/skills install shopify-store
```

After installation, skills are available in `.claude/skills/shopify-suite/`.
Slash commands `/shopify-dev` and `/shopify-store` appear in the Claude Code menu.

## Connecting shopify-mcp (store auditor Mode A)

```json
{
  "mcpServers": {
    "shopify": {
      "command": "npx",
      "args": [
        "shopify-mcp",
        "--clientId", "YOUR_CLIENT_ID",
        "--clientSecret", "YOUR_CLIENT_SECRET",
        "--domain", "YOUR_STORE.myshopify.com"
      ]
    }
  }
}
```

Get credentials by creating a custom app in your Shopify admin with Admin API access.

## Enabling live docs for shopify-dev (Context7)

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

## Usage examples

```
Add a sticky add-to-cart button to my Dawn theme
Create a Shopify app that syncs products to an external CRM
Write a bulk GraphQL query to update all product metafields
Audit my Shopify store - find what's hurting conversion
Which apps should I remove to speed up the store?
Fix the SEO issues on my product pages
```

## Part of VeyraSkills

This pack is part of the [veyraskills](https://github.com/veyralabsgroup/veyraskills) collection.

Also available:
- [@veyralabs/shopify-dev](https://github.com/veyralabsgroup/shopify-dev) - developer skill standalone
- [@veyralabs/shopify-store](https://github.com/veyralabsgroup/shopify-store) - store auditor standalone
- [@veyralabs/naming-suite](https://github.com/veyralabsgroup/naming-suite) - startup naming and brand analysis
- [@veyralabs/webcloner](https://github.com/veyralabsgroup/webcloner) - pixel-accurate website cloning
