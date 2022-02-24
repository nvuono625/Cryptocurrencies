# Overview

Decentralized Finance (DeFi) is steadily developing it's value into a new asset class. In the new age of cryptocurrencies it has almost become a race to develop a coin with great security or anonymity while maintaining that high trasaction per second (TPS) speed. This new industry also provides for new investors to receive that  "get rich quick" possibility. Due to this opportunity, it is time to use unsupervised machine learning, analyzing [crypto_data.csv](https://github.com/nvuono625/Cryptocurrencies/blob/main/Resources/crypto_data.csv) and build a classification system for this new investment. The goal is to process data, cluster, reduce dimensions and reduce principal components using PCA to build visualizations that rank each cryptocurrency into a specific class.

_____

# Results
## Preprocessing the Data for PCA
After loading the [crypto_data.csv](https://github.com/nvuono625/Cryptocurrencies/blob/main/Resources/crypto_data.csv) dataset, the cryptocurrencies that are not being traded were dropped from the dataset. In doing so it allows us to remove the "IsTrading" column because we know that the dataset now only contains tradable cryptocurrencies. Next, NaN's in the TotalCoinsMined column were dropped and the respective coins were excluded as well.

![/Resources/crypto_df.png](/Resources/crypto_df.png)

______

## Reducing Data Dimensions Using PCA
After using get_dummies to create variables for text features and StandardScaler to standardize the data. PCA was used to reduce data dimensions to three principal components, PC 1, PC 2, and PC 3.

![/Resources/principal_component.png](/Resources/principal_component.png)

______

## Clustering Cryptocurrencies Using K-Means
To determine the best value for K to run K-Means, an Elbow Curve is created.

![/Resources/kmeans_elbow_curve.png](/Resources/kmeans_elbow_curve.png)
- Because of the hard curve around four, K will equal four, K = 4.

After intializing the K-Means Model to predict clusters and fit a model in the Class column, the crypto_df and pcs_df were concatentated and the Class column along with the CoinName column were added.

![/Resources/clustered_df.png](/Resources/clustered_df.png)
______

## Visualizing Cryptocurrency Results
Now that the data was processed, clustered, dimensions reduced and principal components reduced it was time to develop our visualizations.
A 3D-Scatter with the PCA data and the clusters was created:

![/Resources/scatter_3d.png](/Resources/scatter_3d.png)


Next, a hvplot was used to create or final table of tradeable cryptocurrencies:

![/Resources/hvplot_table.png](/Resources/hvplot_table.png)


Finally, A new dataframe was scaled to develop a hvplot scatter using TotalCoinsMined as the X and TotalCoinSupply as the Y:

![/Resources/hvplot_scatter.png](/Resources/hvplot_scatter.png)
