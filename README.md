# CamVox_modified
CamVox代码改动，修复了一些bug， 调整了一些代码，例如：
1. 修复运行 rosrun online camvox 出现segment fault的问题，参考我的回答https://github.com/ISEE-Technology/CamVox/issues/34#issuecomment-1196521621
2. isee_preprocessing 模块报错（把头文件中的isee_synchronize改成了isee_preprocessing）
3. 找不到livox ros driver
4. 直接使用catkin_make编译

# 参考
https://github.com/ISEE-Technology/CamVox  

# 环境
1. Ubuntu（Ubuntu18.04）  
2. ROS (测试了melodic)  
3. Opencv (测试了OpenCV 3.4.1)  
4. PCL（测试了pcl1.9）  
5. Pangolin（测试了Pangolin0.6）  
6. Ceres Solver（测试ceres-solver-1.14.0）  
7. Eigen（测试了Eigen3.3.4）  
8. livox_ros_driver  参考
9. MVS camera SDK，http://download.huaraytech.com/pub/sdk/Ver2.2.5/Linux/x86/ ，安装后，将/opt/DahuaTech/MVviewer/lib/GenICam/bin/Linux64_x64目录下的所有.so 文件拷贝至 /usr/lib 。或者添加该路径为环境变量也可。    

# 编译
1. 将CamVox拷贝到ros工程空间src文件夹内，例如~/catkin_ws/src/  
2. cd ~/catkin_ws/
3. catkin_make
4. source ~/catkin_ws/devel/setup.bash  
5. cd src/CamVox/isee-camvox/Vocabulary && tar zxvf ORBvoc.txt.tar.gz

# 数据
https://zenodo.org/record/5749452#.YuNXM29Bw5l

# 运行
1. 使用硬件 
``` 
cd ~/catkin_ws/src/CamVox/  
chmod +x run.sh  
./run.sh
```  
2. 使用rosbag 
```
roscore  
source ~/catkin_ws/devel/setup.bash   
rosrun online camvox Vocabulary/ORBvoc.bin camvox/online/Livox.yaml  
rosbag play CamVox.bag  
```
saving trajectory and colored pcd files after finishing specified frames (e.g. 1000)
```
rosrun online camvox Vocabulary/ORBvoc.bin camvox/online/Livox.yaml 1000
```