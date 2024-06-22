---
title: GithubでどのブランチからのコミットでもSlackに通知させる方法
tags:
  - GitHub
  - Slack
private: false
updated_at: '2023-01-23T19:17:01+09:00'
id: 8e9ed6b6fbe9cf76cb38
organization_url_name: orizo
slide: false
ignorePublish: false
---
## はじめに
当記事ではGithubとSlackを連携させ、`main`ブランチのコミットに紐づけて通知を受け取る設定が完了していることを前提としています。

### デフォルトのsubscribeではmainブランチからのコミットでしか通知されない
まずデフォルトのsubscribeでできることは下記の通り
| オプション | 通知されるイベント |
|:-:|:-:|
| issue  |  作成されたまたはクローズした |
|  pulls | 新しく作成されたまたはマージされたプルリク、および「Ready for Review」とマークされた  |
|  commits | `main`ブランチでコミットされた  |
|  release | リリースが公開された  |
|  comment | `issue`とプルリクに関する新しいコメント  |

デフォルトのままでは`main`ブランチからのコミットでしか通知されないのである


### 全てのブランチからのコミットを通知したい時
結論から申し上げるとこれでOK
```sh
/github subscribe owner/repository reviews comments branches commits:*
```
全てのレビュー、コメント、ブランチの作成、コミットが通知されるようになる！！

コマンド実行後にコミットした結果


![スクリーンショット 2023-01-23 19.14.47.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/282722/79a07fa5-817b-3c73-aa68-31bd93ca9410.png)

これで`main`以外のブランチがコミットしたら通知が来るようになった:laughing:

#### 参考
https://mseeeen.msen.jp/subscribe-github-commits-for-all-branches-in-slack/

https://github.com/integrations/slack
