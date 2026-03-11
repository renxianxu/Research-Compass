第一版：A multimodal research assistant that takes problem descriptions as input and returns relevant papers with mechanism, evidence, and trade-off analysis（一个面向多模态研究问题的科研助手：输入研究痛点描述，输出相关论文、方法机制、证据与代价分析）.

---

## Overview（项目简介）

MultiModal Research Compass（多模态科研罗盘） is a research support project focused on multimodal machine learning（MultiModal Research Compass 是一个聚焦多模态机器学习方向的科研辅助项目）.

Instead of relying only on keyword-based search（它不是只依赖关键词检索）, this project starts from a researcher's actual problem description（而是从研究者真实遇到的研究痛点描述出发）, such as:

- what problem they are working on（当前在做什么问题）
- what bottleneck they are facing（当前遇到的瓶颈）
- what constraints they must satisfy（必须满足哪些约束）
- what kind of methods they are looking for（希望找到什么类型的方法）
- what kinds of costs or assumptions are unacceptable（哪些代价或假设不可接受）

The system then converts the problem description into structured retrieval intents（系统会把这些问题描述转成结构化检索意图）, retrieves relevant multimodal papers（检索多模态相关论文）, and generates structured result cards（并输出结构化结果卡片）, including:

- why the paper is relevant（为什么相关）
- what mechanism it uses（它依赖什么机制）
- what evidence supports it（它有哪些实验支持）
- what trade-offs or risks it has（它有哪些代价与风险）
- whether it may fit the current research problem（它是否适合当前研究问题）

---

## Motivation（项目动机）

Keyword-based paper search is often insufficient for real research workflows（仅靠关键词搜索通常不足以支持真实科研流程）.

In multimodal research, a method that works well in one subproblem or neighboring setting may be highly relevant to another problem（在多模态研究中，一个在相邻问题上表现很好的方法，可能对另一个问题也很有启发）, but researchers may fail to retrieve it simply because they do not know the “right keywords” in advance（但研究者往往因为不知道“正确关键词”而检索不到）.

This project is designed to support a more problem-driven and judgment-oriented research workflow（本项目希望支持一种更“问题驱动、判断导向”的科研工作流）.

The goal is not to automatically decide which paper is “valuable” in an absolute sense（目标不是替研究者自动裁决哪篇论文“绝对有价值”）, but to help researchers:

- retrieve relevant work more effectively（更有效地找到相关工作）
- understand papers in a structured way（以结构化方式理解论文）
- connect methods to actual research pain points（把方法和真实研究痛点对应起来）
- identify trade-offs, assumptions, and transfer risks（识别方法的代价、前提与迁移风险）
- build stronger research taste over time（逐步提升科研判断力与科研品味）

---

## Current Scope（当前范围）

Version 1（第一版） only focuses on the multimodal research domain（第一版只聚焦多模态研究领域）.

The initial scope includes topics such as（初始覆盖范围包括）:

- missing modality / incomplete multimodal learning（模态缺失 / 不完整多模态学习）
- multimodal fusion（多模态融合）
- uncertainty-aware multimodal learning（不确定性感知的多模态学习）
- conflict-aware evidence fusion（冲突感知证据融合）
- multimodal alignment（多模态对齐）
- multimodal robustness（多模态鲁棒性）
- partial observation / sparse evidence settings in multimodal tasks（多模态任务中的部分观测 / 稀疏证据场景）

At this stage, the system is designed as a retrieval-and-analysis assistant rather than a full autonomous research agent（当前阶段，本系统定位为“检索与分析助手”，而不是“全自动科研智能体”）.

---

## Core Idea（核心思想）

The system does not begin with a paper title or a fixed keyword（系统不是从论文标题或固定关键词开始）.

Instead, it begins with a researcher’s problem description（它从研究者的研究痛点描述开始）.

### Example input（输入示例）

> I am working on multimodal sentiment analysis with missing modalities at test time.  
> I do not only want modality completion, but also robust downstream classification.  
> I also want uncertainty awareness, so that wrong completion does not mislead final decisions.  
> Existing methods often assume random missing patterns, but I care more about irregular and realistic missing scenarios.

The system should parse this input into structured research intents（系统会把这段话解析成结构化研究意图）, including:

- task（任务）
- bottleneck（瓶颈）
- constraint（约束）
- desired capability（目标能力）
- unacceptable assumptions or costs（不可接受的假设或代价）

Then it retrieves papers and outputs structured result cards（然后检索论文并输出结构化结果卡片）.

