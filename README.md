# raspicat_3d-navigation
Raspberry Pi CatでROSの[mcl_3d](https://github.com/at-wat/mcl_3dl)lや[Navigation Stack](https://wiki.ros.org/navigation)を使用して3次元自己位置推定をし、ナビゲーションを行うためのパッケージ開発用テストリポジトリです。

### 動作環境
##### ハードウェア

* ノートPC(thinkpad P43s)

##### ソフトウェア

* OS
  * Ubuntu 18.04 decktop LTS

* ROS
  * [Melodic](https://wiki.ros.org/melodic/Installation/Ubuntu)
* ROS Packages
  * [uhobeike/raspicat_3d-navigation](https://github.com/uhobeike/raspicat_3d-navigation/tree/test)

### インストール

```sh
# ROSパッケージのダウンロード
cd ~/catkin_ws/src
git clone -b test https://github.com/uhobeike/raspicat_3d-navigation.git
git clone https://github.com/at-wat/mcl_3dl_msgs.git
git submodule update --init --recursive

# 依存パッケージのインストール
rosdep install -r -y -i --from-paths .

# make & install
cd ~/catkin_ws && catkin build
source devel/setup.bash
```
以下の共有リンクから2つのデータをダウンロード。
### [rosbagおよびPCDデータ](https://1drv.ms/u/s!AomkMtsKOUnSgldqJ9qDNwgWX6s4?e=UbkbmV)

### 使い方

#### 3次元自己位置推定のテスト
ターミナル上で次のコマンドでノードを起動します。

```sh
roslaunch mcl_3dl test.launch bag_file:=${HOME}/Downloads/vtc.bag map_pcd:=${HOME}/Downloads/cloud_merge.pcd
```

### 動作例
|mcl_3dl param-change(VTC)|
|---|
|[![](https://img.youtube.com/vi/gHUiftKDlPM/0.jpg)](https://www.youtube.com/watch?v=gHUiftKDlPM)|


## ライセンス

このリポジトリはApache License 2.0ライセンスで公開されています。詳細は[LICENSE](./LICENSE)を確認してください。

