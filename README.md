## Stock Movement Prediction using Reddit Data

The sources provide a detailed walkthrough of a project that uses Reddit data to predict stock movements. Here is a summary of the key steps and insights:

**1. Data Collection:**

* The project focuses on collecting data from three subreddits: 'wallstreetbets', 'stocks', and 'investing', which are known for their active discussions on stocks and investments.
* Using the `asyncpraw` library, an asynchronous function is defined to efficiently collect data from these subreddits. This allows the program to simultaneously fetch data from multiple sources without waiting for each request to complete.
* For each post, the function gathers information such as the subreddit name, post title, score, URL, number of comments, and creation timestamp. 

**2. Data Cleaning:**

* Before analysis, the collected data needs to be cleaned. This involves:
    * **Handling missing values:** Rows with missing data are removed to avoid errors in analysis.
    * **Removing emojis and special characters:** These can interfere with sentiment analysis and are therefore removed using regular expressions. 
    * **Removing duplicate entries:** This ensures that each post is only analysed once.
    * **Converting timestamps to datetime format:** This allows for easier manipulation and analysis of time-related trends. 

**3. Sentiment Analysis:**

* Sentiment analysis is performed using the `vaderSentiment` library, which assigns a sentiment score to each post title.
* The compound score, ranging from -1 (most negative) to +1 (most positive), is used to represent the overall sentiment of a post.
* Sentiment scores are further categorised into positive, negative, and neutral labels using adjusted thresholds for more straightforward interpretation.
* The results of the sentiment analysis are saved to a separate CSV file for future use.

**4. Feature Extraction:**

* Besides sentiment polarity, the project extracts additional features relevant to stock movement prediction:
    * **Frequency of stock mentions:** The number of times specific stock symbols (like AAPL, TSLA, GME) are mentioned in post titles is counted using regular expressions. This serves as a measure of investor interest and potential stock volatility.
    * **Sentiment polarity by stock:** While not explicitly mentioned in the sources, the provided code can be easily adapted to calculate the average sentiment polarity for posts mentioning specific stocks. This could provide insights into how sentiment towards specific companies might influence their stock prices.

**5. Topic Modelling:**

* Latent Dirichlet Allocation (LDA), a statistical method for topic extraction, is applied to the post titles to identify the main themes being discussed.
* The `CountVectorizer` is used to convert the text data into a numerical format suitable for LDA.
* LDA identifies five distinct topics from the data, revealing conversations around market trends, specific stocks, and influential figures like Elon Musk.

**6. Correlation Analysis:**

* Historical stock price data is fetched using the `yfinance` library for the selected stock symbols.
* The stock data is merged with the Reddit data based on the date of the posts. This allows for the analysis of relationships between sentiment, mentions, and stock price changes.
* Correlations are calculated between sentiment polarity, stock mentions, and stock prices to assess potential relationships.
* The results, while not explicitly shown in the sources, can provide insights into whether positive or negative sentiment, or the frequency of mentions, is correlated with changes in stock prices.

**7. Visualisation:**

* Data visualisation is implemented using libraries like `matplotlib` and `seaborn` to better understand the trends and relationships within the data. 
* Line plots are used to visualise the average daily sentiment polarity over time, allowing for the observation of overall sentiment trends. 
* Separate line plots visualise the frequency of mentions for specific stocks over time, highlighting periods of increased investor attention. 
* Stock price changes over time are also plotted to observe price fluctuations. 
* A scatter plot is used to explore the relationship between sentiment polarity and price changes for a specific stock (AAPL in this case). 
* A heatmap visually represents the correlations between sentiment polarity and price changes for multiple stocks, offering a comprehensive overview of the relationships.

**8. Insights and Recommendations:**

* The sources highlight that stocks like GME and AMC, often categorized as "meme stocks," exhibit high sensitivity to social media sentiment. Positive sentiment on platforms like Reddit can potentially lead to short-term price increases, while negative sentiment may signal price drops. 
* Tesla (TSLA) also displays some sensitivity to sentiment, although not as pronounced as GME and AMC. It's recommended to use sentiment analysis alongside other indicators for a more comprehensive view.
* Apple (AAPL), being a more established company, shows low sensitivity to social media sentiment.  Investment decisions for such companies should be primarily based on fundamental analysis rather than sentiment trends.

**9. Future Expansions:**

* The sources propose several avenues for enhancing the project's analysis and prediction accuracy:
    * **Incorporate multiple data sources:** Integrating news articles, financial reports, analyst ratings, and economic data can provide a more holistic understanding of factors influencing stock prices.
    * **Adopt advanced sentiment analysis models:** Utilising NLP models like BERT or GPT can improve sentiment analysis accuracy by better capturing nuanced language and context.
    * **Implement real-time sentiment tracking:** This allows for timely responses to emerging trends and market events.
    * **Integrate volume and volatility metrics:** Including trading volume and stock volatility data can provide a clearer picture of how sentiment and attention translate into price movements. 
    * **Expand sector-level analysis:** Analysing sentiment across entire sectors can help identify broader trends affecting multiple stocks and industries.

**10. Conclusion:**

The project demonstrated in the sources effectively showcases the potential of using Reddit data for stock movement prediction, particularly for volatile stocks heavily influenced by social media sentiment. However, it's essential to remember that sentiment analysis should be used as one of many tools in making informed investment decisions. Further enhancements, as suggested in the sources, can improve the accuracy and scope of these predictions, leading to more robust and valuable insights. 

