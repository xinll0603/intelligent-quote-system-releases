# 智能化报价系统 Releases

此仓库仅用于发布智能化报价系统 Windows 安装包和 `update-manifest.json`，供客户端安全检查、下载和校验更新。

- 源代码不在此公开仓库中。
- 安装包由客户端按文件大小和 SHA-256 校验。
- 当前为个人/内部使用的未签名版本，Windows 可能显示未知发布者提示。

## 大文件可靠发布

大型 Windows 更新包先以小型编号分片推送到临时 `upload/<版本>-<哈希>`
分支，再由 `Assemble and publish release asset` GitHub Actions 工作流在云端
完成合并。工作流会同时核对文件大小、SHA-256 和 `update-manifest.json`，
全部一致后才允许覆盖现有 Release 资产。

该流程不公开私有源码、不新增个人访问令牌，也不要求本机长时间保持单个
大文件上传连接。临时分支仅在远端 Release 资产及 digest 独立复核通过后删除。
