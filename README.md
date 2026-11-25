# Google Trends Scraper: Related Queries, No 429 · $2/1K

Get Google Trends data for any keyword, in any country, without fighting `429 Too Many Requests`. One result per search term, with:

**[Run it on Apify](https://apify.com/pomlabs/google-trends-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)**: no install, no login, free credit on a new Apify account.

## What you get

The usual problem with Google Trends is the `429` error: Google allows only a few dozen requests per IP, and `pytrends`, notebooks and many scrapers stop there. This Actor spreads the work over fresh residential IPs, warms each session the way a browser does, retries a failed keyword on a new IP, and gives every failed keyword a second pass at the end of the run. You only pay for what arrives.

Measured success rate: **100%: 1,580 of 1,580 keywords delivered** in 16 runs over 4 hours (87.7% on the first try, the rest after automatic retries on a new IP) (see "Reliability" below).

## Pricing

**$0.002 per keyword delivered** ($2 per 1,000), down to $1.40 per 1,000 on paid Apify plans. Keywords that Google blocks or that fail after all retries are **free**.

That is the free-plan price; Apify paid plans (Bronze, Silver, Gold) pay less per item.

## Call it by API

```bash
curl -X POST "https://api.apify.com/v2/acts/pomlabs~google-trends-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"searchTerms": ["bitcoin", "ai agents"]}'
```

Python:

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("pomlabs/google-trends-scraper").call(run_input={"searchTerms": ["bitcoin", "ai agents"]})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Use it from Claude, Cursor or any MCP client

```bash
claude mcp add google-trends "https://mcp.apify.com?tools=pomlabs/google-trends-scraper" -t http
```

## More Actors by Pom Labs

- [YouTube Transcript Scraper: Translate, No Login · $3/1K](https://apify.com/pomlabs/youtube-transcript-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [Instagram Transcript Scraper: Reels, TikTok, Facebook, Hook](https://apify.com/pomlabs/social-video-transcript?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [Reddit Scraper: Deleted & Removed, Mods, Hidden Profiles](https://apify.com/pomlabs/reddit-posts-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [LinkedIn Company Scraper (No Cookies): Posts, Similar Companies](https://apify.com/pomlabs/linkedin-company-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [YouTube Comments Scraper + Replies, Shorts · No API Key · $1/1K](https://apify.com/pomlabs/youtube-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [Instagram Profile Scraper: Exact Followers, Reels Views](https://apify.com/pomlabs/instagram-profile-data?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [LinkedIn Profile Scraper (No Cookies) + Similar Profiles](https://apify.com/pomlabs/linkedin-profile-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [Threads Scraper: Keyword Search, Posts & Profiles · No Login](https://apify.com/pomlabs/threads-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [AliExpress Scraper: Exact Units Sold, Prices, Search · $1/1K](https://apify.com/pomlabs/aliexpress-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [AI Brand Visibility Tracker - ChatGPT, Claude & Perplexity](https://apify.com/pomlabs/ai-brand-visibility?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [Mercado Livre & Amazon BR Coupon Code Checker](https://apify.com/pomlabs/mercadolivre-coupon-checker?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [Page Time Machine · Wayback Diff + AI · No Login · $2.5/1K](https://apify.com/pomlabs/page-time-machine?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [Video Downloader: TikTok No Watermark, Instagram, YouTube, X](https://apify.com/pomlabs/video-downloader?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)
- [NSFW Image Detector & Image Tagger - Moderation + Categories](https://apify.com/pomlabs/image-moderation-tagger?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper)

Full documentation, input fields and output format: [Google Trends Scraper: Related Queries, No 429 · $2/1K on Apify](https://apify.com/pomlabs/google-trends-scraper?utm_source=github&utm_medium=readme&utm_campaign=google-trends-scraper).
