# agent 
 - classic Agent pipeline： https://github.com/modelscope/modelscope-agent/blob/master/modelscope_agent/agents/role_play.py；https://github.com/modelscope/modelscope-agent/blob/master/resources/modelscope-agent.png
 - Train process：
   + data collection：model API、common API、API- oriented QA、
   + LLM training
 - Inferecne：
   + tool retrival
   + memory control 
   + task planing
   + tool use
   + API execute
   + response generation

# meta-prompting

* https://mp.weixin.qq.com/s/y-bMFqpu7cuxpSAzbyt4cQ?poc_token=HFV1ymWjA8Y7Kk6DG0NKa0u94hX8Mi3Uwr2POir7

* https://arxiv.org/abs/2401.12954
* 从表1所示的结果中可以看到，元提示（meta-prompting）技术相较于传统的零样本（zero-shot）提示技术具有明显的优势——
元提示技术的表现分别比标准提示提高了17.1%，比专家（动态）提示（expert (dynamic) prompting）提高了17.3%，以及比多人格提示（multipersona prompting）提高了15.2%。
零样本分解、错误检测与聚合
元提示框架之所以成功，一大原因是它巧妙地利用了专业知识、内部合作以及在过程中不断自我检验的机制。
这种方法，连同采用多角色互动的方式，促进了多轮对话，让不同的角色共同参与到解决问题的过程中。
以解决MGSM数据集中的多语言算术问题为例，GPT-4在采用元提示方法时，通常会经历三个阶段：
首先将问题从源语言（比如，孟加拉语）翻译成英语，接着应用计算专长（例如，请求数学专家的帮助）来寻找解决方案，最后进行独立或验证确认。
其中，元提示能够在不被明确指令的情况下完成这样的翻译。
* 大语言模型倾向于重复自己的错误，并且还非常自信。
相比于多角色提示，元提示会在过程中让专家或不同角色重新审视问题，从而为发现新的见解和先前未被注意到的错误提供了可能。
想象一下，如果任务是解决24点游戏，即用6、11、12和13这四个数字，每个各用一次，组成一个算术表达式，使其结果为24：
1. 元模型（Meta Model）建议咨询数学、问题解决和Python编程的专家。强调需要准确无误地遵循规则，并在必要时让其他专家进行复审。
2. 在一位专家给出方案后，另一位专家指出了其中的错误。于是，元模型建议编写一个Python程序来搜索可行的方案。
3. 接着，元模型邀请了一位编程专家负责编写这个程序。
4. 另一位编程专家随后发现了程序中的错误，对其进行了修改，并执行了更新后的程序。
5.为了确保输出的结果无误，元模型又请了一位数学专家来进行验证。
6. 经过核验，元模型最终给出了答案。
可以看到，通过在每一步骤中加入新的视角，元提示不仅能找到问题的解决方案，还能有效地发现并更正错误。
