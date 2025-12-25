# chinorobo_ros2_opencv_02
## パッケージ概要（Package description）
知能ロボットシステムコース5R実習科目「ロボット知能化演習」の画像処理実習パッケージその2

## インストール方法（How to install & setup）
### 本パッケージのダウンロード方法（Download the repository）
```
$cd ros2_ws/src
$git clone https://github.com/tominagalab/chinorobo_ros2_opencv_02.git
```

## ノード仕様（Nodes）
### __*image_proc_node*__
１つの3チャンネル画像をサブスクライブして，画像処理後，結果の画像をパブリッシュするためのテンプレートノードである．  
このノードを基礎として各種画像処理ノードの実装を行う．  
- サブスクライバー（Subscribers）
  - __image_src__ : 3チャンネルの入力画像．
- パブリッシャー（Publishers）
  - __image_dst__: Nチャンネルの出力画像．画像処理後の画像のチャンネル数を考えて実装させる．  
- ノード起動方法（how to excute）  
```
ros2 run chinorobo_ros2_opencv_02 image_proc_node
```  
## 授業内容

### OpenCVをROS2で使用する
1. 画像データ，画像処理とは
1. OpenCVについて

### リマップ機能を活用したROS2システム構築

#### トピック名のリマップ
ノード実行時にコマンドライン引数でノードが扱うトピック名を置換できる．
パブリッシャー・サブスクライバーのどちらでも置換可能である．
以下に例を示す．
```
$ros2 run chinorobo_ros2_opencv_01 image_grayscale2binary_node --ros-args --remap /image_grayscale:=/image/r_channel
```
リマップしたいトピックを追加する場合，--remapが再度必要になる．以下に例を示す．
```
$ros2 run chinorobo_ros2_opencv_01 image_grayscale2binary_node --ros-args --remap /image_grayscale:=/image/r_channel --remap /image_binary:=/image_bin_r_channel
```

#### ノード名のリマップ
ノード実行時にコマンドライン引数でノード名を置換できる．
以下に例を示す．
```
$ros2 run chinorobo_ros2_opencv_01 image_grayscale2binary_node --ros-args --remap __node:=image_gray2bin_node1
```
#### ノード名もトピック名もリマップする場合
各リマップに対して--remapをつけて実行することになる．
以下に例を示す．
```
$ros2 run chinorobo_ros2_opencv_01 image_grayscale2binary_node --ros-args --remap __node:=image_gray2bin_node1　--remap /image_grayscale:=/image/r_channel --remap /image_binary:=/image_bin_r_channel
```