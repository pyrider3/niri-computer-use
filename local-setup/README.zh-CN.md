# 当前 NiriComputerUse 部署记录

此仓库 fork 自 [ayagmar/niri-computer-use](https://github.com/ayagmar/niri-computer-use)，保留原 MIT 许可证和源码历史。本次保存配置与说明，尚未实现新的提速功能，也不修改当前运行的服务。

## 保存内容

- 主程序版本：0.1.5；Niri：26.04。
- 本机已安装二进制 SHA-256：`63a8acf3cfe0fefac2aeafcd9d493533185ab948ecf35d20fd79c4eec3a0c8df`。不在仓库重复上传可执行文件。
- 技能位于 `skills/niri-computer-use/`，本次已与本机安装版本逐字比较一致。
- `policy.toml` 保存允许启动所有程序的选择和微信预设；后台查看器作为可选预设，安装路径需自行填写。
- `codex.toml`、`pi-mcp.json` 是独立的最小合并片段，路径已脱敏，不包含其他 MCP、模型设置或账号。

## 安装与恢复

程序安装按仓库根目录 README 的上游流程进行；本部署基线是 0.1.5，恢复时应核对版本，不把最新版本当成相同基线。安装 skill 后，将本目录的配置片段合并到自己现有配置：策略在 `~/.config/niri-computer-use/policy.toml`，Codex 在 `~/.codex/config.toml`，Pi 在 `~/.pi/agent/mcp.json`。先备份原文件，替换模板中的 `/home/YOUR_USER`；不要直接覆盖完整 Codex 或 Pi 配置。

后台微信独立桌面与查看器见 [wechat-use](https://github.com/pyrider3/wechat-use)。主桌面控制使用本仓库，后台微信操作使用另一个仓库的 skill 和 MCP。

## 当前验证范围

2026-10-30 只读状态检查：服务 0.1.5、Niri 兼容、事件流已连接、无障碍可用、共享引擎开启、完整工具配置可用。其他会话当时持有租约，本次未接管桌面，未发送消息。此前本机已有中文粘贴与窗口操作实测，但本次上传不代表重新执行这些测试。

主桌面停止键为 Super+Shift+Esc；保留租约、焦点核对和用户恢复机制。`unrestricted = true` 是此部署的显式选择，允许启动任意程序，不是后台运行或隔离环境。

未上传截图、审计日志、聊天记录、运行时 socket、凭证或完整个人配置。

## 本次上传检查

配置 TOML / JSON 解析与 Git 空白检查通过。已运行 `make check`：格式、Clippy、文档构建通过，但当前环境缺少 cargo-deny，完整门禁在此停止，后续步骤未由该命令执行，不能称完整门禁通过。另行运行 `cargo test --all-targets --locked` 成功；尚未单独运行共享模式协议测试及 Noctalia 插件测试。本次仅增加部署文档和模板，没有修改运行代码。
