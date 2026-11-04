# GCP 个人 API 中心

自托管的多媒体 API 控制台前端，配合 GCP 上的 Caddy 网关使用。

## 服务

| 路由 | 后端 | 说明 |
|---|---|---|
| `/translate` | LibreTranslate | 文本翻译 |
| `/tts/v1/audio/speech` | tts-daemon (Piper) | 语音合成 |
| `/stt/v1/audio/transcriptions` | Speaches (faster-whisper) | 语音识别 |
| `/stats` | 服务器指标 | 状态面板 |

## 使用

1. 打开页面，输入访问密码。密码哈希存于 `index.html` 的 `PWD_HASH`（SHA-256），换密码时本地生成新哈希替换即可，明文不出现在任何文件里
2. 服务器地址默认 `https://gcp.111312.xyz`（Cloudflare 代理），也可填 IP
3. 密码解锁后 7 天内免重复输入

## 部署（Cloudflare Pages）

- 连接本 GitHub 仓库，构建命令留空，输出目录 `/`（纯静态单文件）
- 或直接把 `index.html` 拖入 Cloudflare Pages 的 Direct Upload

## 源站架构

GCP VM 上 Docker 跑 Caddy 网关 + libretranslate + tts + stt + RustDesk，Caddy 反代见 `/etc/caddy/Caddyfile`。
