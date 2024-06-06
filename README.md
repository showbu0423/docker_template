# 環境構築方法
##  前提
作業用フォルダを作成し、フォルダ内に移動する。

## 環境構築ファイル（dockerファイル）をクローン
```
git clone git@github.com:showbu0423/docker_template.git .
```

## docker環境をビルド
`docker-compose.yml`の存在する階層でビルドする
```
docker compose up -d
```

## Docker環境にlaravelをインストールする
Dockerコンテナに移動
```
docker exec -ti "作成したdockerのapp名"-app-1 bash

composer create-project laravel/laravel .
```

## docker環境をいじる
`.env`ファイルの作成
```
cp .env.example .env
```

`.env` の`APP_KEY`に値を入れる為、`/var/www/html`の階層でlaravelコマンドを実行する
```
php artisan key:generate
```

Laravelの認証システムをインストールする
```
composer require laravel/breeze --dev
php artisan breeze:install blade
```

## php artisan migrate実行時のエラー
### SQLSTATE[HY000] [1044] Access denied for user 'admin'@'%' to database　　のエラーが発生した場合
phpmyadmonの `サーバ： db/ユーザアカウント`から`admin`を選択して`グローバル権限  すべてチェックする`をチェックして実行する
その後`php artisan migrate`を再度実行するとうまくいく


## アクセス
アプリ画面
```
http://localhost:8080
```

phpmyadmin
```
http://localhost:8081
```

phpmyadmin
```
http://localhost:8025
```
