# docker練習

本半分くらいまで読んだけど、push稼ぎのために復習がてら最初からやります

## 二章復習メモ

`docker (container) run -d` めちゃつかうバックグラウンド実行

dockerのポートフォワーディング

`docker (container) run -p {ホスト側ポート}:{コンテナポート}`

### image操作

`docker image build -t example/echo:latest .` 基本

`docker image --pull=true -t example/echo:latest .`
ローカルにベースイメージが存在している場合dockerは差分でビルドするので、最新のベースイメージを取得してからイメージをビルドしたいときに使うぴょん

`docker search [options] 検索キーワード` docker hub使うなら必須

`docker image pull` イメージの取得

`docker image ls` 実は`docker images`でいけるの気づいた

`docker image tag example/echo:latest example/echo:0.1.0

`docker image push [options] リボジトリ名[:tag]`

例`docker image tag exampl/echo:latest userID/echo:latest`の後`dokcer image push userID/echo:latest`でpushできるぴょん

### container操作

`docker ps --filter "ancester=example/echo"とか`docker ps --filter "name=echo1"とかでフィルターできる

`docoker ps -a`終了したやつも含め全部表示

`docker stop`コンテナを停止

`docker container restart`コンテナの再起動

`docker exec -it echo sh`echoコンテナをshで実行できるようになる

### 管理者コマンド

`docker (image contanienr) prune`停止したイメージ、コンテナを全て削除してくれる

`docker system prune`コンテナイメージボリュームネットワークの全てのリソースを削除

`docker contaner stats`  docker上で UNIX系OSの`top` コマンドをしているようなもの

### docker-composeでマルチコンテナ操作

`docker-compose up -d` docker-compose.yamlを読み込んで実行してくれる

`docker-compose down`yamlに書いてるコンテナを停止する

