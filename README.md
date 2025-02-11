# aie5_hw7

Question #1 - What are the three types of query synthesizers doing? Describe each one in simple terms.

In the context of Ragas, we are using query synthesizers to generate different kinds of user prompt queries based on the scenario and the persona. The aim to bridge the gap between how a user asks a question and how the retrieval system finds the best supporting documents. Ragas uses a few pre-created query synthesizers.

* SingeHopSpecificQuerySynthesizer: As the name suggests this produces questions that are very straighforward and direct where the LLM is able to give the answer in a single shot. There are no ambiguous terms or irrelevant words and its easier for the LLM to understand the question and it can be answered by a single document source or chunk in vector.

* MultiHopAbstractQuerySynthesizer: This kind of synthesizer generates more abstract queries that requires information to be fetched from multiple sources. The abstract part suggests that it can either be summarizing or generalizing
  
* MultiHopSpecificQuerySynthesizer: This also focusses on abstract queries that requires information to be fetched as a result of multi-hops fetching information from different sources but this focusses on specific aspects or sub-questions related to the overall question. This synthesizer is good at breaking the complex topic into smaller more manegeable questions that are multi-hop

Question #2 - Highlight what each evaluator is evaluating:

* qa_evaluator: This is using the function provided by LangSmith for QA(question-answer) evalauation. The objective is to evaluate the quality of the answer generated the QA system, given a set of questions and comparing the answers to the referencible answers also known as ground truth answers. The comparison is done by the eval_llm which can use various techniques like direct comparison or LLM based assessment. Its a valuable tool to evaluating and improving the performance of the QA tool.
  
* labeled_helpfulness_evaluator: The labeled_helpfulness_evaluator is custom defined evaluator and is designed to evaluate the helpfulness of a submission (response from a LLM) by comparing it to a reference answer and considering the original input (question). It does this by prompting the eval_llm with the helpfulness description and providing it with the prediction, reference, and input. This is a way to quantitatively measuring the helpfulness of your model's responses.
  
* dope_or_nope_evaluator: The dope_or_nope_evaluator is also a custom defined evaluator and it just emulates to show how subjective or informal the custom evaluation criteria can be. This one gives the assessment of dope, lit or cool based on the input question. Other real world subjective evaluations or creativity judgement or originality or impact of a piece of writing.

Question #3 - Why would modifying our chunk size modify the performance of our application?

Modifying the chunk size in a retrieval-augmented generation (RAG) application can significantly impact performance, both in terms of retrieval quality and computational efficiency. The following are the reasons for that:
* Computational Efficiency and Chunk Size : Chunk size impacts computational efficiency. Smaller chunks lead to increased retrieval overhead and more LLM calls. Larger chunks result in wasted computation and memory issues.
* Finding the Optimal Chunk Size: The best chunk size depends on data nature, query complexity, LLM context window, and embedding model.

Hence modifying chunk size requires finding a balance that provides enough context without sacrificing focus or exceeding computational limits. Experimentation is key to finding the optimal chunk size.

