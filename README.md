## リファクタリングした箇所
- Main.java,RedFantasy.javaに存在するfor文をstreamに置き換えた

## オブジェクト指向エキササイズのためのクソコード
- このプロジェクトはプログラミング言語論の演習課題「オブジェクト指向エキササイズ」のためのクソコードである．
- オブジェクト指向エキササイズについては下記参照のこと．下記書籍及びスライドに書かれている9つのエキササイズを実施することが目標．
 - ThoughtWorks Inc. (著), 株式会社オージス総研 オブジェクトの広場編集部 (翻訳), ThoughtWorksアンソロジー ―アジャイルとオブジェクト指向によるソフトウェアイノベーション 単行本（ソフトカバー），オライリー・ジャパン，2008/12/27. https://www.amazon.co.jp/dp/487311389X
 - 大圖衛玄，オブジェクト指向できていますか？, http://www.slideshare.net/MoriharuOhzu/ss-14083300, 2012/8/27.

## クソコード作成指針
何か良いのが思いついたら追加予定
- Collectionとパッケージを使わない
- できる限りクラスを作らない
- 作れるsetter/getterは全部作る
- ネストは深ければ深いほど良い
- 1つのメソッド内でできることを分割しない
- if-else if..は長ければ長い方が良い
- 変数名，メソッド名は適当につける
- 一行に付くドットの数の限界に挑戦したい（クラスを作らないと難しい．．．）
- 同じコードを何回でも書く

## redfantasy仕様
- Main.javaではRedfantasyクラスをnewしたあと，3秒毎にstartPhase()を呼び出し，player/cpuいずれかのHPが0以下になるまで繰り返す．
- playerMonsters/playerMonstersPoint はint型の配列で，モンスターのカード番号とmonsterPointが格納される
  - モンスターのカード番号はMain.javaのsetMonstersメソッドでmonsters配列に格納される配列のindex(0~21)が表す
- startPhase()では，下記の順に処理が行われる
  1. モンスターカードを引き，playerMonsters, playerMonstersPointをセットし，何を引いたかを表示する（CPUも同様）
  1. サイコロを振る．1の場合はモンスターポイントが半分に，6の場合はモンスターポイントが倍になる．それ以外の場合はbonuspointがサイコロの目にセットされる（CPUも同様）
  1. player/cpuの全モンスターのモンスターポイントとbonuspointを合計する
  1. cpu vs player（モンスターポイントの合計で勝負），モンスターポイントの差分を負けた方のHPから引き，HPを表示する
  1. 結果を記録する
