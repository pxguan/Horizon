---
layout: default
title: "Horizon Summary: 2026-05-06 (ZH)"
date: 2026-05-06
lang: zh
---

> From 45 items, 11 important content pieces were selected

---

1. [由于 DNSSEC 签名格式错误，.de 顶级域名全面瘫痪](#item-1) ⭐️ 9.0/10
2. [美国近 20 个州级医保平台向科技巨头泄露用户敏感数据](#item-2) ⭐️ 9.0/10
3. [OpenAI 发布 GPT-5.3 Instant，幻觉率最高降低 26.8%](#item-3) ⭐️ 9.0/10
4. [Google 发布 Gemma 4 多令牌预测草稿器，将推理速度提升高达 3 倍](#item-4) ⭐️ 8.0/10
5. [Anthropic 发布十款面向金融服务和保险行业的 AI 智能体模板](#item-5) ⭐️ 8.0/10
6. [谷歌 Chrome 在未经明确同意的情况下自动安装 4 GB 的 Gemini Nano AI 模型](#item-6) ⭐️ 8.0/10
7. [扎克伯格亲自授权 Meta 侵犯版权以进行 AI 训练](#item-7) ⭐️ 8.0/10
8. [Simon Willison 发布 Redis 原生数组类型的交互式测试场](#item-8) ⭐️ 8.0/10
9. [欧元区财长要求访问 Anthropic 的 Mythos AI 模型以评估安全风险](#item-9) ⭐️ 8.0/10
10. [GitHub 为近期故障致歉并宣布 30 倍基础设施扩容计划](#item-10) ⭐️ 8.0/10
11. [Google DeepMind 英国员工投票组建工会抗议军事 AI 合同](#item-11) ⭐️ 8.0/10

---

<a id="item-1"></a>
## [由于 DNSSEC 签名格式错误，.de 顶级域名全面瘫痪](https://dnssec-analyzer.verisignlabs.com/nic.de) ⭐️ 9.0/10

此次事件代表了德国主要域名空间的关键基础设施瘫痪，实际上使得数百万 .de 网站对于安全网络上的用户无法访问。这凸显了 DNSSEC 的脆弱性，一次单一的加密错误就能比标准服务器中断更彻底、更迅速地破坏全球连接。 技术分析表明，问题源于与密钥标签 33834 关联的 NSEC3 记录上的无效 RRSIG，导致验证解析器返回 SERVFAIL。底层的区域数据保持完整，这意味着中断纯粹是验证失败，而不是权威数据的丢失。

hackernews · warpspin · May 5, 20:16 · [社区讨论](https://news.ycombinator.com/item?id=48027897)

**背景**: DNSSEC 是一套旨在通过验证数据来源和完整性来保护 DNS 安全的加密扩展，它使用存储在 RRSIG 记录中的数字签名。验证解析器会根据信任锚检查这些签名；如果签名格式错误或验证失败，解析器会拒绝响应以防止潜在攻击。DENIC 是负责运营 .de 域名并维护其 DNS 基础设施的合作社。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cloudflare.com/learning/dns/dnssec/how-dnssec-works/">How does DNSSEC work? - Cloudflare</a></li>
<li><a href="https://www.rfc-editor.org/rfc/rfc4034">RFC 4034: Resource Records for the DNS Security Extensions</a></li>
<li><a href="https://www.denic.de/en/">DENIC eG: DENIC – Registry for all .de domains</a></li>

</ul>
</details>

**社区讨论**: 观察家指出，在如此大规模的顶级域名上发生这种灾难性的 DNSSEC 故障极为罕见，一些人指出中断的间歇性可能是由于任播传播造成的。虽然一些用户对此事轻描淡写，但其他人鉴于 .de 是一个重要的非限制性域名，强调了其严重的经济影响。

**标签**: `#DNSSEC`, `#Outage`, `#Infrastructure`, `#DNS`, `#Security`

---

<a id="item-2"></a>
## [美国近 20 个州级医保平台向科技巨头泄露用户敏感数据](https://www.bloomberg.com/features/2026-healthcare-advertising-trackers-privacy/) ⭐️ 9.0/10

调查显示，全美近 20 个州及华盛顿特区的政府医疗保险交易平台通过植入的广告追踪器，向 Meta、Google、TikTok 和 LinkedIn 等公司泄露了超过 700 万用户的敏感个人数据。泄露的具体信息包括公民身份、种族、性别、收入详情以及怀孕信息等。 这代表了政府数据处理方面的系统性失误，涉及将高度敏感的个人身份信息未经授权直接传输给科技巨头用于广告投放。这一事件凸显了第三方追踪像素在敏感网站上的严重隐私风险，并可能引发重大的法律和监管后果。 泄露发生的原因是州政府网站中嵌入的追踪像素捕获了用户在网页表单或 URL 参数中输入的数据，例如邮政编码和家庭详细信息。具体案例包括华盛顿特区向 TikTok 发送种族数据，以及弗吉尼亚州与 Meta 共享邮政编码以匹配 Facebook 个人资料进行定向广告投放。

telegram · zaihuapd · May 5, 03:06

**背景**: 追踪像素是一种嵌入在网页中的微小不可见图像（通常为 1x1 大小），当页面加载时会触发服务器请求，将数据发回给像素的所有者。虽然营销人员常用它来衡量广告效果和跟踪用户行为，但如果数据包含在页面 URL 或表单提交中，这些像素可能会无意中捕获个人身份信息（PII）。对于处理受保护健康信息（PHI）的医疗保健网站而言，这种做法尤其危险，因为美国的 HIPAA 等严格法规旨在保障患者隐私。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.thecybersignal.com/state-health-exchanges-sent-citizenship-race-data-tiktok-meta-bloomberg-investigation/">20 State Health Exchanges Leaked Citizenship Data to TikTok</a></li>
<li><a href="https://improvado.io/blog/what-is-tracking-pixel">What Is a Tracking Pixel? How It Works, Types, and Privacy Concerns in 2026</a></li>
<li><a href="https://www.malwarebytes.com/blog/news/2022/10/health-care-provider-notifies-patients-of-potential-breach-of-personal-data-due-to-tracking-pixels">Healthcare site leaks personal health information via Google and Meta tracking pixels</a></li>

</ul>
</details>

**标签**: `#Privacy`, `#Data Security`, `#Healthcare`, `#Web Tracking`, `#Policy`

---

<a id="item-3"></a>
## [OpenAI 发布 GPT-5.3 Instant，幻觉率最高降低 26.8%](https://t.me/zaihuapd/41231) ⭐️ 9.0/10

OpenAI 发布了 GPT-5.3 Instant，这是对 ChatGPT 日常对话模型的重大更新。新版本在启用网络搜索的情况下，将高风险领域的幻觉率最高降低了 26.8%，同时减少了不必要的拒绝回答，并提升了网络搜索结果的质量。 此次更新直接解决了 AI 可靠性的关键问题，特别是在医疗和金融等对准确性要求极高的敏感领域。通过显著降低幻觉率并减少过度拒绝，GPT-5.3 Instant 消除了企业采用 AI 的主要障碍，使 AI 交互更加流畅和值得信赖。 内部评测显示，在启用网络搜索的高风险领域中，幻觉率降低了 26.8%，而基于用户反馈的评测显示这一降幅为 22.5%。GPT-5.3 Instant 现已成为所有 ChatGPT 用户的默认模型，取代了 GPT-5.2 Instant，并已集成到 Microsoft 365 Copilot 中。

telegram · zaihuapd · May 5, 17:06

**背景**: 大型语言模型（LLM）有时会出现“幻觉”，即生成看似自信但事实错误或荒谬的信息。“拒绝处理”是指模型区分应被阻止的有害请求和应被回答的良性查询的能力，旨在避免过度拒绝安全提示词带来的挫败感。GPT-5.3 Instant 在先前版本的基础上进行了优化，旨在实现更安全、更有用的日常对话体验。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/gpt-5-3-instant/">GPT‑5.3 Instant: Smoother, more useful everyday conversations</a></li>
<li><a href="https://www.datacamp.com/blog/gpt-5-3-instant">GPT-5.3 Instant: Features, Tests, and Availability - DataCamp</a></li>
<li><a href="https://www.ibm.com/think/topics/ai-hallucinations">What are AI hallucinations? - IBM</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#GPT-5.3`, `#LLM`, `#Hallucination`, `#AI Safety`

---

<a id="item-4"></a>
## [Google 发布 Gemma 4 多令牌预测草稿器，将推理速度提升高达 3 倍](https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/) ⭐️ 8.0/10

此次更新显著减少了运行大型语言模型（LLM）时通常存在的延迟和内存带宽瓶颈，使高性能 AI 变得更加普及且更具成本效益。这巩固了 Google 在开源领域的强有力竞争地位，社区成员指出，像 llama.cpp 这样的本地运行时在速度和性能方面已经看到了显著提升。 MTP 方法通过将轻量级草稿模型与较大的目标模型配对来加速生成，目前对这种架构的支持正在被集成到 llama.cpp 等本地推理工具中。尽管 31B 版本提供了令人印象深刻的性能，但在启用视觉功能和草稿器的情况下运行它需要大量的显存，这对于硬件受限（例如仅拥有单块 24GB 显存 GPU）的用户来说是一个挑战。

hackernews · amrrs · May 5, 16:14 · [社区讨论](https://news.ycombinator.com/item?id=48024540)

**背景**: 推测解码是一种优化技术，其中一个更小、更快的“草稿”模型提出多个令牌，由一个更大的“目标”模型同时进行验证，从而减少所需的昂贵计算步骤。这解决了 LLM 推理中常见的内存带宽瓶颈问题，即速度往往受限于数据从内存传输的速度，而非计算速度本身。Gemma 是 Google 开发的一系列开放权重模型，旨在保持最先进性能的同时，足够高效以便在本地硬件上运行。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/">Accelerating Gemma 4: faster inference with multi-token ...</a></li>
<li><a href="https://app.daily.dev/posts/multi-token-prediction-in-gemma-4-p8wqk64sp">Multi-token-prediction in Gemma 4 | daily.dev</a></li>
<li><a href="https://conzit.com/post/gemma-4-speeds-up-ai-with-multi-token-prediction-drafters">Gemma 4 Speeds Up AI with Multi-Token Prediction Drafters</a></li>

</ul>
</details>

**社区讨论**: 用户们强调，Gemma 模型在基准测试中取得了接近 Qwen 等领先竞争对手的性能，但使用的令牌数量显著更少，执行速度也更快。社区对 MTP 支持集成到 llama.cpp 等本地运行环境感到兴奋，不过也有人担心，在消费级硬件上运行具有视觉功能等新特性的大型 31B 模型需要极高的显存。

**标签**: `#LLM Inference`, `#Gemma`, `#Google AI`, `#Optimization`, `#Open Source`

---

<a id="item-5"></a>
## [Anthropic 发布十款面向金融服务和保险行业的 AI 智能体模板](https://www.anthropic.com/news/finance-agents) ⭐️ 8.0/10

社区反应不一，许多用户对一家 AI 公司能否妥善处理敏感的金融数据和监管风险持怀疑态度。一些用户担心这一发布会威胁到该领域的数千家初创公司，而另一些人则讨论这些智能体是否能有效颠覆 Intuit 等现有巨头。

hackernews · louiereederson · May 5, 15:05 · [社区讨论](https://news.ycombinator.com/item?id=48023533)

**背景**: KYC, or 'Know Your Customer,' is a mandatory compliance process that involves verifying client identities against global watchlists and sanctions to prevent financial crimes. Financial auditing is a rigorous examination of an organization's financial records, traditionally involving manual sampling, which is increasingly being augmented by AI to analyze entire datasets for anomalies.

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.businessinsider.com/anthropic-ai-agent-tool-wall-street-finance-bank-2026-5">Anthropic Just Launched AI Agent Tools to Shake up Finance ...</a></li>
<li><a href="https://www.lseg.com/en/risk-intelligence/glossary/kyc/kyc-screening">KYC Screening in Compliance - Glossary | LSEG</a></li>

</ul>
</details>

**社区讨论**: Community reactions are mixed, with skepticism regarding whether an AI company can properly handle sensitive financial data and regulatory risks. Some users express concern that this announcement threatens thousands of startups in the space, while others debate whether these agents can effectively disrupt incumbents like Intuit.

**标签**: `#AI Agents`, `#FinTech`, `#Anthropic`, `#Enterprise Automation`, `#Regulatory Risk`

---

<a id="item-6"></a>
## [谷歌 Chrome 在未经明确同意的情况下自动安装 4 GB 的 Gemini Nano AI 模型](https://www.thatprivacyguy.com/blog/chrome-silent-nano-install/) ⭐️ 8.0/10

当启用 #optimization-guide-on-device-model 或 #prompt-api-for-gemini-nano 等特定标志时，系统会触发下载，允许网页通过 LanguageModel.create() API 调用该模型。在 Windows 系统上，该模型存储在 AppData\Local 目录中，这给使用漫游配置文件或共享网络存储的环境带来了挑战。 这一进展凸显了软件自主性的重大转变，即浏览器正演变为重型本地 AI 处理平台，从而引发了对存储管理和用户同意权的担忧。这对存储或带宽有限的企业管理员和用户产生了直接影响，并引发了关于自动更新界限的激烈争论。

hackernews · john-doe · May 5, 07:34 · [社区讨论](https://news.ycombinator.com/item?id=48019219)

**背景**: Gemini Nano 是谷歌设计的轻量级基础生成式 AI 模型，旨在本地设备上运行，以便在不将数据发送到云端的情况下处理任务。“端侧 AI”指的是直接在用户硬件上运行机器学习模型的实践，与在远程服务器上处理相比，这可以提高隐私保护并降低延迟。Chrome 正在整合这项技术以支持 Prompt API 等功能，从而允许开发者直接在浏览器内执行 AI 任务。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://developer.chrome.com/docs/ai/built-in">Built-in AI | AI on Chrome | Chrome for Developers</a></li>
<li><a href="https://developer.android.com/ai/gemini-nano">Gemini Nano - AI | Android Developers</a></li>
<li><a href="https://www.google.com/chrome/ai-innovations/">Gemini in Chrome | The next generation of AI in Chrome | Chrome</a></li>

</ul>
</details>

**社区讨论**: 用户意见不一，部分人认为这只是现有软件协议涵盖的标准组件更新，而另一些人则批评缺乏透明度以及巨大的存储占用。系统管理员特别表达了沮丧情绪，指出这对网络文件服务器的影响，以及在配置文件非持久化的实验室机器上管理这些大文件的困难。

**标签**: `#Privacy`, `#Google Chrome`, `#AI/ML`, `#Web Browsers`, `#Software Ethics`

---

<a id="item-7"></a>
## [扎克伯格亲自授权 Meta 侵犯版权以进行 AI 训练](https://variety.com/2026/digital/news/meta-ai-mark-zuckerberg-copyright-infringement-lawsuit-publishers-scott-turow-1236738383/) ⭐️ 8.0/10

诉讼文件显示，马克·扎克伯格亲自授权使用受版权保护的作品来训练 Meta 的 LLaMA 模型，并无视了授权方面的顾虑。这一披露将法律焦点从一般的企业政策转移到了针对公司激进数据抓取行为的具体高管责任上。 这一披露意义重大，因为它暴露了最高层高管参与了有关 AI 训练数据的决策，这可能使扎克伯格个人承担侵权责任。这加剧了关于抓取受版权保护的内容用于“变革性”AI 是否构成合理使用或盗版的法律和伦理辩论。 社区报告显示，Meta 的抓取工具激进地绕过了 robots.txt 和基于 IP 的速率限制等技术障碍来获取数据。法律论点依赖于区分“变革性使用”和为了训练目的而盗版作品的初始行为，这一区别与近期 Anthropic 15 亿美元的和解案有关。

hackernews · spankibalt · May 5, 18:04 · [社区讨论](https://news.ycombinator.com/item?id=48026207)

**背景**: 像 Meta 的 LLaMA 这样的大型语言模型（LLM）需要海量数据集才能运行，这往往导致公司从互联网上抓取包括受版权保护的书籍和文章在内的公开文本。这种做法的法律辩护通常依赖于“合理使用原则”，该原则允许出于教学、学术研究或新闻报道等目的在未经许可的情况下有限度地使用受版权保护的材料。然而，版权持有者辩称 AI 训练不符合合理使用的条件，并且直接与原作品竞争，这引发了一场关于数据使用未来的巨大法律斗争。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Llama_(language_model)">Llama (language model) - Wikipedia</a></li>
<li><a href="https://en.wikipedia.org/wiki/Fair_use_doctrine">Fair use doctrine</a></li>
<li><a href="https://hai.stanford.edu/news/reexamining-fair-use-age-ai">Reexamining "Fair Use" in the Age of AI - Stanford HAI</a></li>

</ul>
</details>

**社区讨论**: 社区内部存在严重分歧，一些人引用 Anthropic 的先例认为，无论模型是否具有变革性，为了训练而盗版作品都属于侵权。另一些人则强烈支持追究个人责任，并指出 Meta 无视 robots.txt 的历史，还有一些人希望扎克伯格败诉能确立一个先例，使所有人都能合法地免费获取科学论文。

**标签**: `#AI Copyright`, `#Legal Issues`, `#Meta`, `#LLM Training`, `#Ethics`

---

<a id="item-8"></a>
## [Simon Willison 发布 Redis 原生数组类型的交互式测试场](https://simonwillison.net/2026/May/4/redis-array/#atom-everything) ⭐️ 8.0/10

原生数组类型的引入代表了 Redis 的一次重大结构演进，可能会简化那些以前需要使用列表或集合来变通处理的数据建模用例。通过 WebAssembly 提供一种即时、可访问的方式来测试这些功能，开发者可以在代码正式合并之前评估这些更改的影响并提供反馈。 该实现引入了 18 个以 'AR' 为前缀的新命令，包括 ARGREP，它利用集成的 TRE 正则表达式库对数组值执行服务器端的 grep 操作。这个测试场本身是使用 Claude Code for web 构建的，并将特定的 Redis C 模块编译为 WebAssembly，从而无需后端服务器即可运行。

rss · Simon Willison · May 4, 15:53

**背景**: Redis 是一种流行的内存数据结构存储，传统上支持字符串、哈希、列表、集合和有序集合等数据类型。虽然开发者使用列表来存储有序数据，但列表缺乏随机访问能力，导致不得不使用 RedisJSON 或复杂的客户端逻辑来实现类似数组的行为。这种新的原生数组类型旨在直接在 Redis 核心引擎中提供高效的、可随机访问的序列，以满足社区长期以来的需求。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://antirez.com/news/164">Redis array type: short story of a long development -</a></li>
<li><a href="https://github.com/simonw/tools/pull/277">Add redis-array.html: in-browser playground for Redis Array (PR #15162) by simonw · Pull Request #277 · simonw/tools</a></li>

</ul>
</details>

**标签**: `#Redis`, `#Databases`, `#WebAssembly`, `#Developer Tools`, `#Data Structures`

---

<a id="item-9"></a>
## [欧元区财长要求访问 Anthropic 的 Mythos AI 模型以评估安全风险](https://www.bloomberg.com/news/articles/2026-05-04/euro-finance-chiefs-want-mythos-ai-access-to-prepare-defenses) ⭐️ 8.0/10

5 月 4 日，欧元区财政部长正式要求 Anthropic 向欧洲企业开放其尚未发布的 Mythos AI 模型访问权限，以评估系统性风险。此举旨在让欧洲实体能够针对该模型发现系统漏洞的能力建立防御体系，据报道，这一计划遭到了白宫的反对。 这一要求凸显了欧美在 AI 治理方面日益扩大的分歧，因为欧洲监管机构担心，若无法获取前沿模型，将在网络安全能力上落后于美国。这揭示了一个战略困境：即扣留强大的模型以防止全球滥用，同时也让主要盟友和金融系统在面对潜在威胁时毫无防备。 据报道，Mythos 能够大规模自主检测并利用先前未知的软件漏洞，已引发全球央行和情报机构的紧急响应。尽管 Anthropic 以安全为由限制访问，但欧洲官员认为，必须获得有限的访问权限，以便屏蔽支付系统和数字基础设施面临的这些特定风险。

telegram · zaihuapd · May 5, 03:30

**背景**: Anthropic 是一家领先的 AI 安全实验室，开发了“ Mythos ”，这是一个尚未发布的模型，因其过于强大而被公司认为不适合公开发布。据报道，该模型拥有发现软件漏洞的高级能力，引发了对金融和关键基础设施系统性网络安全风险的警报。目前，美国政府正与 Anthropic 就应如何严格控制此类强大模型的访问权限进行法律和战略层面的博弈。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.nytimes.com/2026/04/22/technology/anthropics-mythos-ai.html">Anthropic’s New Mythos A.I. Model Sets Off Global Alarms ...</a></li>
<li><a href="https://www.wsj.com/tech/ai/white-house-opposes-anthropics-plan-to-expand-access-to-mythos-model-dc281ab5">White House Opposes Anthropic's Plan to Expand Access to Mythos Model - WSJ</a></li>

</ul>
</details>

**标签**: `#AI Policy`, `#Cybersecurity`, `#Anthropic`, `#Geopolitics`, `#AI Safety`

---

<a id="item-10"></a>
## [GitHub 为近期故障致歉并宣布 30 倍基础设施扩容计划](https://github.blog/news-insights/company-news/an-update-on-github-availability/) ⭐️ 8.0/10

GitHub 详细说明了 4 月份的具体事故，包括 4 月 23 日影响 658 个仓库的合并队列故障（导致错误的 Squash 合并），以及 4 月 27 日因 Elasticsearch 集群过载导致的搜索服务中断。为了提高透明度，GitHub 已在其状态页添加可用性指标，并承诺公开所有规模的故障。 这一架构演进对于支持 AI 智能体巨大的计算需求，同时确保全球最大代码托管平台的稳定性至关重要。转向多云策略和采用 Go 等现代语言，解决了可扩展性的瓶颈，并降低了供应商锁定和单点故障的风险。

telegram · zaihuapd · May 5, 11:42

**背景**: GitHub 历史上一直依赖一个被称为“The Monorail”的大型 Ruby 单体架构，虽然这支持了敏捷开发，但在面对现代 AI 功能的性能需求时遇到了挑战。迁移到 Go 可以提供更好的并发性和资源效率，而转向多云架构则将风险分散到 Azure 等多个提供商之间，而不是依赖单一的基础设施。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue">Managing a merge queue - GitHub Docs</a></li>
<li><a href="https://www.newhorizons.com/resources/blog/multi-cloud-vs-single-cloud-whats-the-difference">Multi Cloud vs Single Cloud: What's the Difference? - New Horizons</a></li>

</ul>
</details>

**标签**: `#Infrastructure`, `#GitHub`, `#Scalability`, `#Cloud Migration`, `#Site Reliability`

---

<a id="item-11"></a>
## [Google DeepMind 英国员工投票组建工会抗议军事 AI 合同](https://www.theverge.com/tech/923918/google-deepmind-union-bid-ai-military-israel) ⭐️ 8.0/10

Google DeepMind 伦敦总部的 1000 多名员工正投票组建工会，以抗议公司与美国国防部及以色列政府签署的军事 AI 合同。员工们要求承诺不研发武器并建立独立的伦理监管机制，同时威胁称，如果诉求得不到满足，将对 Gemini 等核心产品发起“研究罢工”。 此次组建工会的行动标志着“科技伦理”辩论的重大升级，这是领先 AI 实验室首次专门为了抗议军事应用而组织劳工力量。“研究罢工”的威胁引入了一种强有力的新劳工筹码，可能会扰乱关键 AI 基础设施的开发进程。 此次抗议源于谷歌近期确认与美国国防部达成协议，允许美军使用其 AI 模型，以及备受争议的与以色列签署的价值 12 亿美元的 Project Nimbus 合同。谷歌曾在 2024 年因抗议该以色列合同而解雇了 50 多名员工，这标志着公司与员工之间的关系显著恶化。

telegram · zaihuapd · May 5, 12:36

**背景**: Project Nimbus 是谷歌与亚马逊联合签署的一项价值 12 亿美元的合同，旨在为以色列政府和军方提供云计算及 AI 基础设施。此次争议让人联想到 2018 年的“Project Maven”抗议事件，当时数千名谷歌员工要求公司取消五角大楼的 AI 合同，促使谷歌承诺不制造用于武器的 AI——而员工们现在认为这一承诺正遭到违背。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.businessinsider.com/google-deepmind-employees-unionize-vote-ai-military-contract-uk-2026-5">UK Google DeepMind Employees Vote to Unionize Over AI ...</a></li>
<li><a href="https://www.theguardian.com/us-news/2026/may/04/google-deepmind-uk-workers-union">Google DeepMind workers in UK vote to unionize amid deal with ...</a></li>
<li><a href="https://www.aljazeera.com/news/2024/4/23/what-is-project-nimbus-and-why-are-google-workers-protesting-israel-deal">What is Project Nimbus, and why are Google workers protesting ... Exclusive: Google Workers Revolt Over $1.2 Billion Israel ... What is Project Nimbus? Google's $1.2bn Israel Deal Explained The Hidden Ties Between Google and Amazon’s Project Nimbus ... Google Worried Israeli Contract Could Enable Human Rights ... Israel's $1.2 bn Nimbus deal asked Google, Amazon for 'secret ...</a></li>

</ul>
</details>

**标签**: `#AI Ethics`, `#Labor Rights`, `#Google DeepMind`, `#Military AI`, `#Tech Industry`

---