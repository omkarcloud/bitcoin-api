# Bitcoin API

REST API to get the latest Bitcoin price in USD with 24-hour market data — daily high, low, volume, and price change. One endpoint. Real-time data.

## Features

- Get current Bitcoin price in USD with a single API call
- 24-hour market data: daily high, low, volume, price change
- No parameters required — just call the endpoint
- 5,000 requests/month on free tier
- 99.99% uptime SLA
- Example Response:
```json
{
  "price_usd": "68849.12000000",
  "daily_high_usd": "72250.87000000",
  "daily_low_usd": "68452.45000000",
  "daily_volume": "14.47241000",
  "daily_price_change_usd": "-2229.41000000",
  "daily_price_change_percent": "-3.137",
  "updated_at": "2026-02-09T11:51:59+00:00"
}
```

## Get API Key

Create an account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up?redirect=/api-key) to get your API key, and use it in requests. 5000 requests are free every month.

## Quick Start

```bash
curl -X GET "https://bitcoin-api.omkar.cloud/bitcoin-price" \
  -H "API-Key: YOUR_API_KEY"
```

```json
{
  "price_usd": "68849.12000000",
  "daily_high_usd": "72250.87000000",
  "daily_low_usd": "68452.45000000",
  "daily_volume": "14.47241000",
  "daily_price_change_usd": "-2229.41000000",
  "daily_price_change_percent": "-3.137",
  "updated_at": "2026-02-09T11:51:59+00:00"
}
```

## Installation

### Python

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://bitcoin-api.omkar.cloud/bitcoin-price",
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()
print(f"Bitcoin Price: ${data['price_usd']}")
```

### Node.js

```bash
npm install axios
```

```javascript
import axios from "axios";

const response = await axios.get("https://bitcoin-api.omkar.cloud/bitcoin-price", {
    headers: { "API-Key": "YOUR_API_KEY" }
});

console.log(`Bitcoin Price: $${response.data.price_usd}`);
```

## API Reference

### Endpoint

```
GET https://bitcoin-api.omkar.cloud/bitcoin-price
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `API-Key` | Yes | API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key) |

### Parameters

None. Just call the endpoint with your API key.

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `price_usd` | string | Current Bitcoin price in USD |
| `daily_high_usd` | string | Highest price in the last 24 hours |
| `daily_low_usd` | string | Lowest price in the last 24 hours |
| `daily_volume` | string | 24-hour trading volume |
| `daily_price_change_usd` | string | Price change in USD over the last 24 hours |
| `daily_price_change_percent` | string | Price change as a percentage over the last 24 hours |
| `updated_at` | string | When the data was last updated (ISO 8601) |

## Examples

### Get Bitcoin price for a trading bot

```python
import requests

response = requests.get(
    "https://bitcoin-api.omkar.cloud/bitcoin-price",
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()
price = float(data["price_usd"])

if price < 70000:
    print(f"Buy signal: Bitcoin is at ${price:,.2f}")
else:
    print(f"Hold: Bitcoin is at ${price:,.2f}")
```

### Track 24-hour price movement

```python
import requests

response = requests.get(
    "https://bitcoin-api.omkar.cloud/bitcoin-price",
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()
change = float(data["daily_price_change_percent"])
print(f"24h Change: {change}% | High: ${data['daily_high_usd']} | Low: ${data['daily_low_usd']}")
```

## Error Handling

```python
response = requests.get(
    "https://bitcoin-api.omkar.cloud/bitcoin-price",
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 5,000 |
| Starter | $25 | 100,000 |
| Grow | $75 | 1,000,000 |
| Scale | $150 | 10,000,000 |

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Bitcoin API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Bitcoin%20API.)

[![Contact Us on Email about Bitcoin API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Bitcoin%20API%20Question)
