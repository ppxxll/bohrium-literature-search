# 中英文文献检索 Skill

一个用于 Codex 的文献检索 skill。输入研究主题后，它会分别寻找中文与英文论文，核对题目、作者、正式发表出处、年份、DOI 和摘要，并用中文整理每篇论文的方法与相关性。

> 本仓库提供的是 **Codex skill 指令与网站清单**，不是自动爬虫或文献数据库。每次检索仍需实时访问相应网站；全文权限取决于网站和用户的机构订阅。

## 功能

- **双语检索**：默认分别检索中文和英文论文；用户指定单一语言、数据库或时间范围时按要求调整。
- **按学科选站**：中文可选知网、万方、维普、NSTL、SinoMed 等；英文可选 Bohrium、IEEE Xplore、PubMed、OpenAlex 等。详见 [中文网站清单](references/chinese-sources.md) 与 [英文网站清单](references/english-sources.md)。
- **逐篇核验**：以论文详情页和出版方页面确认作者、DOI、卷期、正式出版年，区分预印本、网络首发和正式版本。
- **可追溯输出**：附论文链接、检索日期、实际访问的平台、摘要依据与访问限制；同一论文按 DOI 去重。

## 安装

下载或克隆仓库后，将**整个 `bohrium-literature-search` 文件夹**放到 Codex 的个人 skills 目录，保留 `SKILL.md` 与 `references/` 的相对位置：

```text
~/.codex/skills/
└── bohrium-literature-search/
    ├── SKILL.md
    └── references/
        ├── chinese-sources.md
        └── english-sources.md
```

若设置了 `CODEX_HOME`，目录为 `$CODEX_HOME/skills/bohrium-literature-search/`。Windows 默认位置通常是 `%USERPROFILE%\.codex\skills\bohrium-literature-search\`。在新的 Codex 任务中即可按名称调用；若未立即出现在可用 skills 列表，重启 Codex。

此 skill 本身没有 Python 依赖。可选的 `quick_validate.py` 校验脚本属于 Codex 的 skill-creator 工具，运行它才需要 PyYAML。

## 使用示例

```text
用 bohrium-literature-search 查找“多无人机动态任务分配”近五年的中英文文献，各选五篇，列出算法、约束、优化目标、出处和 DOI。
```

```text
查找“面向搜救的无人机任务分配”中文和英文综述，优先可公开阅读的论文。
```

结果通常分中文、英文两组。每篇包含题目、作者、期刊或会议、年份、DOI、基于摘要或全文的简要介绍、与主题的关系及来源链接。数量、格式和筛选条件可在提问时指定。

## 检索与核验原则

1. 分别设计中文和英文检索词，按主题选择互补平台，而不是逐个查询清单中的所有网站。
2. 聚合检索平台用于发现候选论文；论文出处与正式版本优先以出版方、会议或期刊官网核对。
3. 搜索结果片段和 AI 自动生成的摘要不等于作者摘要；无法核实的字段标为“未查到”。
4. 知网等网站可能需要登录，部分出版平台需要订阅。访问失败时改查可访问来源，并说明实际检索范围，不绕过访问控制。
5. 预印本不视为已同行评审的期刊论文；同一论文的预印本与正式版合并呈现。

## 仓库内容

| 文件 | 用途 |
| --- | --- |
| [`SKILL.md`](SKILL.md) | Codex 的触发描述、检索流程和输出规范 |
| [`references/chinese-sources.md`](references/chinese-sources.md) | 中文文献网站、覆盖范围与选站建议 |
| [`references/english-sources.md`](references/english-sources.md) | 英文文献网站、覆盖范围与选站建议 |

网站入口、收录范围与访问政策可能变化。正式使用时以网站当前页面及论文原始出版记录为准。
