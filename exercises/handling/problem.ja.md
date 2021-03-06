パス"`/`"へのリクエストに対し、静的なHTMLファイル`index.html`の内容を返す
サーバーを作成して下さい。`index.html`の内容は以下のとおりです。

```html
<html>
    <head><title>Hello Handling</title></head>
    <body>
        Hello Handling
    </body>
</html>
```

-----------------------------------------------------------------
## ヒント

このエクササイズをするために、`@hapi/inert`モジュールをインストールする
必要があります。これはhapiのプラグインで、静的なファイル、あるいは
ディレクトリを扱うためのものです。このモジュールを使用するためには、
コードの中でプラグインをhapiに登録する必要があります。

```js
var Inert = require('@hapi/inert');

await server.register(Inert);
```

ハンドラは関数ではなく、オブジェクトとして宣言することが出来ます。
オブジェクトは次の何れかを持ちます。

* `file` (要`@hapi/inert`プラグイン)
* `directory` (要`@hapi/inert`プラグイン)
* `proxy` (要`@hapi/h2o2`プラグイン)
* `view` (要`@hapi/vision`プラグイン)

以下は`file`キーを持つオブジェクトをハンドラとして設定する例です。

```js
handler: {
    file: "index.html"
}
```

[注意]
実際にはプログラムディレクトリの中にある`index.html`への絶対パスを
指定する必要があるでしょう。このパスを取得するために、`path`コア
モジュールの`join()`関数、及びグローバル変数の`__dirname`が必要と
なるかもしれません。
