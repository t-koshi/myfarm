# myfarm

## macを使っている場合

はじめに、下記サイトからDocker for Macをインストールしてください。

https://docs.docker.com/docker-for-mac/

## docker-compose を使っている場合

### 環境構築

- サーバー構築
- bundle install
- DB 生成＆マイグレーション
- ホスト側の hosts 設定

#### サーバ構築、 bundle install、 DB 作成
下記のコマンドで、サーバを作成し、Bundle インストール後に DB の生成、マイグレーションを行う

```
$ docker-compose build
$ docker-compose run web bundle install
$ docker-compose run web bundle exec rake db:create db:migrate
```

### 起動確認

サーバを起動する

```
$ docker-compose up
```

サーバが起動したら

http://localhost:3000/

へアクセスして、起動を確認する

### デバッガー（ブレークポイント）を使う場合

`docker-compose up` ではデバッガー（ブレークポイント）を使うことが出来ないので、
`binding.pry` や `beybug` を使いたい場合は次のようにしてください。

```
$ docker-compose run --service-ports web bundle exec rails s -b 0.0.0.0
```

