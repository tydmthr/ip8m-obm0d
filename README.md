# 豊田元洋 — Field Notes (公開用)

名刺QR遷移先のレスポンシブHTML。GitHub Pagesでホスティングする想定。

## 構成

```
public/
├── index.html      ← 単独ページ
├── style.css
└── assets/         ← 写真・QR・ロゴ
```

## GitHub Pages へのデプロイ手順

1. **新規リポジトリを作成**(プライベート可。Pagesはパブリックリポジトリ無料、プライベートはGitHub Pro以上が必要)
2. `public/` の中身をリポジトリのルート、または `docs/` フォルダに配置
3. リポジトリ Settings → Pages
   - Source: `main` ブランチ / `/ (root)` または `/docs`
   - Save
4. 数分待つと `https://<ユーザー名>.github.io/<リポジトリ名>/` で公開される

### URL を「読まれにくく」する工夫

- リポジトリ名をランダム文字列にする(例: `k7n9-xq2m4`)
  → URL: `https://<ユーザー名>.github.io/k7n9-xq2m4/`
- `<meta name="robots" content="noindex, nofollow">` は既に設定済み(検索エンジンには載らない)
- 名刺QRにはこのURLを直接埋め込む

### 独自ドメインを使う場合

`public/` 内に `CNAME` ファイルを作り、ドメイン名を1行で書く。

```
profile.toyodaeisei.com
```

## ローカル確認

```sh
cd public
python3 -m http.server 8000
# → http://localhost:8000
```

## 編集

- 文言・連絡先は `public/index.html` の中で直接書き換える
- 写真の差し替えは `public/assets/` 内の同名ファイルを上書き
- スタイルは `public/style.css`

## 注意

- noindex を入れていますが、URL を SNS 等に公開すれば誰でも見られます
- 「QRを読んだ人にだけ」を厳密にやるなら、Cloudflare Access / Netlify の Password Protection など、認証付きホスティングへの移行を検討してください
