# Pyxel 三国志とは

レトロゲームエンジン [Pyxel](https://github.com/kitao/pyxel) で制作した、三国志を題材にした 8 ビット風の戦略シミュレーションゲームです。iOS および Android でプレイいただけます。

ゲーム制作：frenchbread（@frenchbread1222）
タイトル画像：エリむーと（@Emt_mezzo）様

アプリ本体に簡単なガイドをつけているので、このドキュメントではゲームについて詳しく知りたくなった方のための細かい情報を記します。

## プレイ方法

（後で追記）

## ゲームの世界観について

三国志を題材としたゲームは、小説「三国志演義」のストーリーやキャラ設定をベースにしたものが多いですが、本作は演義ではなく正史ベースです。そのため、たとえば周倉のような演義オリジナルキャラは登場しないのと、劉備・趙雲・周瑜・魯粛など三国志演義でキャラクタが極端に特徴づけられている武将については、武将の評価が演義ベースのゲームと大きく異なっていることが多いのでご注意ください。

また、本作は登場する都市数が少ないのとバランス調整の都合で、シナリオ開始時の設定やイベントなどが正史とも演義とも違っていたり、不自然な設定になっている点があります。顕著なのはシナリオ「劉備入蜀」で、劉備の初期領土が江陵と江夏で飛び地になっています。またゲーム進行状況によってはイベントにより予想外の出来事が発生したりしますが、バランス調整の観点であえてそのような仕様にしているものとご理解ください。

## 勢力と都市のステータス

| パラメータ名 | 単位 | パラメータの意味                                                                                                       |
| ------------ | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| 兵士         | 都市 | 戦争時、兵力がなくなると都市が占領されます                                                                             |
| 訓練         | 都市 | 戦争時の攻撃力・防御力に影響します                                                                                     |
| 武装度       | 勢力 | 戦争時の攻撃力に大きく影響します                                                                                       |
| 戦力         | 勢力 | 兵士の数と強さ（訓練と武装度）を総合的に評価した値（参考数値）です                                                     |
| 金           | 勢力 | 勢力の保有財力であり、兵糧の概念も含みます。ほぼ全てのコマンドで消費し、金（兵糧）が不足すると守備戦で兵士が脱走します |
| 収益         | 勢力 | 全ての都市の収益を合算し、武将の俸禄や兵の維持費を減算した数値で、この数値の分だけ、毎月金が増加します                 |
| 都市の価値   | 都市 | 収益の基本値です。治安が 100 になるとこの数値がそのまま都市の収入になります                                            |
| 治安         | 都市 | 都市の収益に影響します。また低いと住民が反乱を起こしたり、兵が雇えなくなったり、都市の武将が離反しやすくなったりします |
| 治水         | 都市 | 洪水の対策状況を示します。低いほど洪水被害が甚大になります                                                             |
| 防御         | 都市 | 都市の城塞の強さで、籠城戦のときの防御力に影響します。また、異民族や賊徒襲撃時の被害も抑えることができます             |

## 武将の能力・特性

### 階級（C〜S の４段階）

- 階級Sのみ、君主死亡時に後継者になれます（他に親族武将がいない場合のみ）
- 高いほど主君を裏切りにくくなります。特に階級 S になると謀反を絶対に起こしません
- 高いほど提案の発言力が増します
- 高いほど戦争時に兵力を割り当てられます
- 高いほど優先して太守に任命されます

### 武勇（標準〜＋２の３段階）

- 訓練・城壁破壊の発動率や効果、兵雇用時の訓練度に影響します
- 戦闘時の攻撃力に影響します
- 高いほど敗戦・壊滅時に捕縛されにくくなります
- （太守の場合）異民族・賊徒襲撃時の防御力に影響します

### 統率（標準〜＋２の３段階）

- 訓練・改修の効果に影響します
- 戦闘時の攻撃力・防御力・計略回避率に影響します
- （太守の場合）異民族・賊徒襲撃時の防御力に影響します

### 知略（標準〜＋２の３段階）

- 各種計略・引き抜き・改修・治水のの発動率や効果に影響します
- 戦闘時の計略発動率・計略回避率に影響します
- （太守の場合）異民族・賊徒襲撃時の防御力に影響します

### 野心（標準〜＋２の３段階）

- 高いほど裏切りやすく、また旗揚げや独立をしやすくなります
- 高いほど敗戦・壊滅時の捕縛・戦死を回避しやすくなります
- 高いほど提案の発言力が増します
- 高いほど進軍・雇用・武器購入・流言コマンドを好みます
- （君主の場合）高いと自身が前線に出ることを好みます

### 名士

- 巡察・改修の効果に影響します
- コマンド「徳政令」を提案できます（名士・学識・王佐の才のいずれか）
- 在野にいる他の名士を採用しやすくなります
- （太守の場合）毎月の治安回復率が大きくなります

### カリスマ

- 多くの武将（特に能力値が高い武将）に好意を抱かれます

### 学識が深い

- 城壁破壊・改修・治水の効果に影響します
- コマンド「徳政令」を提案できます（名士・学識・王佐の才のいずれか）

### 王佐の才

- 主君を裏切りにくいです
- 提案の発言力が増します
- コマンド「徳政令」を提案できます（名士・学識・王佐の才のいずれか）

### 交渉が得意

- 異民族襲撃・在野登用・停戦や同盟締結・引き抜きの発動率に影響します
- 武器を安く買うことができます

### 逆境に強い

- 戦争時、被害を受けるほど防御力が上がります
- 戦死を回避しやすくなります

### 冷静沈着

- 離反（独立）する確率が低いです
- 治水の効果に影響します
- 改修・停戦コマンドを好みます
- 戦争時の策略回避率に影響します

### 愛嬌がある

- 多くの武将からの好感度が上がります
- （太守の場合）毎月の治安回復率が大きくなります

### 大胆不敵

- 訓練の効果に影響します
- 進軍コマンドを好みます
- 戦争時の攻撃力に影響します。また、標的に選ばれやすくなります
- （君主の場合）攻撃的な方針を優先し、また、自身が前線に出ることを好みます

### 小心者

- 離反（独立）する確率が低く、また自身では旗揚げしません
- 訓練の効果に影響します（負の影響）
- 撤退・治水のコマンドを好み、進軍コマンドを好みません
- 戦争時の攻撃力に影響します（負の影響）。また、標的に選ばれにくくなります
- （太守の場合）守備戦で籠城を選択しやすく、自身が迎撃に出ることを避けます
- （君主の場合）守備的な方針を優先します

### 立派な風格

- 巡察の効果に影響します
- 多くの武将からの好感度が上がります

### 風采が上がらない

- 多くの武将からの好感度が下がります

### 剛直の士

- 主君を裏切りにくいです
- 訓練の効果・兵雇用時の訓練度に影響します
- 訓練コマンドを好みます
- 撤退コマンドを絶対に提案しません

### 優柔不断

- 離反（独立）・旗揚げをしません
- 訓練の効果・兵雇用時の訓練度に影響します（負の影響）
- 進軍コマンドを好みません
- 提案の発言力が下がります
- （太守の場合）自身が迎撃に出ることを避けます
- （君主の場合）守備的な方針を優先します。また、援軍派遣に消極的です

### マスクデータ（非表示の能力・特性）

上記のほかにも、ゲーム上表示されない武将の特性が存在します。たとえば「義理がたい」「利己的」「傲慢」などです。これらは表示される能力・特性と同様、提案の優先度や後述の武将どうしの相性などに影響します。

### 武将どうしの相性

武将間には好悪の感情が存在します。これもゲーム内で直接知ることはできませんが、基本的には同じ特性をもっている武将どうしの相性は良いです。また、「カリスマ」をもつ武将は多くの武将に好かれるが「小心者」には嫌われるといった、一方向的な好悪関係も存在します。

## イベント

### 武将の縁故加入と在野の士官

- 勢力に属する武将の血縁武将は、成人済みで他の勢力に属していなければ自勢力に自主的に士官します（例外あり）。
- また、それ以外にも在野武将が自主的に士官してくる場合があります。

### 武将の病死

- 武将は概ね史実で死亡した年以降になると病死します。長く生き残る場合もあります。
- 史実で戦死したり処刑されている武将（不自然死した武将）は、たいていの場合史実で死亡した年代より後まで生き残ります。

### 洪水

- 毎年 6〜9 月にランダムで発生します。金と治安が減少するほか、治水状態が悪いと兵力も失われます。
- 治水状態が 90 以上の場合、逆に住民に感謝され治安が上昇します。

### 住民反乱

- 治安が 50 未満の都市に対してランダムで発生します。
- 多額の金の支払いが要求されます。金がない場合は武力鎮圧となり、兵力を失います。

### 異民族襲撃

- 異民族襲撃は基本的には計略により発生しますが、大勢力に対してのみ、異民族が自主的に襲撃してくる場合があります。
- 都市の兵力・防御・治安が失われ、最悪の場合都市が占領されてしまいます。

### 賊徒襲撃

- 治安および防御が一定以下の都市に対して発生することがあります。
- 効果は異民族襲撃と同じですが、異民族襲撃に比べれば威力はかなり小さいです。

### その他の特殊イベント

- ゲーム内の状況によって、歴史イベントが発生する場合があります。あまり数は多くなく、通常にプレイしていると発生するものがほとんどです。

## FAQ

### 思い通りのコマンドが提案されない（全体的に）

- 金が不足する場合はコマンドが提案されません。一見金があるようでも、勢力の兵力を維持するのに最低限必要な金はキープするため、金不足と判断される場合があります。
- 前述の武将の特性を見て、コマンドとの相性が悪くないか判断しましょう。たとえば進軍したいけど都市の武将が小心者ばかり、というケースであれば、「大胆不敵」などの武将を本国に招集することで解決するかもしれません。

### 難易度「普通」と「難しい」の違いは？

- 物量優遇によるハンデはありません。また、武将の提案内容についても差異はありません。違いがあるのは敵君主の方針のみです。
- 難易度「普通」の場合は「流言」（悪い噂を流す）や異民族襲撃をプレイヤー勢力に使ってきません。
- 難易度「普通」の場合はプレイヤー勢力を仮装敵国にする優先度が下がります。また、CPU は特定の勢力が大きくなるとその勢力を集中攻撃しますが、プレイヤー勢力への集中攻撃はしてきません。

### 行動回数はどうやって決まる？

- 都市数が2以下の場合、都市数＝行動回数となります。
- 都市数が3以上の場合、武将数が20未満なら2回、30未満なら3回、40未満なら4回、40以上だと5回となります。

### ピンチなのに兵を雇ってくれない

- たいていの場合、金不足・収益が悪すぎる・治安値が低すぎるのどれかが理由です。この場合は都市を防衛しきるのは困難でしょう。

### 進軍してくれない

- 周囲の勢力を警戒して兵力を出しづらい状況だったり、兵力では上回っていても敵勢力・都市の訓練度や武装度が高い場合は進軍困難と判断されます。外交して周囲の敵を減らしたり、地道に訓練度などを上げたり、先に城壁を破壊することで進軍可能となるかもしれません。

### 敵勢力を弱らせるには？

- 強大な勢力に対しては、正攻法で挑むより計略で弱らせて内部崩壊させるほうが効果的な場合が多いです。知略が高い武将や交渉が得意な武将を本国に集めれば、敵勢力を弱らせたり有力な敵武将を引き抜いたりするチャンスが生まれる可能性がありです。
- 計略「流言」（悪い噂を流す）で治安を 50 未満に下げると、住民反乱を誘発することがあります。これは異民族襲撃と並んで非常に強力です。

### 配下の裏切りが止まらない

- 勢力が大きくなるほど、謀反の発生確率が上がります。
- 野心が高い武将が太守になっていないか、注視しましょう。別の太守を派遣したり、場合によっては追放してしまうのも手です。
- 逆に、裏切りにくい特性（王佐の才・冷静沈着・剛直の士・小心者・優柔不断）を持つ武将が太守になっていれば概ね安心できます。階級が上がればなお盤石です。

### 他勢力と停戦・同盟したい

- 仮想敵国に設定した勢力とは、停戦したり同盟を結んだりできません。まずターゲットから外す必要があります。
- 一方、共通の敵がいる勢力とは同盟を結びやすくなります。
- 戦略を「守備的」にしたり、本国に交渉が得意な武将がいるとチャンスが増えます。

### 異民族襲撃に悩まされる

- 異民族襲撃が発生するのは、北平・南皮（烏丸）、西涼（羌）、建業・蘆江（山越）、成都・永安（南蛮）です。
- 異民族襲撃の防止・軽減策としては、優秀な太守を配置するか、城防御度を上げるしかありません。

## 更新履歴

※ 小さなバグの修正などは記載していないのでご了承ください。

2024/3/xx 初版リリース