---

## What the System Returns（系统输出什么）

For each retrieved paper, the system generates a structured card with fields such as（对于每篇召回论文，系统会生成结构化结果卡片，包含如下信息）:

- Basic paper information（论文基础信息）
- Why it was retrieved（为什么被召回）
- What mechanism it uses（它使用什么机制）
- What evidence supports it（有哪些实验支持）
- What trade-offs it introduces（引入了哪些代价）
- Why it may fit the current research problem（为什么可能适合当前问题）
- Why it may not fit（为什么可能不适合）
- Transfer risks and assumptions（迁移风险与前提）

This makes the output closer to a research judgment aid rather than a generic summary tool（这使得系统输出更接近“研究判断辅助”，而不是普通摘要工具）.

---

## V1 Goals（第一版目标）

The first version aims to support the following workflow（第一版目标支持如下流程）:

1. Input a multimodal research pain point description（输入一段多模态研究痛点描述）
2. Parse the description into structured slots（解析成结构化槽位）
3. Generate multiple retrieval queries（生成多组检索查询）
4. Retrieve relevant multimodal papers（检索相关多模态论文）
5. Generate structured paper cards（生成结构化论文卡片）
6. Return a short synthesized summary（返回一段整体综合总结）

---

## What V1 Does Not Attempt（V1 暂不尝试做什么）

Version 1 does **not** aim to do the following（第一版**不以**以下内容为目标）:

- automatically write papers（自动写论文）
- automatically generate final research ideas（自动生成最终研究方案）
- fully replace human research judgment（完全替代人的科研判断）
- support all scientific domains（支持所有学科领域）
- build a full knowledge graph from the start（一开始就构建完整知识图谱）

Instead, V1 focuses on a narrower but more useful task（第一版更聚焦于一个更窄但更实用的任务）:
problem-driven multimodal paper retrieval and structured output（问题驱动的多模态论文检索与结构化输出）.

---

## Output Structure（输出结构）

Each result card is expected to contain the following sections（每张结果卡预期包含以下模块）:

### 1. Paper Basic Info（论文基础信息）
- title（标题）
- authors（作者）
- year（年份）
- venue / source（来源）
- link（链接）

### 2. Problem Match（问题匹配）
- which pain point it matches（匹配了你的哪个痛点）
- which desired capability it addresses（对应了你的哪个目标能力）

### 3. Method Mechanism（方法机制）
- method type（方法类型）
- core mechanism（核心机制）
- whether it focuses on fusion / completion / alignment / uncertainty / robustness（它主要关注融合、补全、对齐、不确定性还是鲁棒性）

### 4. Evidence（证据）
- datasets（数据集）
- metrics（指标）
- experimental support strength（实验支持强度）

### 5. Trade-offs（代价与权衡）
- model complexity（模型复杂度）
- data dependency（数据依赖）
- inference cost（推理代价）
- assumptions（关键前提）

### 6. Fit Assessment（适配性判断）
- why it may fit（为什么可能适合）
- why it may not fit（为什么可能不适合）
- transfer risk（迁移风险）

---

## Design Principles（设计原则）

This project follows several core principles（本项目遵循以下几个核心原则）:

- Problem first, keyword second（先问题，后关键词）
- Facts first, inference second（先事实，后推断）
- Research judgment support, not fake certainty（辅助研究判断，而不是制造虚假的确定性）
- Trade-off awareness matters（重视代价与权衡）
- Better retrieval should improve research taste, not just reading speed（更好的检索应当提升科研品味，而不仅是提升阅读速度）

---

## Future Directions（后续方向）

Possible future extensions include（后续可能扩展的方向包括）:

- multimodal problem–method graph（多模态问题—方法图谱）
- paper memory and note storage（论文记忆与笔记存储）
- project-specific relevance analysis（面向具体项目的相关性分析）
- comparison across retrieved methods（候选方法之间的比较）
- lightweight human-in-the-loop review flow（轻量人工审核流程）
- broader cross-domain retrieval（更广义的跨领域检索）

---

## Project Status（项目状态）

- [x] Project scope defined（项目范围已定义）
- [x] V1 objective defined（V1 目标已定义）
- [ ] Input schema implementation（输入 schema 待实现）
- [ ] Retrieval pipeline implementation（检索流程待实现）
- [ ] Paper card generator implementation（论文卡片生成器待实现）
- [ ] Memory / storage layer（记忆/存储层待实现）

---

## License（许可证）

MIT License（MIT 开源许可证）
