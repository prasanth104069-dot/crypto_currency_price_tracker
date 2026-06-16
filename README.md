# Cryptocurrency Price Tracker

A Python-based web scraper that collects **real-time cryptocurrency prices** from [CoinMarketCap](https://coinmarketcap.com/) using Selenium. It extracts the top 10 coins with key market data and saves them to a timestamped CSV file for trend analysis.

---

## Features

- **Live Price Scraping** — Fetches real-time prices and market data automatically
- **Dynamic Page Handling** — Uses Selenium WebDriver to handle JavaScript-rendered pages
- **Top 10 Coins** — Extracts Rank, Name, Symbol, Price (USD), 24h Change %, and Market Cap
- **CSV Export** — Saves extracted data into a structured `.csv` file
- **Historical Logging** — Appends timestamped data on each run for trend tracking
- **Headless Browser Mode** — Run silently in the background (no browser window)
- **Price & Change Filtering** — Filter coins by price range or 24h % change

---

## Technologies Used

| Tool | Purpose |
|------|---------|
| Python | Core programming language |
| Selenium | Browser automation and dynamic scraping |
| selenium-stealth | Bypass bot detection on CoinMarketCap |
| pandas | Data manipulation and CSV export |
| webdriver-manager | Auto-manages ChromeDriver setup |
| Google Chrome | Browser controlled via ChromeDriver |

---

## Project Structure

```
cryptocurrency price tracker/
│
├── crypto_tracker.py      # Main scraper script
├── requirements.txt       # Python dependencies
├── crypto_prices.csv      # Output file (auto-generated on first run)
└── README.md              # Project documentation
```

---

## Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/your-username/cryptocurrency-price-tracker.git
cd cryptocurrency-price-tracker
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Make sure Google Chrome is installed
Download from: https://www.google.com/chrome/

---

## How to Run

```bash
python crypto_tracker.py
```

On the first run, ChromeDriver is automatically downloaded by `webdriver-manager`.

---

##  Configuration

Edit these variables at the top of `crypto_tracker.py`:

```python
HEADLESS = False        # True = background mode | False = visible browser
TOP_N = 10              # Number of top coins to scrape

# Optional filters (set to None to disable)
MIN_PRICE = None        # e.g. 100.0
MAX_PRICE = None        # e.g. 50000.0
MIN_CHANGE_24H = None   # e.g. 2.0 (only coins up more than 2%)
MAX_CHANGE_24H = None   # e.g. -1.0 (only coins down more than 1%)
```

---

## Sample Output

### Console
```
=======================================================================
Rank   Name               Symbol   Price (USD)    24h %   Market Cap
=======================================================================
1      Bitcoin            BTC       $69,420.1200   +2.35%  $1.36T
2      Ethereum           ETH        $3,512.8800   +1.87%  $422.1B
3      Tether             USDT           $1.0001   +0.01%  $109.8B
...
=======================================================================
Scraped at: 2026-06-15 10:30:00
```

### CSV (`crypto_prices.csv`)
```
Timestamp,Rank,Name,Symbol,Price (USD),24h Change (%),Market Cap
2026-06-15 10:30:00,1,Bitcoin,BTC,69420.12,2.35,$1.36T
2026-06-15 10:30:00,2,Ethereum,ETH,3512.88,1.87,$422.1B
```

Each run **appends** a new set of rows with the current timestamp — enabling historical trend tracking.

---

##  Notes

- CoinMarketCap uses JavaScript rendering; Selenium is required (requests/BeautifulSoup won't work)
- `selenium-stealth` is used to avoid bot detection
- If scraping fails, try increasing the `time.sleep()` delay in the script
- Run the script repeatedly (e.g., every hour) to build a historical dataset

---

## Author

**Prasanth**  
Student, SKP Engineering College  
Mini Project — Cryptocurrency Price Tracker
