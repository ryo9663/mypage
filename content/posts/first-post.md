+++
date = '2026-03-07T10:24:12+09:00'
draft = false
title = '１年生を振り返って'
+++

<style>
  /* 1. 親要素のリセット（はみ出し防止） */
  article, .post-content, .nested-copy-line-height {
    max-width: 900px !important;
    padding: 20px !important;
    margin: 0 !important;
  }

  /* 2. テーブル：横幅いっぱい・均等固定 */
  table {
    border-collapse: collapse !important;
    width: 100% !important;
    table-layout: fixed !important;
    margin: 1rem 0 !important;
    border: 2px solid #333 !important;
    overflow-x: auto;
  }

  /* 3. セル：【ここを修正】すべての文字を上下左右中央へ */
  td, th {
    padding: 0 !important;
    border: 1px solid #666 !important;
    height: 80px; /* 高さを少し出すと見やすいです */
    text-align: center !important;   /* 左右中央（通常文字用） */
    vertical-align: middle !important; /* 上下中央 */
  }
/* 4. 出席したコマの枠組み（ベタ塗りをやめる） */
  .attended {
    display: flex !important;
    align-items: center;
    justify-content: center;
    width: 100% !important;
    height: 100% !important;
    margin: 0 !important;
  }

  /* 5. 時間割のリンクすべてを「ぷっくりボタン」にする */
  td a {
    display: flex !important;
    align-items: center;
    justify-content: center;
    width: 85% !important;   /* セルとの間に隙間を作ってボタン感を出す */
    height: 75% !important;  /* 高さを絞る */
    margin: auto !important; /* 中央寄せ */
    border-radius: 8px;      /* 角を丸く */
    background-color: #f8f9fa; /* 出席タグがないコマは薄いグレー */
    border: 1px solid #e0e0e0;
    box-shadow: 0 2px 4px rgba(0,0,0,0.05); /* ほんのり影をつける */
    text-decoration: none !important;
    color: #333 !important;
    font-weight: bold;
    font-size: 0.9rem;
    transition: all 0.2s ease; /* ホバー時の動きを滑らかに */
  }

  /* 6. 出席したコマ（.attended）の中のボタンは黄色くする */
  .attended a {
    background-color: #fff9c4 !important;
    border-color: #ffd54f !important;
  }

  /* 7. マウスを乗せた時（ホバー）の浮き上がる動き */
  td a:hover {
    transform: translateY(-2px); /* 少し上に動く */
    box-shadow: 0 5px 12px rgba(0,0,0,0.1); /* 影を濃くして立体感を出す */
    background-color: #ffe082 !important; /* マウスを乗せたら少し濃い黄色に光る */
  }

  /* 星評価のスタイル設定 */
  .review-table {
    max-width: 500px !important; /* 評価表は少しコンパクトに */
    margin: 20px auto !important;
    font-weight: bold;
  }

  .stars {
    color: #ffca28; /* 黄色（★） */
    font-size: 1.4rem;
    letter-spacing: 4px;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
  }

  .star-gray {
    color: #e0e0e0 !important; /* 灰色（☆） */
    text-shadow: none;
  }

  .review-label {
    background-color: #f5f5f5;
    width: 40%;
  }
  /* 星なし・コメントのみの場合のスタイル */
  .review-comment-only {
    color: #333;
    font-size: 1rem;
    font-weight: normal;
    /* 星がない分、少しだけ目立たせるなら */
    border-left: 3px solid #ffca28; /* 左側に黄色の線を添えるとお洒落 */
    padding-left: 10px;
  }
  html { scroll-behavior: smooth; }

  /* ジャンプ先の見出しが隠れないよう隙間を作る */
  h4 { scroll-margin-top: 80px; }
  /* ======== 目次（INDEX）のスタイル ======== */
  .custom-toc {
    background-color: #fbfbfb;
    border: 1px solid #eeeeee;
    border-radius: 10px;
    padding: 25px;
    margin: 40px 0;
    box-shadow: 0 4px 10px rgba(0,0,0,0.03);
  }

  /* タイトルの装飾 */
  .toc-title-wrapper { text-align: center; }
  .toc-title {
    font-weight: bold;
    font-size: 1.2rem;
    color: #444;
    margin-bottom: 20px;
    letter-spacing: 2px;
    border-bottom: 3px solid #ffca28; /* アクセントの黄色線 */
    display: inline-block;
    padding: 0 10px 5px;
  }

  /* ボタンを横に並べる設定（PCなら2列、スマホなら自動で1列） */
  .custom-toc ul {
    list-style: none !important;
    padding: 0 !important;
    margin: 0 !important;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 12px; /* ボタン同士の隙間 */
  }

  .custom-toc li { margin: 0 !important; }

  /* リンク（ボタン）の見た目 */
  .custom-toc a {
    display: block !important;
    padding: 12px 15px;
    background-color: #ffffff;
    border: 1px solid #e0e0e0;
    border-radius: 6px;
    color: #333 !important;
    text-decoration: none !important;
    font-size: 0.95rem;
    font-weight: bold;
    text-align: center;
    transition: all 0.2s ease;
  }

  /* マウスを乗せた時の動き */
  .custom-toc a:hover {
    background-color: #fff9c4 !important; /* 米田さんの出席色（黄色） */
    border-color: #ffd54f;
    transform: translateY(-3px);
    box-shadow: 0 5px 10px rgba(0,0,0,0.08);
  }

  /* パターンA：蛍光ペン風のマーカー（一番おすすめ） */
  .marker-yellow {
    background: linear-gradient(transparent 60%, #ffe082 40%);
    font-weight: bold;
    padding: 0 2px;
  }

  /* パターンB：赤色の波線・点線（ガチの警告用） */
  .warning-line {
    border-bottom: 2px dashed #e53935; /* 赤い点線 */
    color: #d32f2f; /* 文字も少し赤くする */
    font-weight: bold;
    padding-bottom: 2px;
  }
  /* ======== 成績まとめ・GPAのスタイル ======== */
  .gpa-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 15px;
    margin: 30px 0;
  }

  .gpa-card {
    background-color: #fbfbfb;
    border-left: 5px solid #e0e0e0;
    border-radius: 8px;
    padding: 15px 20px;
    width: 28%;
    min-width: 140px;
    text-align: center;
    box-shadow: 0 3px 6px rgba(0,0,0,0.04);
  }

  /* 総合GPAだけ色を変えて目立たせる */
  .gpa-card.total {
    border-left-color: #ffca28; /* 黄色 */
    background-color: #fffde7;  /* 薄い黄色 */
  }

  .gpa-card h4 {
    margin: 0 0 5px 0 !important;
    color: #666;
    font-size: 0.9rem;
  }

  .gpa-score {
    font-size: 2rem;
    font-weight: 900;
    color: #333;
    font-family: 'Arial Black', sans-serif;
  }

  /* 成績集計表（高さをコンパクトにする） */
  .grade-table {
    max-width: 600px !important;
    margin: 0 auto 40px auto !important;
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
  }

  .grade-table th {
    background-color: #f5f5f5 !important;
    height: 40px !important; /* 全体設定の80pxを上書き */
    font-size: 0.9rem;
  }

  .grade-table td {
    height: 40px !important; /* 全体設定の80pxを上書き */
    font-size: 1rem;
  }

  /* 合計の行を少し目立たせる */
  .grade-table .total-row td {
    font-weight: bold;
    background-color: #fafafa !important;
  }
