# Chinese-News-Classification-Paddle
百度飞桨比赛：中文新闻文本标题分类 分数：0.9+

Baidu Paddle competition: Chinese News Text Title Classification score: 0.9+

## 1.1 赛题简介：

本次比赛为新闻标题文本分类 ，要求参赛者基于原始新闻标题文本数据训练模型，从而判断其所属类别。

## 1.2 数据介绍：

THUCNews是根据新浪新闻RSS订阅频道2005~2011年间的历史数据筛选过滤生成，包含74万篇新闻文档（2.19 GB），均为UTF-8纯文本格式。在原始新浪新闻分类体系的基础上，重新整合划分出14个候选分类类别：财经、彩票、房产、股票、家居、教育、科技、社会、时尚、时政、体育、星座、游戏、娱乐。

为了使参赛者快速进入比赛核心阶段，我们已将训练集按照“标签ID+\t+标签+\t+原文标题”的格式抽取出来，参赛者可以直接根据新闻标题进行文本分类任务，希望参赛者能够给出自己的解决方案。

## 1.3 模型思路：

基于PaddleNLP，微调预训练模型 bert-wwm-ext-chinese 获得比赛单模高分；
更换并微调其他预训练模型 ernie-3.0-xbase-zh、roberta-wwm-ext-large和nezha-large-wwm-chinese；
使用“伪标签法”，将不同模型相同预测结果数据加入训练集，提升模型效果；
采用“加权投票融合法”对多模型预测结果融合，提高分数达到0.9+

fine-tuning文件

## 1.4 伪标签：
伪标签方法主要是将模型对无标签的测试数据的预测结果加入到训练中去从而增大训练数据量提升模型效果，适用于模型精度较高的情况。考虑到单模型准确度0.89+还算较高故采用了该技巧。
