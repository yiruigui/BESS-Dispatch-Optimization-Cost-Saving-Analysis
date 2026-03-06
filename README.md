# California Utility-Scale Battery Storage: Cost Savings & Price Suppression Analysis

This project explores the economic and grid-stability impact of large-scale battery energy storage systems (BESS) within the California ISO (CAISO) electricity market. By simulating the "Merit Order" (supply stack), this analysis quantifies how shifting midday solar energy to evening peak hours can reduce system-wide procurement costs through the **Price Suppression Effect**.



## 📊 Research Question
**How much money can California utilities save by using large batteries to shift electricity from cheap midday hours to expensive evening peaks?**

### Hypothesis
By charging during midday solar peaks (acting as new demand) and discharging during evening spikes (acting as negative demand), utilities can displace expensive natural gas "peaker" plants, lowering the clearing price for all consumers.

## 🛠 Methodology
The project utilizes a custom **Energy & Battery Dispatch Simulation Engine** that mimics real-time CAISO market clearing:

1.  **Data Reconstruction**: Merges CAISO OASIS "System Load" and "Public Bid" datasets to reconstruct the hourly Supply Stack (Merit Order).
2.  **MW Adjustment**:
    * **Charging (09:00–15:00)**: Adds load during cheap solar hours.
    * **Discharging (17:00–21:00)**: Subtracts load during evening peaks.
3.  **Price Re-Discovery**: Unlike fixed-price arbitrage models, this simulation accounts for **Price Elasticity**. It finds a new "Marginal Clearing Price" based on the adjusted Net Load within the reconstructed supply stack.

### Battery Parameters
* **Capacity**: 1,000 MWh
* **Power Rating**: 250 MW (4-hour duration)
* **Efficiency**: 90% Round-trip

## 🚀 Key Insights
* **Grid Relief**: On the target date (Nov 30, 2025), the grid required ~7,400 MW of new generation in just 5 hours (HE 13 to HE 18). Shaving this peak directly improves grid reliability.
* **The "Secondary Peak" Risk**: Uncoordinated charging (all batteries hitting the same hour) can create new peaks that accidentally raise costs.
* **The Optimal Strategy**: **Staggered Coordination** emerged as the most resilient strategy. While "Greedy" bidding maximizes private profit, it leads to diminishing returns once the fleet exceeds 1,000 MW.



## 🧰 Tech Stack
* **Language**: Python 3
* **Libraries**: `pandas`, `numpy`, `matplotlib`
* **Data Source**: [CAISO OASIS](https://oasis.caiso.com/mrioasis/logon.do)

## 📖 Citations
1.  **CAISO OASIS**: Nov 30, 2025 Market Data.
2.  **CPUC (2023)**: Integrated Resource Plan (IRP) and Long-Term Procurement Plan.
3.  **CEC (2024)**: Load Flexibility goals for 2030.

---
*Developed as a Final Project for Python for Data Analysis.*