</style>

２０２５年度入学の(りょう)^2です. 無事先日１年の科目の成績が帰ってきたのでレビューを書きました. 他の方がやっているように自分のサイトにも憧れていたので作ってみました. ここでは各科目を受けて自分の感じたことなどまとめます.

<span class="warning-line">あくまで個人の感想です. 過去問, レポの配布とかはないのでご了承ください.</span>

<div class="custom-toc">
  <div class="toc-title-wrapper">
    <div class="toc-title">目次</div>
  </div>
  <ul>
    <li><a href="#pro">自己紹介</a></li>
    <li><a href="#前期">前期</a></li>
    <li><a href="#後期">後期</a></li>
    <li><a href="#sum">全体を通して</a></li>
    <li><a href="#gpa">成績</a></li>
    </ul>
</div>

## 自己紹介 {#pro}

改めまして(りょう)^2です. １類２クラでBクラスになります. 最近めっきりベースにハマっている人です, 軽音系(器楽, シンセ, 軽音)によくいますのでよろしくお願いします.

<span class="marker-yellow">ここでは簡単な自己紹介および自語りをします. 興味ない人は飛ばすのを推奨します.</span>

まずサークルは軽音系です, 夏休みの前くらいに友人たちに誘われて始めてどハマりしました.


得意科目は数学の主に微積とかそっちの方です. 物理とか化学も好きですね. ~~なぜ1類にきたんでしょうか~~

