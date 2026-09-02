# GitHub Pages Deployment Setup

This guide walks through configuring `market-loft.com` to point to this GitHub Pages repository.

## DNS Configuration (Porkbun)

### For the root domain (market-loft.com)

Delete the existing ALIAS record pointing to `uixie.porkbun.com` and add **4 A records** pointing to GitHub's IP addresses:

| Type | Host | Value |
|------|------|-------|
| A | *(blank)* | 185.199.108.153 |
| A | *(blank)* | 185.199.109.153 |
| A | *(blank)* | 185.199.110.153 |
| A | *(blank)* | 185.199.111.153 |

### For www (www.market-loft.com)

Replace the wildcard CNAME `*.market-loft.com → uixie.porkbun.com` with a specific www CNAME:

| Type | Host | Value |
|------|------|-------|
| CNAME | www | `sarahsonrisa.github.io` |

## GitHub Pages Configuration

1. Go to your repository settings → **Pages**
2. Under "Custom domain", enter `market-loft.com`
3. GitHub will automatically create a `CNAME` file in your repository

## After DNS Propagates

Once DNS changes propagate (usually 5-30 minutes):

1. Enable **Enforce HTTPS** in GitHub Pages settings
2. Remove the wildcard CNAME `*.market-loft.com` from Porkbun
   - Keep only the root domain A records and www CNAME

## Verification

- Visit `https://market-loft.com` — should load the GitHub Pages site
- Visit `https://www.market-loft.com` — should also work and redirect appropriately

## Reference

- [GitHub Pages custom domain documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [GitHub Pages IP addresses](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
