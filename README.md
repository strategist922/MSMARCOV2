# MSMARCO V2
MS MARCO(Microsoft Machine Reading Comprehension) is a large scale dataset focused on machine reading comprehension, question answering, and passage ranking. In MS MARCO, all question have been generated from real anonymized Bing user queries which grounds the dataset in a real world problem and can provide researchers real contrainsts their models might be used in.The context passages, from which the answers in the dataset are derived, are extracted from real web documents using the most advanced version of the Bing search engine. The answers to the queries are human generated.

First released at [NIPS 2016](https://arxiv.org/pdf/1611.09268.pdf), the current dataset has 1,010,916 unique real queries that were generated by sampling and anonymizing Bing usage logs. After sampling, we used Bing to extract the 10 most relevant passages and asked a human judge to answer the query given the information present. Not all queries had answers present in the passages but we thought this data would be useful to help systems learn that not all answers can be answers.  Around 35% of all queries in the dataset have the answer 'No answer Present' meaning judges were unable to answer the question given the information provided by the 10 relevant passages. Additionally, as of 10/26/2018 we have release a passage re-ranking reformulation of the dataset. 

For more information about the Q&A dataset please read this [Documentation](https://github.com/dfcf93/MSMARCOV2/blob/master/Q%2BA/README.md)

For more information about the Ranking dataset please read this [Documentation](https://github.com/dfcf93/MSMARCOV2/blob/master/Ranking/README.md)

## Dataset Generation, Data Format, And Statistics
What is the difference between MSMARCO and other MRC datasets? We believe the advantages that are special to MSMARCO are:
- Real questions: All questions have been sample from real anonymized bing queries.
- Real Documents: Most Url's that we have source the passages from contain the full web documents. These can be used as extra contextual information to improve systems or be used to compete in our expert task.
- Human Generated Answers: All questions have an answer written by a human. If there was no answer in the passages the judge read they have written 'No Answer Present.'
- Human Generated Well-Formed: Some questions contain extra human evaluation to create well formed answers that could be used by intelligent agents like Cortana, Siri, Google Assistant, and Alexa.
- Dataset Size: At over 1 million queries the dataset is large enough to train the most complex systems and also sample the data for specific applications.
## Download the Dataset
To Download the MSMARCO Dataset please navigate to [msmarco.org](http://www.msmarco.org/dataset.aspx) and agree to our Terms and Conditions.

### Tasks
In an effort to produce a dataset that can continue to be challanging and rewarding we have broken down the MSMARCO dataset into tasks of varying difficulty.

##### Question Answering
Given a query q and a set of passages P = p1, p2, p3,... p10 a successful Machine Reading Comprehension system is expected to read and understand both the questions and passages. Then, the system must accuratley decide if the passages provide addequate information to answer the query since not all queries have an answer. If there is not enough information, the system should response 'No Answer Present.'. If there is enough information the system should create a quality answer. The target of the answer a should be as close as possible to the human generated refrence answers RA= ra1,ra2,...,ram. Evaluation will be done using ROUGE-L, BLEU-1, and a F1 score computed by measuring how well a system can know to answer questions or not. Questions that have the do not have an answer will not be used to calculate ROUGE-L or BLEU-1.

##### Natural Language Generation
Given a query q and a set of passages P = p1, p2, p3,... p10 a successful Machine Reading Comprehension system is expected to read and understand both the questions and passages. For this task all queries have an answer so systems do not need to understand No Answer Queries. Using the relevant passages a successful system should produce a candidate answer that should be as close as possible to the human generated well formed refrence answers RA= wfra1,wfra2,...,wfram. Evaluation will be done using ROUGE-L and BLEU-1.

##### Passage Reranking task Task
Given a query q and a the 1000 most relevant passages P = p1, p2, p3,... p1000, as retrieved by BM25 a succeful system is expected to rerank the most relevant passage as high as possible. For this task not all 1000 relevant items have a human labeled relevant passage. Evaluation will be done using [MRR](https://en.wikipedia.org/wiki/Mean_reciprocal_rank)

### Feedback
MS MARCO has been designed not as a dataset to be beat but an effort to establish a large community of researchers working on Machine Comprehension. If you have any thoughts on things we can do better, ideas for how to use datasets or general question please dont hesitate to [reach out and ask](mailto:ms-marco@microsoft.com?subject=MS MARCO Feedback).

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
