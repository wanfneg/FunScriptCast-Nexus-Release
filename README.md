# FunScriptCast-Nexus

本项目由我个人借助 AI 工具开发。个人精力的付出、AI 工具的使用都有成本，而项目**免费**提供给大家使用。

欢迎大家体验，并提出 **BUG 反馈、功能需求、优化建议**。也欢迎大家投喂白饭给大肥鱼，助力项目开发。

<p align="center">
  <img src="docs/sponsor/meme.jpg" alt="梗图" width="420">
</p>

<p align="center">
  <img src="docs/sponsor/wechat.png" alt="微信赞助" width="300">
  &nbsp;&nbsp;&nbsp;
  <img src="docs/sponsor/alipay.jpg" alt="支付宝赞助" width="300">
</p>

**沟通渠道**：QQ `2831691505`

---

面向 VR 观影的 PC 端控制中枢：**DLNA 媒体服务 + AI 实时字幕 + 设备联动**，一个窗口、一个托盘。

> 本仓库是**安装包发布仓库**（仅发布文件，不含源码，源码仓库为私有）。
> 请在 [Releases](https://github.com/wanfneg/FunScriptCast-Nexus-Release/releases) 页面下载最新版本。

## 主要功能

- **DLNA 媒体服务**：把电脑 / 网盘挂载目录变成头显可浏览的媒体库（DeoVR 等 DLNA 播放器直接播放，零拷贝）
- **AI 实时字幕**：观看日语（可扩展多语言）视频时实时生成中文字幕——头显推音频、PC 识别并翻译，头显浮层同步显示
  - 识别引擎双选一：**Whisper**（日文特化，默认）/ **Qwen3**，界面一键切换
  - 翻译后端：本地大模型（llama.cpp + Sakura，离线免费）或云端 OpenAI 兼容 API，界面切换
  - 模型**一键下载**：走 hf-mirror 镜像，断点续传、进度显示；也可手动放置模型文件
  - 字幕缓存：同一视频看第二遍直接出字幕，不再重算
- **设备同步**：funscript 脚本与视频一键增量推送到 Quest（应用自带 adb，无需安装 Android 工具）
- **开箱即用**：自包含运行时（无需装 Python / Node / Android SDK），托盘常驻，DLNA 开机自启可选

## 下载与安装

| 文件 | 说明 |
|---|---|
| `FunScriptCast-Nexus-Setup-1.0.18.exe`（111 MB） | 安装包（核心框架 + 自包含运行时 + adb） |
| `llama-runtime-windows.zip`（627 MB） | 本地翻译运行时（llama.cpp · CUDA），在程序内也可一键下载 |

1. 运行 Setup 安装（默认装到 `%LOCALAPPDATA%\Programs`，不需要管理员）
2. 常规功能（DLNA / 设备同步）安装即可用
3. **AI 字幕**：打开「AI 字幕」页 → 按需点下载（识别模型 / 翻译模型 / 本地翻译运行时）→ 重启字幕服务
   - 用**云端翻译**：只需识别模型（约 1.4 GB）+ 自己的 API Key
   - 用**本地翻译**（离线免费）：识别模型 + 翻译模型（4 GB，推荐）+ 本地翻译运行时（627 MB）

## 硬件与系统要求

| 项目 | 要求 |
|---|---|
| 系统 | Windows 10 / 11 x64 |
| 显卡 | AI 字幕需 NVIDIA 显卡（8GB 显存可跑本地识别 + 翻译；无 N 卡时 Whisper 自动降级 CPU，云端翻译不受影响） |
| 头显 | Meta Quest / Pico（DLNA 播放器或配套 VR 端） |

## 支持平台

| 平台 | 安装包 |
|---|---|
| Windows 10 / 11 x64 | `FunScriptCast-Nexus-Setup-1.0.18.exe` |

## 说明

- 源码仓库为私有；本仓库仅发布安装包与运行时文件
- AI 识别 / 翻译模型与 llama.cpp 运行时不随安装包分发，由程序内按需下载（模型上游为 hf-mirror 公开仓库，运行时为本仓库资产）
- 本地翻译模型（Sakura 系）遵循 CC BY-NC-SA 4.0 许可，仅供个人学习使用
