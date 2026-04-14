# research-notebook CLAUDE.md

## ファイル操作ポリシー

| パス | 操作権限 |
|-----|---------|
| `plans/auto-*.md` | 読み取り・編集可（パイプラインが自動生成） |
| `plans/*.md`（`auto-` なし） | `@claude` へのメンション時のみ編集可 |
| `reports/auto-*.md` | 読み取りのみ（パイプラインが書き込む） |
| `reports/*.md`（`auto-` なし） | 変更禁止（人間の記録） |
| `README.md` | 変更禁止 |
| その他 | 変更禁止（明示的に許可されたファイルのみ操作） |

## ファイルの新規作成・削除

- `plans/auto-*.md` の**新規作成**は許可（パイプラインからのコミット）
- **削除は一切禁止**
- `auto-` プレフィックスのないファイルの作成は禁止

## ラベル運用

| ラベル | 意味 | 遷移先 |
|-------|------|-------|
| `plan:proposed` | パイプラインが計画案を生成 | 人間レビュー待ち |
| `plan:approved` | 人間がレビューして承認 | `plan:run` 付与待ち |
| `plan:run` | 実行トリガー（research-pipeline に dispatch） | Phase 3 実行中 |
| `plan:completed` | Phase 3 完了・Issue クローズ | 終了 |

## 禁止事項

- APIキー・パスワード・秘密鍵のコミット
- `main` ブランチへの直接コミット（PR 経由のみ）
- `reports/` 配下の人間記録ファイルの変更・削除