パソコン触るのは昔から好きでしたがプログラミング経験はほぼ０です. 高校の時にちょっとだけ触ったことあるくらいで本当に何も分からない状態で入学しました.(ターミナルってなんですか状態)

後期入学で高校でも受験勉強ばっかやってたので本当にペーパーが得意みたいな人で, 前期には大学の勉強とのギャップになかなか苦しみました(なんなら今も).

バイトは4月から週２で塾バイトをやっています, ４時間*２ですし肉体労働はほぼないので体力的には楽ですが, 時間外の対応や曜日が固定されてたりしたのが大変でした.

実家が大学から30分くらいなので結構近めだと思います.

ざっくりこんな感じの状態で１年を過ごしました. 一人暮らしの人とかいると思います. 正直バイトとサークルと大学の課題とでいっぱいいっぱいだったので家事とか入ると本当に大変だなと思います. バイトは長期休みに単発で入るとかがいいんじゃないかなと思います.

以下では各科目の詳細?なレビューをします.
## 前期 {#前期}
海外の推薦のため3.5を目指そうと思ってめっちゃ成績のための勉強してました. 途中で楽器初めて楽しくなって若干右肩下がり.
### 時間割
出席があったものは色をつけています.
| 時限 | 月 | 火 | 水 | 木 | 金 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | | | <span class="attended">[微積第一](#w1f)</span> | | <span class="attended">[AWE](#f1f)</span> |
| **2** | <span class="attended">[必中](#m2f)</span> | <span class="attended">[ASE](#tu2f)</span> | | <span class="attended">[選中](#th2f)</span> | [化概第一](#f2f) |
| **3** |  <span class="attended">[健康論](#m3f)</span>|  <span class="attended">[コンリテ](#tu3f)</span>|  <span class="attended">[数演第一](#w3f)</span>| [線形第一](#th3f)|  <span class="attended">[えっけん(春)](#f3f)</span>|
| **4** | |  <span class="attended">[物概第一](#tu4f)</span>| | |  <span class="attended">[びっけん(夏)](#f4f)</span>|

#### 月2 必修中国語(nkmr先生) 秀{#m2f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
おそらく必修中国語の中ではかなり楽です. 課題はありますがすぐ終わるのでほぼないようなものです. 単語テストもあるんですが成績に入らないらしいです. (後のために真面目に勉強することはおすすめします)

出席はありますが授業の終わりなので多少の遅刻は問題ないです. (流石に終わり際は目をつけられる?)

テストで意味や並び替えを答える問題文は事前に伝えられるのでテスト自体はそこまでしんどくなかったです.

後述する選択中国語のおかげで理解は進みました. 必修だけでこの先生だと少し大変かもです. 好成績狙いの人は中国語に関しては選択をとることをお勧めします. 単位取得のみを目標にする人は正直好みです.

好成績狙いのアドバイスとしてはとにかく真面目に最前で受けることです. とにかく中国語を真面目に勉強して色々質問して名前を覚えもらえればいい成績もらえるんじゃないかな. ~~媚びろというわけではないです~~

体感テストは前期9割, 後期7-8割ほどでした. 前期は比較的に簡単, 後期は前期の倍以上難しいと感じました.
#### 月3 健康論 秀{#m3f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars"><span class="star-gray">★★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">授業内レポート</span>
  </td>
    </tr>
  </tbody>
</table>

特に言うことはないです. 出席して座学のときのレポートを裏面までちゃんと埋めれば秀きます.内容もですが文量が大事です.
#### 火2 Academic Spoken English(Mr skpj) 優{#tu2f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内ワーク&プレゼン</span>
  </td>
    </tr>
  </tbody>
</table>
初めに満足度が高いのは, 僕が留学したいので実践的な英語を身につけたいと考えているからです. そうでない人にとってはかなりしんどいというかめんどいと思います.

基本的にプレゼン準備→プレゼンという流れをずっとやります. 原稿考えてプレゼン資料を作るのが割と大変でした. 単位取得難易度はわからないんですがプレゼンを無難にこなせば単位は来ると思います. 逆に休みすぎるとやばいかも.

好成績を狙うにはプレゼンで頑張るしかないです.
プレゼン資料を凝り, 原稿を全て覚え, 他の学生の発表後に質問をするという3つです.
僕は前期で3-4回くらいあったブレゼンでファイナルプレゼンだけ全部覚えました. あと何回か質問しました.

とにかくアクティブに授業に参加することをおすすめします, いい先生で拙い英語でも汲み取って言い換えてくれたりするのでどんどん話すといいことがあります. 実践が多いので単純に勉強になりました.
#### 火3 コンピュータリテラシー(tkg 先生) 優 {#tu3f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
前述した通りプログラミングさっぱりだったのでちょっと大変でした. 後述の基礎プロも同じ感じです. 経験者に頼りましょう.

まず基本的に課題は4点中3点が普通とされてます. 僕みたいな人は3狙いでいいと思います. 本当はちゃんと内容を理解してやった方が良かったのでしょうが半分くらい忘れてます.

 テストは教科書が見れるので, 単位が来る程度の点数は取れると思います. 学習の確認問題を頑張ってやるといいです.
#### 火4 物理学概論第一(mmr先生) 優 {#tu4f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">テスト</span>
  </td>
    </tr>
  </tbody>
</table>
物理や微積が好きなので満足度は高め, 人によっては苦痛です. 出席は時間内にフォーム的なの出せば終わりなので実質出席なしです.

この先生は流体力学の先生でかなり授業の雰囲気は良かったです. 回収できなかった質問にはちゃんと次の回に解決してくれるのでやる気ある人にはちゃんと応えてくれる方でした.

評価に関しては全クラス共通のテストです. まず高校物理で微積分をちゃんと使った物理をやってきた人は簡単, 逆にそうでない人には若干きついかもしれない. そういう意味で単位取得難易度は人によります. また試験問題は割と公式の過去問通りで差がつかないので2-3ミスで全然秀から落ちるとかあります, 僕のことです. 問題文はちゃんと読みましょう.
#### 水1 微分積分学第一(hg先生) 秀 {#w1f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">テスト</span>
  </td>
    </tr>
  </tbody>
</table>
出席は1秒でも遅れたらアウトです, 1限だったので大変でした. 豪雨で遅延したときは終わったと思いましたが流石にそのときは大丈夫でした.

授業は文字小さすぎて後ろの方だったので何も見えなかったので全然聞いてなかったです, ごめんなさい. ただ配布される資料がかなり分かりやすく, また証明方法も綺麗ですごい勉強になりました.

試験は計算で答えのみなのでかなり大変. 量も多いです. 自分はかなり計算が早い方で, やった内容は高校の時に少し知ってた内容だったので本当にギリギリ終わりましたが, 苦手な人は部分点狙いでいいと思います. 思ったよりできなくても単位はくるらしいです.

好成績取りたい人は非公式の過去問からほぼ同じ問題が出るらしいので覚えれば簡単に高得点取れます. 僕は過去問なしで中間期末どっちも81%で秀でした, 本当は満点とか取りたかったんですけど秀が取れたんで安心でした. 9割以上が秀とはされてますが平均が低いので秀ラインも下がったのでしょう.

数演にもつながる科目なので真面目に勉強することをお勧めします. 課題結構多いけど力になります.
#### 水3 数学演習第一(enmt先生) 秀 {#w3f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">テスト</span>
  </td>
    </tr>
  </tbody>
</table>
後期で化けますが正直前期は試験で計算ミスしないかゲーですので気をつけましょうしか言えないです. 微積はかなり演習メインだったこと, 線形代数は前期は行列の基本演算しかないので単位は比較的簡単に取れるはずです. 計算ミスしないようにしましょう.

#### 木2 選択中国語(ri先生)　優{#th2f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
必修が進度遅いせいで選択が初学でしたがかなり分かりやすく, ネイティブなので発音練習が多くかなり力になりました. 予習はした方がいいけど授業内で頑張ればしなくてもついていける, ただやばいと感じたらちょっとは復讐とかするといいかなくらい.

特にしんどいことはないです. 強いて言うなら出席があるので気をつけましょうくらい. テストは直前回に模擬テスト的なプリント演習で出た問題と似た問題があるので単位をとる分にはしんどくない, 逆に差がつきづらいので少しのミスが秀には命取りかと思います.

#### 木3 線形代数学第一(rkn先生) 優{#th3f}

<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★<span class="star-gray">★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">課題 & テスト</span>

  </td>
    </tr>
  </tbody>
</table>
当たりです. めちゃくちゃ数学の背景から話してくれます. 教科書の読み方や考え方を学べるのでかなりありがたかったです. 欲を言えば後期の写像ら辺の講義を聞きたかった. テストは昔は証明だったりしたが, 出来が悪過ぎて穴埋めの簡単問題になったとのこと. 実際難易度はそんなに高くなく計算ミスが命取りなので注意しましょう. 過去問あるらしいけど初見で十分解ける程度なので本当に計算ミスを気を付けよう後期だと過去問から9割同じ問題出たらしいので過去問あるなら頼ってもいいとは思います.

線形代数で出てくる考え方はいろんなとこで役に立ってるのでぜひ個人的にも勉強してみるのをお勧めします.

#### 金1 Academic Written English(Mr Mcrl) 良 {#f1f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & 課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
通称 枕, レランなのにラーレンって呼んでる人みて吹き出しました.
英語が苦手すぎて前期はえっけんより辛かったし後期の共鳴の次にやばかった.

まず毎週やばい量の英作と毎月平均1万語くらいのリーディング課題と授業内で出たブリント課題をやる. コピペでやるとバレるのでAI使用者が途中で刺されました. みんなバレないように使っていたけどどうせ将来英語使うしバカ真面目に英語の勉強した方がいいです, 実際将来に向けて考えてくれている先生なので真面目に受けるだけだんだん楽になると思います. AI使った方がむしろ大変かも.

授業内でエッセイ書かされたりするから頑張って食らいつこう, いい先生ではあるし授業は結構いいことやってるけど課題の内容と違い過ぎてまず課題で何やるのかから考えないといけないのが大変. ~~てかえっけんに被せんな, 金曜1限にすんな.~~
でも最終課題の提出場所ミスったけど評価してくれてありがとう.

英語以外の科目だけど何か伸ばしたいって人には神だと思います.


#### 金2 化学概論第一(isd先生) 秀 {#f2f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
化学が好きなため満足度が高かったです.

出席はなく授業内容はそこそこ難しいですがテストに関係ないため正直行かなくても単位は取れます. 課題はありますがAIに食わせればいいので本当に行かなくてもいいと思います.

ただ個人的にこの先生は面白くて(軌道など高校でやってたら)分かりやすいので当たりだと思います.

 テストは物概や数演と同じでミスの無いように気をつけましょう.

なお個人的に作成したテスト対策用のpdfがあるので良ければ参考程度にしてください.
https://x.com/ryoKmath/status/1951412718109598185?s=20

#### 金曜3,4(春) 基礎科学実験A 優 {#f3f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★<span class="star-gray">★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">レポート</span>
  </td>
    </tr>
  </tbody>
</table>

他の人たちも色々悪い噂を言ってますが大体あってます.私は振子, ヤング率, 光電効果で比較的楽な方でした.

パワポで図を作成するのは思ったより時間がかかるので土日の内に終わらせることをお勧めします. あとLaTeXの環境構築はなるべく初回までにはすることがいいです.

他の科目(主にASE, AWE)のしんどい時期と被ると地獄です. 単体ではそれほどしんどくないんですが重なるのですごい大変というのがえっけんのしんどさの原因かなと思います.

秀狙いの人は過去レポだったり頼るのがいいのかなと, 僕はなかったです, ただ図や考察は丁寧に頑張れたので優はきました, とにかく実験値の誤差の要因を定量的に評価するのが大事だなという印象でした.

バイトが水木だったので疲労で生きた心地がしなかったです. これを乗り切った後, かなり精神力がついた気がします()

#### 金曜3,4(夏) 基礎科学実験B 優 {#f4f}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★<span class="star-gray">★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">レポート</span>
  </td>
    </tr>
  </tbody>
</table>
雑魚いえっけんです. えっけん後だったので書き方は迷わずえっけんよりは楽でした. ただ毎週あるのと手書きだったのでそこが苦しかったです.

 また字は小さく書きましょう. 前のタームでびっけんだった友達とえっけんのレポを交換してなんとなく雰囲気をつかんでました.

前期は特に言うことがないです. めちゃくちゃ書いてそれっぽい考察すれば優くらいは狙えると思います. 秀は過去レポでも見てればいいと思います.
SABCAで優でした.

<div style="text-align: right; font-size: 0.9rem; margin-top: 10px;">
  <a href="#前期">↑ 前期の時間割に戻る</a>
</div>

## 後期
この辺から時間ある時は楽器弾くようになって明らかに成績が落ちました.
### 時間割
出席があったものは色をつけています.

| 時限 | 月 | 火 | 水 | 木 | 金 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | [離散](#m1b) | | <span class="attended">[JRE](#w1b)</span> | | <span class="attended">[AWE](#f1b)</span> |
| **2** | <span class="attended">[必中](#m2b)</span> | <span class="attended">[ASE](#tu2b)</span> | | <span class="attended">[選中](#th2b)</span> | [微積第二](#f2b) |
| **3** |  <span class="attended">[体づくり](#m3b)</span>| | | [線形第二](#th3b)|  <span class="attended">[えっけん(秋)](#f3b)</span>|
| **4** | | [解析](#tu4b) | <span class="attended">[数演第二](#w4b)</span> | <span class="attended">[基礎プロ](#th4b)</span> |  <span class="attended">[びっけん(冬)](#f4b)</span>|
#### 月1 離散数学 (tkhs先生) 良{#m1b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars"><span class="star-gray">★★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">テスト</span>
  </td>
    </tr>
  </tbody>
</table>
一回しか行ってないですごめんなさい.
この成績は不甲斐ないです, 真面目に勉強しましょう.

基本的に共有されるスライドが分かりやすいのでそれで勉強すればいいと思います. テストは任意課題(演習用)を解ければ単位は来るほど難しくはないです. 過去問から似た問題が出たらしいので持ってる人は使うといいと思います.

解説も分かりやすいのでテスト勉強めんどくさい人は絶対授業行った方がいいです.

なおおそらく評価基準に厳密な方だと思うので秀を狙う方はしっかり勉強しましょう. また授業(スライド内)で解説していた方法使って解くといいでしょう.
#### 月2 必修中国語(nkmr先生) 秀 {#m2b}
前期と同じです. テストは若干難しくなるので注意.
#### 月3 健康・体づくり実習 秀
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★<span class="star-gray">★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内テスト & レポート</span>
  </td>
    </tr>
  </tbody>
</table>

４つのスポーツの中から選択してやります. 実技点は雀の涙程度で, 毎授業内の振り返りレポート的なのの記述量や内容で評価されます.


#### 火2 Academic Spoken English(Mr skpj)　良 {#tu2b}
前期と同じです. みなさんはちゃんと出席しましょう.
#### 火4 解析学(itu 先生) 優 {#tu4b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">テスト</span>
  </td>
    </tr>
  </tbody>
</table>
一回しか行ってないです, ごめんなさい.

離散同様スライド資料が優秀だったり公式が過去問を配布しているのでほぼ過去問対策してれば単位はきます.

また単位が危うい学生にはテスト前に全員やるレポート課題(いくつか問題を解く課題)を評価に入れるので落単率は比較的低いのかと思います. ただ普通にテストは簡単ではないです. 計算量が多いので計算ミスは気をつけましょう.

67点, 90点で優が来ました. 秀は目指しやすいはずです.

#### 水1 情報領域演習 優 {#w1b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　レポート課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
基礎プロの演習のP演習, 離散数学の演習のD演習の二つで構成されています.

BクラスではP演習は出席あり, D演習は出席なしです.

また主な課題はD演習のレポート(少ししかない)です.

P演習は正直プログラムを提出するだけなのでAI使いながらやれば誰でもできます. D演習は割とテストが難しいので別途配布されている演習問題を解けるようにしましょう, そうすればほとんど単位は取れます. 課題が一回でも提出できなかったりミスしたら落単なのでそこだけ気をつけてください.
#### 水4 数学演習第二(enmt先生) 優 {#w4b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>

難易度はそこそこ高いのかと思います. ３回欠席してしまって下がってしまい勿体無いことをした気がする. 期末は細かい点数出てないですが平均は低そうでした.

中間期末で14,15でそれぞれ平均が10点くらいなんじゃないかな. ちゃんと勉強すれば全然9割とか取れますので安心してください. 他科目より先にあったりライブ後だったりでちゃんと勉強できなかったです. 直前になると頭のいい人たちが色々教えてくれるので助けてもらうといいと思います.

僕は授業は大体行っててそこで内容を頑張って理解しようとしたので一夜漬けでもなんとかなりましたが結構きつかったので不安な人は事前に頑張りましょう.

#### 木2 選択中国語(ri先生) 優 {#th2b}
前期とほぼ同じです, 内容が難しく, また多くなるので頑張りましょう.

#### 木3 線形代数学第二(mys先生) 優 {#th3b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★<span class="star-gray">★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
最初以外行ってないです, 授業は基本的に教科書の解説で写経を一緒にやる感じです. 普通です. 証明を追ったことなかったり何勉強すればいいかわからない人にとっても優しいんじゃないかなと思います.

テストはひたすら計算です. 中間と期末でそれぞれ1章ずつ出ますが基本的に章末問題を解けば大丈夫です. ただ今年は期末で過去問の数字入れ替えて作って計算できない問題が出てきたのでこういうことも想定して, 時間配分に気をつけたりや解けるところを見つけて解くのを心がけましょう. 証明はほぼ出ないので計算方法だけ身につけても単位は来るんじゃないでしょうか.
#### 木4 基礎プログラミングおよび演習(kniw) 優 {tn4b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★<span class="star-gray">★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★★<span class="star-gray"></span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>
前半にRuby, 後半にCをやります. 全くわかんない状態から多少できるようになったので僕みたいにあまりやってこなかった人は結構頑張るといいと思います. 周りの経験者に聞きまくってました. 前述のP演習でも触るのでレポート課題を頑張ればいいと思います.

反面テストはほとんど学習の確認問題みたいなのが出るのでそれやれば誰でもある程度できると思います. 慣れてる人は勉強しなくてもいけてた記憶があります.


#### 金1 Academic Written EnglishⅡ(Mr Mcrl) 秀 {#f1b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & 課題</span>
  </td>
    </tr>
  </tbody>
</table>

基本的には前期と同じ, AIを使う人が多いからクラス内ワークを増やしてました. なので前期よりも宿題は減ったので前期より楽でした. 英語の表現とか英作文の典型フレーズをエッセイ書きながら勉強したので, 最後の方の授業でクラス内でミニエッセイ書かされるんですがそれも結構できた記憶があります. エッセイのアウトライン書くときに出した英文に使われているフレーズを覚えるだけでも相当変わるのでコツコツ頑張りましょう.

#### 金2 微積分学第二(amn先生) 優 {#f2b}
<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars"><span class="star-gray">★★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　授業内課題 & テスト</span>
  </td>
    </tr>
  </tbody>
</table>

多分全ての人にとって当たりな先生だと思います. テストのみでそれも結構簡単です. 高得点勝負になるから秀は頑張って, 中間試験は数演より簡単な気がします. 期末も結局重積分しか出なかったので数演を頑張りましょう.

授業の内容は位相の話から始まってだいぶレベルの高いことをやってくれます. えっけんやびっけんがなかったらちゃんと受けたかった. 最初の2回くらいしか出れませんでしたごめんなさい.
#### 金曜3,4(秋) 基礎科学実験A 良 {#f3b}

基本は不確かさが生えてきただけで前期と同じ, 書き方は思い出しときましょう. 不確かさも予習のやつでやりますし, 教科書にも乗ってるので実は意外とそんなでもなかったです, 予習しとくとだいぶ考察が楽できるんじゃないかなと思います.

重力加速度, 共鳴, エアトラでした. 共鳴がやばいです.みなさんは気をつけてください. エアトラはレポート自体はそんなにしんどくないので実験の予習をすればいいと思います.
#### 金曜3,4(冬) 基礎科学実験B 優 {#f4b}

<table class="review-table">
  <tbody>
    <tr>
      <td class="review-label">満足度</td>
      <td class="stars">★<span class="star-gray">★★★★</span></td>
    </tr>
    <tr>
      <td class="review-label">単位取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">好成績取得難易度</td>
      <td class="stars">★★★<span class="star-gray">★★</span></td>
    </tr>
    <tr>
      <td class="review-label">課題量</td>
      <td class="stars">★★★★<span class="star-gray">★</span></td>
    </tr>
    <tr>
      <td class="review-label">評価方法</td>
        <td class="stars">
        <span class="review-comment-only">　レポート</span>
  </td>
    </tr>
  </tbody>
</table>

手書き版のえっけんと言われていて, 毎週だからえっけんよりやばいとは言われてます.しかし, 確かに手書きめんどくさいなと思うところはありますが, 意外とすぐ終わりますし, 考察も基本的には定性的なことなのでシンプルです. 共鳴を乗り越えた状態だったので辛くはなかったです. コツコツやれば大丈夫, ただ一夜漬けで終わるかはクオリティとその人次第かなと思います. 僕は終わんないので実験あった日のうちにちょっとは手をつけてました.

これも前期同様に先にびっけんだった友達を頼りながらやってました. ありがとうございました. 前期に比べて自由に書ける分好成績は若干取りやすいんじゃないかなと思いました.
AABBAで優でした.

<div style="text-align: right; font-size: 0.9rem; margin-top: 10px;">
  <a href="#後期">↑ 後期の時間割に戻る</a>
</div>

## 全体通して {#sum}
個人的にはかなり充実した一年でした. 前期の途中から音楽を始めて後期には結構ライブに出たりなど途中から勉強が若干疎かになっていたんですがなんとか粘って頑張れたんじゃないかなと思います.
前期は本当に寝れなくて正直辛かったです. 受験より忙しかった気がします. 後期はうまく手を抜きながらできたのかなという印象です.

ペーパーだったり成績のための勉強をそこそこやった人間のレビューになりますので参考までに, 成績のための勉強だけでなく興味を持った分野の勉強とかもやっていきたいなと思いました. これを見ている人にはバランスよく生きてほしいなと思います()

 改めてバイトとサークルと勉強の掛け持ちはかなりしんどかったのであまりおすすめはできないですね. 塾バイトで英語の復習したりしてたので英語はなんとかなったんですが, 飲食とかだったら本当に大変なことになってました.

レビューの文量みて分かる通り後期はあんまり行ってなかったです. 先生によって出席の有無は変わりますが僕たちのクラスは後期は言われてるほど大変ではなかった印象です.
今後は目標の３.５を目指しつつGLTPに向けてTOEIC対策をしたいです.

最後に各学期の成績を簡単にまとめて終わります. ここまでありがとうございました.

## 成績 {#gpa}

<div class="gpa-container">
  <div class="gpa-card">
    <h4>前期 GPA</h4>
    <div class="gpa-score">3.31</div>
  </div>
  <div class="gpa-card">
    <h4>後期 GPA</h4>
    <div class="gpa-score">2.94</div>
  </div>
  <div class="gpa-card total">
    <h4>総合 GPA</h4>
    <div class="gpa-score">3.14</div>
  </div>
</div>

<table class="grade-table">
  <thead>
    <tr>
      <th>学期</th>
      <th>秀 </th>
      <th>優 </th>
      <th>良 </th>
      <th>可 </th>
      <th>不可 </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>前期</td>
      <td>5</td>
      <td>7</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>後期</td>
      <td>3</td>
      <td>8</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>

<a href="#" class="back-to-top-btn">
  先頭へ
  </a>
</div>
