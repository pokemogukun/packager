#ターボワープパッケージ

Https://packager.turbowarp.org/

Scratch プロジェクトを HTML ファイル、zip アーカイブ、または Windows、macOS、および Linux の実行可能プログラムに変換します。

## 開発

依存関係をインストールする：

```

Npm ci

```

開発モードで開始：

```

Npmスタート

```

その後、http://localhost:8947にアクセスしてください。手動で更新して変更を確認します。

開発モード中に生成されたパッケージ化されたプロジェクトは、配布しないでください。代わりに、本番ビルドを実行して、Webサイトとパッケージの両方のファイルサイズを大幅に縮小する必要があります。

```

Npm 実行 build-prod

```

出力は `dist` フォルダにあります。

`src`の一般的なレイアウトは次のとおりです。

- packager: プロジェクトをダウンロードしてパッケージ化するコード。

- p4: パッケージャーのSvelteウェブサイト。「p4」は、パッケージャーが内部で自分自身を指すために使用する名前です。

- 足場：最小限のスクラッチプロジェクトプレーヤー。マウス入力の取り扱いなど、スクラッチプロジェクトの実行に関する退屈な詳細のほとんどを処理します。

- 共通：足場とパッケージの両方で使用されるいくつかのファイル。

- アドオン：ゲームパッドのサポートやポインターロックなどのオプションのアドオン。

- ロケール：翻訳。en.jsonには、元の英語のメッセージが含まれています。他の言語はボランティアによって翻訳され、自動スクリプトによってインポートされます。（[あなたは助けることができます]（https://docs.turbowarp.org/translate））

- ビルド：Webpackプラグインやローダーなどのさまざまなビルドタイムスクリプト。

##フォークのヒント

TurboWarp に基づいていない mod であっても、パッケージをフォークしやすくするよう努めています。少なくとも前半は、このセクションを読むと、そうすることがはるかに簡単になるはずです。

###パッケージ

Scratch-vm/scratch-render/scratch-audio/scratch-storage/etc. を変更する場合は、簡単です。

- `npm install` または `npm link` あなたのパッケージ。パッケージ名は関係ありません。

- src/scaffolding/scratch-libraries.js を更新して、お持ちの名前のパッケージをインポートします。（一部のパッケージには `@turbowarp/` の接頭辞が付いていますが、他のパッケージはまだ `scratch-vm` です。一致していることを確認してください）

その後、再構築するだけです。バニラスクラッチVMをインストールしても、すべてのコア機能は引き続き機能します（ただし、補間、高品質のペン、ステージサイズなどのオプション機能は機能しない場合があります）

Npmは非常にバグのあるソフトウェアであり、依存関係ツリーは非常に大きいことに注意してください。依存関係が欠落しているというエラーが発生することがありますが、`npm install`を実行すると消えます。

### 展開
