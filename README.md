# Financial News Sentiment Classifier

Classifies financial news headlines as **bearish**, **neutral** or **bullish**. Built as a first step toward market-prediction models: sentiment from news can later be tested as a signal for price moves.

## Data
Public [Twitter Financial News Sentiment](https://huggingface.co/datasets/zeroshot/twitter-financial-news-sentiment) dataset: 9,543 training and 2,388 test headlines.

## Method
- TF-IDF features (word unigrams and bigrams)
- Logistic regression with class weighting (neutral headlines dominate the data)
- Regularization strength chosen on a validation split; the test set was used once, at the end

## Results (held-out test set, 2,388 headlines)

| Metric | Value |
|---|---|
| Accuracy | 83.0% |
| Macro-F1 | 0.774 |
| Majority-class baseline accuracy | 65.6% |

| Class | Precision | Recall | F1 |
|---|---|---|---|
| Bearish | 0.679 | 0.706 | 0.692 |
| Bullish | 0.735 | 0.743 | 0.739 |
| Neutral | 0.895 | 0.884 | 0.890 |

![Confusion matrix](confusion_matrix.png)

## Limitations
- Bag-of-words features miss negation and context ("profit falls less than expected"), so bearish and bullish are weaker than neutral.
- Many bearish and bullish headlines are predicted as neutral.
- Headline sentiment is not a trading strategy; no link to price moves has been tested yet.

## Next steps
- Compare against a transformer model (e.g. FinBERT)
- Test daily sentiment against next-day stock returns using dated headlines

## Run it
Open `News_Sentiment_Colab.ipynb` in Google Colab and choose Runtime > Run all.

## Author
Rumani
