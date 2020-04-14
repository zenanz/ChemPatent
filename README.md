# ChemPatentEmbeddings

This repository contains an ELMo and a word2vec model pre-trained on a 1 Billion word chemical patent corpus.

## Dataset

The dataset we used for training consists of 84,076 patent documents from 7 different patent authorities. The dataset will **NOT** be made publicly available.

|PO|# of Document|# of Sentences|# of Tokens|
|--|-------------|--------------|-----------|
|AU|7,743        |4,662,375     |156,137,670|
|CA|1,962        |463,123       |16,109,776 |
|EP|19,274       |3,478,258     |117,992,191|
|GB|918          |182,627       |6,038,837  |
|IN|1,913        |261,260       |9,015,238  |
|US|41,131       |19,800,123    |628,256,609|
|WO|11,135       |4,830,708     |159,286,325|
|Total|84,076    |33,687,474    |1,092,836,646|

## Word2Vec

We trained the word2vec model with same hyper-parameters in [Pyysalo et al., (2013)](http://bio.nlplab.org/pdf/pyysalo13literature.pdf) for 10 iterations. The word vectors file (.txt) can be directly loaded into your neural network framework. Note that words **shorter than 25 characters** in length were replaced by *long_token* during training.

Please click [here](http://chemu.eng.unimelb.edu.au:8080/patent_w2v/) to download the pre-trained word vectors.

## ELMo

Default hyper-parameters in [Peters et al., (2018)](https://arxiv.org/abs/1802.05365) were used. Note that words **shorter than 25 characters** in length were replaced by *long_token* during training (cf. max. character length is 50 under default setting).

Please click [here](http://chemu.eng.unimelb.edu.au:8080/ELMo/) to download ELMo model.

* **Fine Tuning**:  Load *weights.hdf5* and *options.json* into the original [ELMo implementation](https://github.com/allenai/bilm-tf) and train it further on your own datasets.

* **Representation**: You can also use contextualized word representations generated by ELMo for downstream tasks by load *weights.hdf5* and *options.json* into [AllenNLP](https://allenai.github.io/allennlp-docs/) framework.

## Reference

If you find the word representations useful, please cite the following paper: *Improving Chemical Named Entity Recognition in Patents with Contextualized Word Embeddings*

```
@inproceedings{zhai2019improving,
  author    = {Zhai, Zenan and Nguyen, Dat Quoc and A. Akhondi, Saber and Thorne, Camilo and Druckenbrodt,
               Christian and Cohn, Trevor and Gregory, Michelle and Verspoor, Karin},
  title     = {{Improving Chemical Named Entity Recognition in Patents with Contextualized Word Embeddings}},
  booktitle = {{Proceedings of the BioNLP 2019 workshop}},
  pages     = {To appear},
  year      = {2019},
}
```
