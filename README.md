# BooksBot 📚

A Scrapy web scraper that extracts book information from [Books to Scrape](http://books.toscrape.com/), a demo website designed for testing web scraping.

## What it does

This bot crawls through all pages of books.toscrape.com and extracts detailed information about each book, including:

- **Title** - The book's title
- **Category** - Book genre/category (e.g., Fiction, History, Romance)  
- **Description** - Book summary/description
- **Price** - Listed price in the website's currency

The spider automatically follows pagination links to scrape all available books across multiple pages.

## Installation

1. Clone this repository:
```bash
git clone https://github.com/wrobb/booksbot.git
cd booksbot
```

2. Install Scrapy:
```bash
pip install scrapy
```

## Usage

### Run the spider
```bash
scrapy crawl books
```

### Save data to JSON file
```bash
scrapy crawl books -o books.json
```

### Save data to CSV file
```bash
scrapy crawl books -o books.csv
```

## Project Structure

```
booksbot/
├── books/                  # Main Scrapy project directory
│   ├── spiders/           # Spider definitions
│   │   ├── __init__.py
│   │   └── books.py       # Main books spider
│   ├── __init__.py
│   ├── items.py           # Item definitions (currently unused)
│   ├── pipelines.py       # Data processing pipelines
│   └── settings.py        # Scrapy settings
├── scrapy.cfg             # Scrapy configuration
└── README.md
```

## How it works

The `BooksSpider` class:

1. **Starts** at the homepage: `http://books.toscrape.com/`
2. **Extracts** all book links from product listings
3. **Follows** each book link to get detailed information
4. **Navigates** to next pages using pagination links
5. **Yields** structured data for each book found

## Output Format

Each scraped book returns a dictionary with the following structure:

```json
{
  "title": "A Light in the Attic",
  "category": "Poetry",
  "description": "It's hard to imagine a world without A Light in the Attic...",
  "price": "£51.77"
}
```

## Features

- ✅ **Respectful scraping** - Obeys robots.txt
- ✅ **HTTP caching** - Enabled for faster development
- ✅ **Pagination handling** - Automatically follows "next" page links
- ✅ **Structured data extraction** - Clean, consistent output format
- ✅ **Multiple output formats** - Supports JSON, CSV, and other Scrapy formats

## Contributing

This is a simple educational web scraping project. Feel free to fork and modify for your learning purposes.

## Legal Note

This scraper targets books.toscrape.com, which is specifically designed as a sandbox site for practicing web scraping. Always respect robots.txt and website terms of service when scraping other sites.