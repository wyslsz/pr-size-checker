# PR Size Checker 🚦

GitHub Action 检查 Pull Request 的大小，防止巨型 PR 合并，保证代码审查质量。

## 使用方法

```yaml
name: PR Check
on: [pull_request]
jobs:
  size-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: wyslsz/pr-size-checker@main
        with:
          max_files: 50   # 最大文件数
          max_lines: 500  # 最大行数
          warn_files: 20  # 警告阈值
          warn_lines: 200
```

## 参数

| 参数 | 默认 | 说明 |
|------|------|------|
| max_files | 50 | 超过此文件数则失败 |
| max_lines | 500 | 超过此行数则失败 |
| warn_files | 20 | 超过此文件数则警告 |
| warn_lines | 200 | 超过此行数则警告 |

## 效果

- ✅ 小 PR → 通过
- ⚠️ 中等 PR → 警告但通过
- ❌ 巨型 PR → 失败，阻止合并

