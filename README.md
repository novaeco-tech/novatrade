# 📈 NovaTrade

> **The Operating System for Circular Markets.**
> A decentralized exchange for secondary raw materials, environmental credits, and circular services.

[](https://www.google.com/search?q=https://github.com/novaeco-tech/novatrade/actions)
[](https://opensource.org/licenses/MIT)
[](https://www.google.com/search?q=https://trade.novaeco.tech)

**NovaTrade** is the Horizontal Enabler responsible for **Value Exchange**. While `NovaFin` handles the *settlement* (money movement), **NovaTrade** handles the *deal* (discovery, negotiation, and contracting).

It creates liquid markets for assets that were previously considered "waste." It connects the output of one sector (e.g., `NovaRecycle` plastic bales) to the input of another (e.g., `NovaMake` filament feedstock), enabling industrial symbiosis.

-----

## 🎯 Value Proposition

The circular economy fails when buyers cannot find sellers. **NovaTrade** solves the liquidity crisis:

1.  **Market Unification:** A single API to trade physical goods (Steel beams), digital assets (Carbon Credits), and service contracts (Repair labor).
2.  **Standardized Grading:** Using `NovaMaterial` data to create "Commodity Classes" for waste (e.g., "Grade A Clear PET"), making it tradable without physical inspection.
3.  **Automated Contracting:** Generating smart contracts for complex circular models like "Chemical Leasing" or "Buy-Back Guarantees."

-----

## 🏗️ Architecture (The Matching Engine)

NovaTrade acts as an **Order Book** and **Matching Engine**. It decouples the "Ask" from the "Bid."

```mermaid
graph TD
    User((Trader)) -->|HTTPS| UI[NovaTrade Terminal]
    UI -->|REST| API[NovaTrade API]
    
    subgraph "The Exchange Core"
        API -->|Post Order| Book[Order Book (Redis)]
        Book -->|Match| Engine[Matching Engine]
        Engine -->|Trade Executed| EventBus[(RabbitMQ)]
    end

    subgraph "The Intelligence Layer"
        Book -->|Price History| Mind[NovaMind]
        Mind -->|Predict Spot Price| API
    end

    subgraph "Post-Trade Execution"
        EventBus -->|Hold Funds| Fin[NovaFin]
        EventBus -->|Book Transport| Logistics[NovaLogistics]
        EventBus -->|Verify Legality| Policy[NovaPolicy]
    end
```

### Integrated Services

  * **[NovaFin](https://www.google.com/search?q=https://finance.novaeco.tech):** The cashier. Once NovaTrade matches a buyer and seller, it instructs NovaFin to execute the atomic swap (Delivery-vs-Payment).
  * **[NovaLogistics](https://www.google.com/search?q=https://logistics.novaeco.tech):** The fulfillment agent. A trade isn't complete until the material moves. NovaTrade automatically books transport based on the trade terms (Incoterms).
  * **[NovaPolicy](https://www.google.com/search?q=https://compliance.novaeco.tech):** The gatekeeper. Checks if a trade is legal *before* matching (e.g., "Cannot export HazMat waste from EU to Non-OECD countries").
  * **[NovaMind](https://www.google.com/search?q=https://mind.novaeco.tech):** The analyst. Analyzes supply/demand trends to suggest "Spot Prices" for illiquid assets like compost or scrap metal.

-----

## ✨ Key Features

### 1\. Multi-Asset Order Books

Supports three distinct asset classes in one view:

  * **Physical:** "10 Tons of Recycled Copper" (Source: `NovaRecycle`).
  * **Digital:** "50 Biodiversity Credits" (Source: `NovaNature`).
  * **Service:** "100 Hours of Repair Labor" (Source: `NovaSkills`).

### 2\. The "Symbiosis" Matcher

It doesn't just match Price; it matches Attributes.

  * **Scenario:** Brewery A lists "Hot Water Waste." Greenhouse B lists "Heat Demand."
  * **Match:** NovaTrade identifies that they are neighbors (via `NovaInfra` GPS) and suggests a direct pipe connection contract.

### 3\. Dynamic Auctions

For rare or unique items (e.g., a vintage engine block from `NovaTronix`).

  * Supports **Dutch Auctions** (Price drops until bought) to clear inventory quickly.
  * Supports **Sealed Bid** for high-value industrial tenders.

### 4\. Regulatory Guardrails

Prevents illegal waste trafficking.

  * Validates the "Waste Carrier License" of the logistics provider via `NovaPolicy`.
  * Blocks trades where the buyer does not have the "Permit to Operate" for hazardous materials.

-----

## 🚀 Getting Started

We use **DevContainers** to provide a consistent development environment.

### Prerequisites

  * Docker Desktop
  * VS Code (with Remote Containers extension)

### Installation

1.  **Clone the repo:**
    ```bash
    git clone https://github.com/novaeco-tech/novatrade.git
    cd novatrade
    ```
2.  **Open in VS Code:**
      * Run `code .`
      * Click **"Reopen in Container"** when prompted.
3.  **Start the Sector:**
    ```bash
    make dev
    ```
      * **Trading Terminal:** http://localhost:3000
      * **API:** http://localhost:8000/docs

### Configuration (`.env`)

```ini
# Exchange Settings
BASE_CURRENCY=EUR
MATCHING_ALGORITHM=FIFO # or PRO_RATA
COMMISSION_RATE=0.01

# Integrations
NOVAFIN_URL=http://novafin-api:8000
NOVALOGISTICS_URL=http://novalogistics-api:8000
NOVAPOLICY_URL=http://novapolicy-api:8000
```

-----

## 📂 Repository Structure

This is a Monorepo containing the sector's specific logic.

```text
novatrade/
├── api/                # Python/FastAPI (Domain Logic)
│   ├── src/
│   │   ├── orders/     # Order Book management (Redis)
│   │   ├── matching/   # Algorithms to pair Bids/Asks
│   │   └── contracts/  # Smart Contract generators (PDF/JSON)
├── app/                # React/Next.js Frontend (Trader UI)
│   ├── src/
│   │   ├── terminal/   # Candlestick charts & Order entry
│   │   └── wallet/     # Portfolio view
├── website/            # Documentation (Docusaurus)
└── tests/              # Integration tests
```

-----

## 🧪 Testing

We use **Market Simulation** for testing.

  * **Matching Engine:** `make test-match`
      * Injects 1,000 random Bids and Asks. Verifies that the engine correctly matches crossing prices and leaves the rest on the book.
  * **Compliance Lock:** `make test-policy`
      * Attempts to trade "Toxic Waste" across borders. Asserts that `NovaPolicy` rejects the order before it hits the book.

-----

## 🤝 Contributing

We need contributors with backgrounds in **Fintech**, **Market Microstructure**, and **Commodities Trading**.
See [CONTRIBUTING.md](https://www.google.com/search?q=../.github/CONTRIBUTING.md) for details.

**Maintainers:** `@novaeco-tech/maintainers-enabler-novatrade`