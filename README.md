## データサイエンス演習 演習ファイル

![R](https://img.shields.io/badge/R-4.x-blue?logo=r) ![Jupyter](https://img.shields.io/badge/Jupyter-R%20kernel-orange?logo=jupyter) ![Status](https://img.shields.io/badge/status-active-success)

`main.ipynb` を R カーネルで実行し、公開データの読み込み・前処理・可視化の基本を学ぶためのリポジトリです。`img/` には演習内容の図を収録しています。

### 特徴
- **R 前提**: tidyverse ベースのモダンなワークフロー
- **再現性**: ノートブック手順に沿って図を再現可能（参考画像あり）
- **シンプル**: 必要最小限のセットアップで開始できます

### 構成
- `main.ipynb`: 演習用ノートブック（R カーネル想定）
- `data/`: サンプルデータ
  - `2016_ec.csv`
  - `TokyoTemp2.csv`
  - `TrafficAccidents.csv`
- `img/`: 参考図（`1-1-1.png` など）
- `README.md`: 本ドキュメント

### 前提環境
- R 4.x（4.2 以上推奨）
- JupyterLab/Notebook + IRkernel（R カーネル）または RStudio + `quarto` でも閲覧可

### セットアップ（Jupyter + R カーネル）
1) R パッケージをインストール
```r
install.packages(c("IRkernel", "tidyverse", "data.table", "lubridate", "readr", "ggplot2", "scales"))
IRkernel::installspec()  # Jupyter に R カーネルを登録
```
2) Jupyter を起動し、R カーネルで `main.ipynb` を開く
```bash
jupyter lab  # もしくは jupyter notebook
```

### 使い方（基本フロー）
1. `main.ipynb` を R カーネルで開く
2. 上から順にセルを実行
3. 必要に応じて可視化のパラメータを調整し、`img/` の図に近い出力を再現

### データ概要
- `data/2016_ec.csv`: EC に関するサンプル（列の意味はノートブックで説明）
- `data/TokyoTemp2.csv`: 東京の気温データ（期間・列はノートブック参照）
- `data/TrafficAccidents.csv`: 交通事故に関するサンプル

注: 学習用ダミーや加工済みの可能性があります。実務適用時はデータ辞書を確認してください。

### 図の再現と保存
ノートブック内の可視化セルを実行すると、`img/` と同名/同等の図を生成できます。保存パスはノートブックで指定している場合があります。

### スタイルと可読性のヒント（R）
- `theme_minimal()` などの ggplot テーマを活用し、`scale_*_continuous(labels = scales::label_comma())` で軸ラベルを見やすく
- 日本語フォントが必要な場合は `showtext` やシステムフォントの設定を検討

```r
library(ggplot2)
library(scales)

ggplot(df, aes(x = x, y = y, color = group)) +
  geom_line(linewidth = 1) +
  scale_y_continuous(labels = label_comma()) +
  theme_minimal(base_size = 13)
```

### トラブルシュート
- 日本語表示が豆腐: フォント設定（`showtext::showtext_auto()` など）を確認
- カーネルが見つからない: `IRkernel::installspec()` を再実行し、Jupyter を再起動
- パスエラー: 実行ディレクトリがリポジトリ直下か確認

### ライセンス / 貢献
商用利用問わず、二次利用を禁止します。


