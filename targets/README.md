# 画像ターゲットファイルの作成手順

MindAR の `.mind` ファイルを作成して `targets/animals.mind` として置いてください。

## 手順

### 1. 動物写真を用意する
- 各動物につき1枚、高解像度の写真を準備
- 推奨: 白または単色背景、高コントラスト、被写体が画面の60〜80%を占める
- 解像度: 1000×1000px 以上推奨

### 2. MindAR オンラインコンパイラで変換する
https://hiukim.github.io/mind-ar-js-doc/tools/compile

1. 上記 URL を開く
2. 「Add Images」ボタンで動物写真を順番通りにアップロード
   - アップロード順 = `index.html` の `TARGET_CONFIG` の `index` 番号と一致させる
3. 「Export」ボタンで `targets.mind` をダウンロード

### 3. ファイルを配置する
```
test-ar/
└── targets/
    └── animals.mind   ← ここに置く
```

### 4. TARGET_CONFIG を確認・編集する

`index.html` の冒頭にある `TARGET_CONFIG` を編集して、
コンパイラにアップロードした順番と動物キーを対応させてください。

```javascript
const TARGET_CONFIG = [
  { index: 0, key: 'cat',   scale: 0.3 },  // 0番目にアップロードした写真 = ネコ
  { index: 1, key: 'dog',   scale: 0.3 },  // 1番目 = イヌ
  // ...
];
```

### 5. スケール調整
`scale` の値でモデルの大きさを調整できます。
- A5サイズ（約15cm幅）印刷の場合: `scale: 0.3` が目安
- 大きくしたい場合は値を増やす（例: `0.5`）
- 小さくしたい場合は値を減らす（例: `0.2`）

## 注意点

- このファイル（`README.md`）は配布の際に削除しても構いません
- `animals.mind` がない場合、アプリは自動的に QR コードモードで動作します
- ファイルは HTTPS サーバー上に置く必要があります（カメラアクセスに HTTPS 必須）

## 有効な動物キー

| key | 動物 | key | 動物 |
|-----|------|-----|------|
| cat | ネコ | elephant | ゾウ |
| dog | イヌ | bear | クマ |
| horse | ウマ | zebra | シマウマ |
| sheep | ヒツジ | giraffe | キリン |
| cow | ウシ | rabbit | ウサギ |
