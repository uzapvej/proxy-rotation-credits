# proxy rotation free trial: 5,000 Credits With No Credit Card, Plus the Credit Math That Decides Which Plan You Actually Need

Most "free trial" offers for rotating proxies come with a catch: a credit card field on the signup form, or a trial so small you can't tell whether the service handles your real targets. ScraperAPI's version avoids both problems. You get **5,000 API credits for 7 days with no credit card required**, and underneath that sits a permanent free plan of 1,000 credits per month that keeps running after the trial ends. That combination matters because it changes what you can test — and how much it costs you to find out.

> **Quick take:** For testing rotating proxies on ordinary websites, the trial alone answers your questions. If you're targeting Amazon, Google SERPs, or bot-protected pages, read the credit-consumption section first — those requests cost 5 to 75 credits each. Most solo developers end up on **Hobby at $49/month** ($44.10/month on annual billing). 👉 [Claim the 7-day trial — 5,000 credits, no card needed](https://www.scraperapi.com/signup?fp_ref=coupons)

## What the free trial actually includes

ScraperAPI runs two free offerings in parallel, and confusing them is the most common mistake people make at signup:

1. **Free Plan (permanent):** 1,000 API credits per month, up to 5 concurrent connections, no card, no expiration. It keeps running indefinitely.
2. **7-day trial (one-time):** 5,000 API credits during your first week, still with no payment info.

The signup flow takes about two minutes: email and password on the registration page (there is no card field), confirm your address, and your API key appears on the dashboard homepage. Requests go through a single endpoint — `api.scraperapi.com` — with your key passed as a query parameter, so nothing needs installing. Official libraries exist for Python, Node.js, Ruby, PHP and Java, but a plain curl request works.

Two dashboard details worth knowing early. You can generate additional API keys to track usage per project, which helps when you're deciding whether a specific target site deserves paid credits. And if you regenerate your key, you can only do it once per 24 hours — pick your key naming before you build anything permanent on top of one.

## The credit multiplier system most articles skip

Here's the part that determines whether the trial is useful for *your* targets. ScraperAPI bills by credits, and "one credit is the cost of a standard page request" — but standard is the floor. Some domains have custom pricing because they're harder to scrape, and it applies automatically:

| Target type | Credits per request |
| --- | --- |
| Normal websites | 1 |
| Amazon, eBay, Walmart | 5 |
| Google / Bing SERPs (including subdomains) | 25 |
| LinkedIn | 30 |
| Cloudflare / Datadome / PerimeterX sites (when bypassed) | +10 |

Feature flags add more on top. JS rendering (`render=true`) costs +10 credits, screenshots +10, premium proxies +10, ultra-premium +30. The combinations stack non-linearly: premium plus rendering is +25, and ultra-premium plus rendering is +75 per request. That last number surprises people — one heavy request with all the bells on eats 75 credits, which is 1.5% of your entire trial allowance in a single call.

What 5,000 trial credits actually buy you:

- **5,000 scrapes** of plain HTML sites (blogs, news, simple catalogs)
- **1,000 Amazon product pages**, or about 333 if you turn on JS rendering
- **200 Google search results**
- **~66 requests** with ultra-premium proxies plus rendering

Before you burn credits guessing, use the **Domain Cost Estimator** in the dashboard — it shows the exact cost of any URL in advance. You can also set a `max_cost` parameter to cap what any single request consumes, which is cheap insurance against accidentally requesting an ultra-premium render on a protected site.

One billing detail cuts in your favor: true failed requests don't cost credits. If a request returns anything other than a 200 or 404, you get the credits back.

## Full plan comparison

