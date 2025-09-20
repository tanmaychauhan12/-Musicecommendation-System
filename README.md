# -Musicecommendation-System

# Introduction
The field of music information retrieval presents a challenge due to the various ways audio can be represented, making it difficult to determine which features should be prioritised in queries. To simplify this issue, our implementation focuses specifically on the rhythm of songs as the sole query feature. While previous research has explored rhythm-based music querying, current methods suffer from inefficiency, as they necessitate querying the entire data structure to match song rhythms. To overcome this limitation, we propose the utilisation of Locality-Sensitive Hashing (LSH), a technique that efficiently identifies similar items within large datasets without requiring exhaustive searches.

# Where Our Solution Differs:
Locality-Sensitive Hashing (LSH) is a widely adopted technique for approximating nearest-neighbour searches. It efficiently identifies similar items within large datasets by mapping them to a lower-dimensional space. However, traditionally, Locality-Sensitive Hashing (LSH) employs a different method called MinHash (or the min-wise independent permutations Locality-Sensitive Hashing scheme) to estimate set similarity. MinHash is commonly used in data mining and information retrieval. While MinHash is generally effective in estimating set similarity, it has certain limitations that may hinder its effectiveness in specific applications.

To address these limitations, we have opted to implement the LSH approach using another efficient technique called Approximate Nearest Neighbors (ANN). This technique is well-suited for finding approximate nearest neighbours in large datasets. By utilising Approximate Nearest Neighbors (ANN) instead of MinHash, we aim to enhance the effectiveness and performance of the Locality-Sensitive Hashing (LSH) implementation in our project.

# Downsides of MinHash Our Approach Aims to Alleviate:
Trade-off between accuracy and computation: MinHash is an approximate technique that introduces the possibility of false positives or false negatives when estimating set similarity. The accuracy of these estimates relies on factors such as the size of the hash signatures and the number of hash functions used. However, increasing these parameters also leads to higher computational costs.
Sensitivity to the choice of hash functions: The quality of MinHash results is heavily influenced by the selection of hash functions that map set elements to the signature. Inaccurate or poor-quality hash functions can result in imprecise estimates, undermining the effectiveness of the method.
Difficulty in handling weighted sets: MinHash assumes that all elements within a set are equally important, which may not hold true in various applications where elements possess different weights or levels of importance. In such cases, the quality of MinHash results can be compromised since it does not account for these variations.
Difficulty in handling high-dimensional sets: MinHash's effectiveness diminishes when dealing with sets that have a large number of dimensions. This can lead to sparse hash signatures and reduced accuracy, a phenomenon often referred to as the "curse of dimensionality."
Why Is Our Approach Better?
Approximate Nearest Neighbors (ANN) offers a more versatile solution for Locality-Sensitive Hashing (LSH) as it can approximate nearest neighbours for various distance metrics. In contrast, MinHash is specifically designed for Jaccard's similarity. This broader applicability allows our approach to provide more accurate estimates of nearest neighbours compared to MinHash, especially when dealing with high-dimensional datasets that require similarity searches based on different distance metrics like Euclidean distance or cosine similarity.

Regarding time complexity, both the Approximate Nearest Neighbors (ANN) and MinHash approaches eventually implement a hash table with Locality-Sensitive Hashing (LSH), resulting in an O(1) time complexity for retrieval in either case. However, our focus lies more on memory efficiency, where the Approximate Nearest Neighbors (ANN) approach outperforms MinHash. This aspect is particularly crucial for our implementation since the audio dataset we utilised is quite large, weighing in at 3.3 GiB.

Therefore, by utilising Approximate Nearest Neighbors (ANN) instead of MinHash, we achieve improved accuracy in estimating nearest neighbours while maintaining efficient retrieval time and better memory efficiency, ensuring optimal performance for our implementation with the sizable audio dataset.

# Usage:
Music Recommendation Based on Rhythmic Similarity Using Locality-Sensitive Hashing (LSH).ipynb — Contains the implementation of our Locality-Sensitive Hashing (LSH) implementation to train and evaluate a music recommendation system on the audio dataset.
app.py — Source code for the web application (Flask) that accompanies the music recommendation system.
templates — Contains the source codes for the web pages, namely index.html and predict.html, which are rendered by the web application (Flask).
static — Contains all the icons and visual elements utilised by the web application (Flask).
static\files — Directory where the audio files uploaded by users on the web application (Flask) are stored.
features.pkl — Object file that contains the Mel-Frequency Cepstral Coefficients (MFCC) features of all the audio files utilised for training.
music.ann — Memory-mapped (mmap) file that contains the AnnoyIndex object for the music recommendation system utilising Approximate Nearest Neighbors (ANN).
# Instructions (Execution):
Execute the app.py file and access the given link to the host port.
Upload any audio file into the system.
Once you reach the /predict page, you will receive both the best and worst recommendations for the uploaded audio file.
Additionally, a file named pied_piper_download.csv will be saved in the current directory, which will include similar audio segments identified from the uploaded audio file.
