# 我的思想库 · 手机阅读入口

一个单页 HTML，把 GitHub 私人仓库里的 Markdown 笔记变成手机上一个点开就能看的列表。

## 为什么需要它

笔记存在私人仓库里，但 GitHub 的网页版在手机上翻文件很费劲：一层层点目录、等加载、找不到想看的。

这个页面把整棵树拉平成一个列表，能搜、能按类筛、能点开就读。

## 怎么用

1. 手机浏览器打开 `https://wdfxf.github.io/notes/`
2. 第一次进去填两样：仓库名（已预填）+ 一个 GitHub Token
3. 之后直接点开就有内容

**Token 只存在你自己浏览器的 localStorage 里，不会发送到 GitHub 以外的任何地方，也不会进这个仓库。**
这个页面是公开的，但没有 token 的人打开只能看到一个空列表。

## 技术说明

- 纯静态单文件，无框架无外部依赖（Markdown 渲染器是手写的）
- 数据源：GitHub REST API
  - `GET /repos/{owner}/{repo}/git/trees/{branch}?recursive=1` — 文件列表
  - `GET /repos/{owner}/{repo}/contents/{path}` — 文件内容（base64 解码为 UTF-8）
- 已读文件本地缓存 1 小时；文件列表每次刷新重新拉
- 支持 `[[双链]]` 点击跳转、表格、引用、代码块、行内 HTML（`<span style>` 保留，判据红色高亮能正常显示）

## 局限

- 只能看，不能改（改还是回到电脑上的 Obsidian）
- 文件名搜索，不做全文搜索（全文搜索要把所有文件拉一遍，手机上太重）
- Token 过期后需要重新填

## License

MIT
