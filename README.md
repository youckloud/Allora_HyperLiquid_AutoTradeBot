# 🚀 AlloraNetwork, HyperLiquid & DeepSeek AI Auto Trade Bot

Welcome to the **AlloraNetwork HyperLiquid Auto Trading Bot**!
By default, the bot uses a **volatility-based strategy**, but you can define your own custom strategy to suit your trading preferences.

---



---

## ⚙️ Configuration Details

- **PRICE_GAP**: Percentage difference between Allora's prediction and the current price required to trigger a trade.
- **ALLOWED_AMOUNT_PER_TRADE**: 💵 Maximum amount (in USD) for each trade, excluding leverage.
- **MAX_LEVERAGE**: Maximum leverage multiplier (e.g., `1` for 1x leverage).
- **CHECK_FOR_TRADES**: Time interval (in seconds) for the bot to check for trading opportunities.
- **VOLATILITY_THRESHOLD**: Minimum volatility level required before a trade executes.
- **BTC_TOPIC_ID** and **ETH_TOPIC_ID**: Mapping of tradable tokens to their Allora prediction topic IDs.

---

## 🧠 Default Volatility Strategy

By default, the bot employs a **volatility-based strategy** to analyze market conditions and Allora's predictions to execute trades. The strategy is implemented in the `volatility_strategy` module.

---

## 🛠️ Custom Strategy

Modify `custom_strategy.py` to create a personalized trading strategy.

### Example Custom Strategy
```python
def custom_strategy(token, price=None, allora_signal=None, allora_prediction=None):
    """
    Custom strategy that trades against Allora’s predictions in high-volatility conditions.
    """
    if price is None or allora_signal is None or allora_prediction is None:
        return None
    
    return volatility_strategy.execute(token, price, allora_signal, allora_prediction)
```
### How to Use
1. Open `strategy/custom_strategy.py`.
2. Modify `custom_strategy` to implement your own logic.

---

## 🤖 DeepSeek AI Trade Reviewer

The bot integrates **DeepSeek AI** for trade validation. It assesses trade risk, confidence, and reasoning before execution.

### How It Works

1. **Trade Analysis**:
   - Current price vs. Allora prediction
   - Market volatility
   - Trade direction (BUY/SELL)
   - Historical performance

2. **Decision Metrics**:
   - `approval` (true/false): Trade approval status
   - `confidence` (0-100): Confidence level in the trade
   - `reasoning`: Explanation of the trade decision
   - `risk_score` (1-10): Trade risk assessment

3. **Trade Execution Criteria**:
   - Confidence score ≥ 70%
   - DeepSeek AI approval ✅
   - Risk score logged for tracking

### Example Output
```
Trade Review by DeepSeek AI:
  Confidence: 85%
  Reasoning: "Allora prediction aligns with market trends.
              Volatility stable. Historical success rate: 70%."
  Risk Score: 3/10
```

---

## 🔄 Example Workflow

1. **Allora Prediction**: "BUY" signal detected for BTC.
2. **Custom Strategy**: Evaluates trade feasibility.
3. **DeepSeek AI Review**: Validates trade based on risk, confidence, and reasoning.
4. **Bot Action**:
   - ✅ If Allora, Custom Strategy, and DeepSeek AI agree → Trade executed.
   - ❌ If any disagree → Trade rejected.

---

## 💬 Support

For questions, reach out via GitHub. If this project helps you, consider giving it a ⭐!

---

## 🤝 Contribute

This project is open source! Feel free to fork the repo, improve the bot, and submit a pull request. 🌟

---

Happy Trading! 🚀📈

