# 更新日志

按 Git 提交日期整理。每个日期块可展开查看当日推送内容，提交号用于回溯具体改动。

<details>
<summary><strong>2026-06-05</strong> - OpenRouter 出图尺寸修复与风格板停止</summary>

- 修复 OpenRouter 生图只按默认尺寸输出的问题，请求会同时发送 `image_config.aspect_ratio` 和 `image_config.image_size`。
- A+ 这类非 1:1 图片会按目标尺寸映射到 OpenRouter 支持的最接近比例，减少显示 2K/4K 但实际只有 1024 级别的情况。
- 生成风格板时新增“停止”按钮，可中断正在进行的风格图请求。
- 将停止信号接入 OpenRouter、OpenAI Images API、自定义接口和 fal 请求链路。
- 提交：`dd63338` 修复 OpenRouter 出图尺寸并支持停止风格板生成。

</details>

<details>
<summary><strong>2026-06-04</strong> - OpenRouter 生图 404 修复</summary>

- 修复 OpenRouter 配置在普通 Images API 路径下报 404 的问题。
- OpenRouter 图片模型改为通过 Chat Completions 生图路径调用。
- 新增 OpenRouter 图片模型识别逻辑，允许 OpenRouter 图片模型作为可生图配置使用。
- 设置页和 Amazon 策划页增加 OpenRouter 图片模型相关提示。
- 补充 OpenRouter 路由、输入图、重试和配置识别测试。
- 提交：`9cdecd0` 修复 OpenRouter 生图 404 问题。

</details>

<details>
<summary><strong>2026-06-03</strong> - 参考图压缩与 413 错误修复</summary>

- 修复参考图过大导致接口返回 413 的问题。
- 新增参考图请求前处理逻辑，对过大的图片进行压缩、尺寸控制和负载校验。
- AI 策划和生图请求都会使用处理后的参考图数据，降低请求体超限概率。
- 增加参考图压缩与负载处理测试。
- 提交：`dc5e54d` 修复参考图过大导致的 413 错误。

</details>

<details>
<summary><strong>2026-06-02</strong> - 普通生图接口限制与在线体验文档</summary>

- 普通生图限制为使用 Images API，避免误用 Chat Completions 等不支持普通生图的配置。
- OpenRouter 图片模型保留可用入口，作为 Chat Completions 生图的兼容例外。
- 设置页和生成入口增加更明确的接口类型提示。
- README 新增在线体验地址和线上使用说明。
- 提交：`031069d` 限制普通生图仅使用 Images API。
- 提交：`56be7df` docs: add online demo link。

</details>

<details>
<summary><strong>2026-06-01</strong> - 策划引导、API 默认配置与启动脚本优化</summary>

- Windows 启动脚本在启动前自动检查并安装依赖，减少首次运行失败。
- 优化 Amazon 策划页的引导、控件和 Prompt 生成体验。
- 调整 API 配置默认值，补充 OpenAI 兼容配置与 URL 参数处理测试。
- 更新图片编辑流程和 A+ 策划规则，让编辑、重试和历史继承更稳定。
- 增强 Listing / A+ 策划 Prompt、风格控制、图片位选择和合规提示。
- 提交：`bff26ca` Install dependencies before bat startup。
- 提交：`7d13774` Improve planner guidance and API profile defaults。
- 提交：`ed43bf5` Update image edit workflow and A+ planning rules。
- 提交：`73c70f4` Improve Amazon planner prompts and controls。

</details>

<details>
<summary><strong>2026-05-31</strong> - 安装说明与历史记录清理</summary>

- README 增加更完整的本地安装、启动和交付给他人使用的说明。
- 历史记录搜索栏增加清理能力，便于清空或管理历史任务。
- 提交：`a85312c` Add install guidance and history clearing。

</details>

<details>
<summary><strong>2026-05-30</strong> - 项目命名更新</summary>

- 项目名称统一调整为“亚马逊图片工作台”。
- 同步更新页面标题、PWA manifest、启动脚本和界面文案。
- 提交：`7c231bf` Rename app to Amazon image workbench。

</details>

<details>
<summary><strong>2026-05-29</strong> - Amazon 策划工作流与默认出图参数升级</summary>

- 大幅更新 Amazon Planner 工作流，强化 Listing 图片和 A+ 图片的策划、选择、生成流程。
- 调整图片默认参数、历史记录字段、任务展示和分类继承逻辑。
- 更新 dev proxy、mock image API、接口兼容测试和参数兼容逻辑。
- 增加 A+ / Listing 相关测试覆盖，整理 Amazon 知识规则和策划接口。
- 提交：`899532d` Update Amazon planner workflow and image defaults。

</details>

<details>
<summary><strong>2026-05-26</strong> - Amazon 知识规则内置与中文本地化</summary>

- 内置 Amazon 图片规范、附图策划逻辑和 A+ 尺寸知识文档。
- 策划接口会引用内置知识规则，提高 Listing / A+ 策划稳定性。
- 应用名称、赞助链接、启动脚本和界面文案进一步中文本地化。
- 合并一次策划文案工作流相关 PR。
- 提交：`5cc09c4` Embed Amazon planning knowledge rules。
- 提交：`0c8b9ec` Merge pull request #2 from Ali-Aria/codex/planner-copy-workflow-guidance。
- 提交：`d1de756` Localize app name and sponsor link。

</details>

<details>
<summary><strong>2026-05-25</strong> - Amazon 策划流程文案优化</summary>

- 明确 Amazon Planner 的工作流说明和页面文案。
- 优化 Listing 图片策划模板、复制逻辑和相关测试。
- 合并一次策划文案工作流相关 PR。
- 提交：`81a3fbd` Merge pull request #1 from Ali-Aria/codex/planner-copy-workflow-guidance。
- 提交：`3778620` Clarify Amazon planner workflow and copy language。

</details>

<details>
<summary><strong>2026-05-24</strong> - 项目初始化、部署配置与 A+ 模板完善</summary>

- 完成项目初始化，包含前端应用、图片生成、图片编辑、历史记录、设置页、PWA、代理和部署基础配置。
- 配置 GitHub Pages 工作流，并支持 main 分支推送后部署。
- 更新部署文档、安装路径说明和项目 GitHub 链接。
- 完善 README 使用说明。
- 优化 A+ Planner 模板、模块文案和任务历史展示。
- 默认关闭流式输出，降低默认配置复杂度。
- 提交：`ab63d9b` Initial commit。
- 提交：`78ef9ea` Update deployment docs。
- 提交：`3826fbc` Fix README install path。
- 提交：`ae118af` Update project GitHub links。
- 提交：`94c5cca` Deploy Pages on main push。
- 提交：`d929bdc` Configure GitHub Pages workflow。
- 提交：`5860ddd` Disable streaming by default。
- 提交：`93f9585` Improve A+ planner templates and copy。
- 提交：`f9198cb` Update README usage docs。

</details>
