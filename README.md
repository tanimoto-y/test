# 概要
第29回高専プロコン競技部門の予選用探索部分です。  
現在、探索用の関数と、探索用のファイル入出力を実装しています。  
# 仕様（探索部分）
# 仕様（ファイル入出力部分）
ファイル入出力にはField_Fileクラスを用いています。  
ファイル入力関数はクラス内のload関数、出力関数はクラス内のsave関数です。  
Field_Fileクラスを**Field_File ff;**と宣言したとき  
ファイルの入力は**ff.load("入力ファイル名");**  
ファイルの出力は**ff.save("出力ファイル名");**  
で動きます。  
入力ファイル名は「file_for_competition.txt」  
出力ファイル名は「output.txt」としています。  
入力形式、出力形式ともに予選用の仮の形式に準拠しています。  
  
また、ファイルの入力時、各要素はField_Fileクラス内の変数に代入されます。  
 int **field_size_x** : フィールドの横方向の大きさ  
 int **field_size_y** : フィールドの縦方向の大きさ  
 int **tile_points**[12][12] : 各マスの値 （-16〜16）  
 int **tile_status**[12][12] : 各マスの状態（色）（0〜2 0:白,1:赤,2:青）  
 Agent **red**[2][SEARCHING_TURNS] : 赤チームのエージェントの状態（Agent構造体については後述）  
 Agent **blue**[2][SEARCHING_TURNS] : 青チームのエージェントの状態  
出力時も同じ変数を参照します。  
   
※SEARCHING_TURNSは一度に探索する回数を示す定数で、初期値は10としています。  
  
Agent構造体は各エージェントの状態を格納する構造体です。内容は以下のとおりです。  
 **position_x** : エージェントのx座標（横）  
 **position_y** : エージェントのy座標（縦）  
 **act** : エージェントの行動（0:待機,1:移動,2:除去）  
Field_Fileクラス内ではAgent構造体red, blueは2次元配列です。  
redまたはblue[エージェント総数][一度に探索する回数]と宣言していて、  
例えばredチームの1番目（初期位置が右下）のエージェントの5回目であれば、  
 x座標はred[1][5].position_x;  
 y座標はred[1][5].position_y;  
 行動はred[1][5].act;  
で参照できます。  
# その他
main.cppやREADME.mdも含めて、必要に応じて変更・修正等行っていただくようお願い致します。