Every paid plan carries the same core feature set: JS rendering, premium proxies, rotating proxy pools, JSON auto-parsing, custom headers and sessions, CAPTCHA and anti-bot bypass, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. Where they differ is volume, concurrency, geotargeting, and billing flexibility. Annual billing takes **10% off every tier** automatically, no code needed. 👉 [See all current plans and prices](https://www.scraperapi.com/pricing?fp_ref=coupons)

| Plan | Monthly | Annual (per mo) | Credits/mo | Threads | Buy |
| --- | --- | --- | --- | --- | --- |
| Free | $0 | $0 | 1,000 | 5 | [ Get free access](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Free Trial (7 days) | $0 | $0 | 5,000 one-time | 5 | [ Start trial](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Hobby | $49 | $44.10 | 100,000 | 20 | [ Try Hobby](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [ Try Startup](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [ Try Business](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [ Try Scaling](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [ Try Professional](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [ Try Advanced](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22M+ | 500+ | [ Contact sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

A second set of differences doesn't fit in one table, and some of them change the decision entirely:

- **Geotargeting:** Hobby and Startup are limited to **US & EU** locations. Country-level targeting worldwide (50+ countries) starts at Business.
- **Analytics history:** Hobby and Startup keep usage stats for 30 days only; Business and up get unlimited history.
- **Pay-as-you-go overflow:** only on Scaling and above. On the three lower paid tiers, hitting 100% of credits means scraping pauses until renewal.

## Limits that only show up in the fine print

These are the details that tend to appear in docs and FAQ pages rather than on the pricing banner, and several of them directly affect your first invoice:

- **404 responses still cost credits.** Both 200 and 404 are billed as successful requests; only other failures are refunded.
- **Cancelled requests get charged** if you cancel before the 70-second processing window completes.
- **A forced 10-minute cache applies on difficult targets.** If you're pulling time-sensitive data like live prices, results can be up to 10 minutes old.
- **No proactive usage alerts.** Nothing emails or texts you when credits run low — you have to watch the dashboard yourself. Set a calendar reminder for your first month until you know your burn rate.
- **Credits don't roll over.** Whatever's unused at renewal disappears.
- **DataPipeline has its own, higher credit schedule.** A request costing 1 credit through the standard API costs 6 credits inside the no-code DataPipeline product. Read those docs before scheduling jobs there.
- **Login-required sites are off-limits by the terms of service.** Session persistence exists, but scraping behind auth walls is explicitly forbidden.

On concurrency, the behavior is actually friendly: exceed your thread limit and you get a 429 response asking you to retry within your plan's limit. There's no overage fee — the request is turned away rather than queued and billed.

## What plans cost in practice, not on the sticker

The listed price and the real cost can diverge fast depending on what you scrape. Hobby's 100,000 credits sounds ample until you translate it: roughly **20,000 Amazon product pages or 4,000 Google queries per month**. For price monitoring or SERP tracking, that budget evaporates quickly. Startup's 1,000,000 credits cover about 200,000 Amazon pages or 40,000 Google queries monthly, which is why it's the natural fit for small teams running production workloads rather than experiments.

The annual discount is modest but real: $58.80/year on Hobby, $178.80/year on Startup. If you're committing anyway, it's free money.

Running out mid-cycle has two official remedies, and they behave differently. **Auto-upgrade** (Hobby through Professional, opt-in) bumps your account to the next tier automatically when credits run out, usually at a better per-credit rate. **Pay-as-you-go** (Scaling and up) keeps scraping at a fixed per-credit rate up to a monthly cap you set, without changing plans. If you're on Hobby with unpredictable volume, turn auto-upgrade on — otherwise your scraper just stops until the next billing date.

For context on how this sits in the market: Bright Data, the enterprise standard, starts around $499/month — out of reach for small teams. ScrapingBee enters at a similar ~$49 tier. ScraperAPI's positioning is in the middle: more accessible than the enterprise options, with a documented per-credit model and a free tier that most competitors don't match.

## How the trial compares to other rotating proxy offers

Since most people searching for a proxy rotation free trial are comparing options, here's what the alternatives' trial terms look like (information only — check their sites for current details):

- **IPIPGO:** 3-day free trial, no card binding, full functionality during the trial window.
- **pxyedge:** 7-day trial with 1GB traffic and 10 rotating IPs, no credit card, activated with a business email.
- **ipfoxy:** trial credits on signup; rotating residential plans run around $5.27 for 1GB over 30 days across 200+ countries.
- **RoProxy:** 10 free sessions, available for 7 days after verification.

The structural difference is worth naming. Most competitors hand you a time-boxed or volume-boxed sample of the proxy pool itself. ScraperAPI gives you credits against a full scraping API — rotation, CAPTCHA handling, JS rendering and retries all included — so what you validate is the end-to-end result on your actual targets. If your priority is raw bandwidth per dollar for a self-managed pool, ipfoxy's per-GB pricing will likely come out cheaper. If your priority is "my script returns clean data without me babysitting proxies," the API model fits better, and the trial is long enough to prove it.

A couple of independent test numbers floating around recent evaluations: Zillow at 100% success, Amazon at 98%, Etsy at 99%, Walmart at 93%. Treat those as directional, since results depend heavily on which pages and settings you use — which is exactly what the trial is for.

## Who should stay on the free plan

Some honest guidance, because upgrading for its own sake is a real way to waste money:

- **Occasional or one-off scraping:** the permanent Free Plan (1,000 credits/month) may be all you ever need. A personal price-monitoring script checking a handful of Amazon products daily runs about 200 credits a month — well under the cap. A weekly SERP pull on 30–40 keywords burns roughly 1,000 credits a month, right at the ceiling.
- **Budget-constrained SERP or LinkedIn monitoring:** at 25–30 credits per request, even Hobby fills up fast. Either limit query volume or plan for Startup from the start.
- **Non-technical users:** this is an API first. The dashboard and DataPipeline cover lower-code workflows on paid tiers, but if you want a point-and-click scraper with zero code, a no-code scraping tool is a more natural starting point.

The trial exists precisely for the workloads that do justify paying: JavaScript-heavy sites, anti-bot-protected pages, high-volume production scraping. Test your real targets before committing, because surcharges for protected-site bypasses only show up on actual requests.

## Before you upgrade, check these three things

1. **Your real burn rate.** Run your actual target URLs through the Domain Cost Estimator, then match against plan volumes. A plan that looks huge for HTML pages can be undersized for SERP work.
2. **Whether you need country-level geotargeting.** If yes, Hobby and Startup are out — your comparison starts at Business ($299/month).
3. **Concurrency needs.** 20 threads (Hobby) handles scheduled jobs fine; it feels cramped for time-sensitive bulk crawls.

If you only need to verify that your targets are scrapeable, the free tier costs nothing and never expires — start there. If the credit math works for your targets, Hobby at $44.10/month on annual billing is the entry point for real workloads, and you can upgrade anytime from the billing page if you outgrow it. 👉 [Start your free trial and test your first target today](https://www.scraperapi.com/signup?fp_ref=coupons)
