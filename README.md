# Binance USDT-M Futures Order Bot (CLI)

## Overview

This project is a **CLI-based trading bot** for **Binance USDT-M Futures**, developed in Python.
It supports **core order types** and **advanced trading strategies**, with strong emphasis on
input validation, structured logging, and reproducibility.

All orders are executed on the **Binance Futures Testnet** for safety.

---

## Features Implemented

### Core Orders (Mandatory)

- ✅ Market Orders
- ✅ Limit Orders

### Advanced Orders (Bonus)

- ✅ OCO Orders (Futures-style simulation using TP + SL)
- ✅ TWAP Strategy (Time-Weighted Average Price)

### Engineering Features

- CLI-based execution
- Input validation for all parameters
- Structured logging with timestamps (`bot.log`)
- Environment variable–based API key handling
- Modular and clean project structure

---

## Project Structure

binance_bot/
│
├── src/
│   ├── market_orders.py # Market orders
│   ├── limit_orders.py # Limit orders
│   ├── advanced/
│       ├── oco.py # OCO strategy (TP + SL)
│       └── twap.py # TWAP strategy
│
├── bot.log # Execution logs
├── README.md # Documentation
└── report.pdf # Analysis 


---

## Requirements

- Python **3.10+**
- Binance account (Testnet)
- Libraries:
  - `python-binance`
  - `python-dotenv`

Install dependencies:

```bash
pip install python-binance python-dotenv

Binance API Setup (Testnet)

Create Binance Futures Testnet API keys

In the project root, create a .env file:

BINANCE_API_KEY=your_testnet_api_key
BINANCE_SECRET_KEY=your_testnet_secret_key

How to Run

All commands must be run from the project root directory.

1. Market Order
python src/market_orders.py BTCUSDT BUY 0.01

2. Limit Order
python src/limit_orders.py BTCUSDT BUY 0.01 10000

3. OCO Order (Advanced)
python src/advanced/oco.py BTCUSDT BUY 0.01 45000 39000

Places:

Take-profit (LIMIT)

Stop-loss (STOP_MARKET)

4. TWAP Strategy (Advanced)
python src/advanced/twap.py BTCUSDT BUY 0.05 5 5

Splits order into 5 parts

Executes every 5 seconds

Logging

All actions are logged in bot.log, including:

Script start

Input validation

Order placement

Errors and exceptions

Log format:
TIMESTAMP | LEVEL | MESSAGE

Notes on OCO Implementation

Binance USDT-M Futures does not support native OCO orders.
Therefore, OCO is correctly simulated by placing:

One take-profit order

One stop-loss order

This approach matches real-world futures trading systems.

Safety Disclaimer

All executions are done on Binance Futures Testnet

No real funds are used

This project is for educational purposes only
