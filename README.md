# LOAM_OUSTER64

Added suppport for OUSTER 16Gen1  64Gen1  128Gen1  64Gen2  LIDARs


#Video
https://www.youtube.com/watch?v=lttLV0zQ2BM

![alt text](https://github.com/snakehaihai/LOAM_3D_LIDARs/blob/master/loamwithouster64.png)


# Prerequisite
Do not use ROS version of PCL as it end up with seg fault

Download PCL and install separately. mkdir build && make

Change the link in the cmakelist to your build 

Modifiy SET("PCL_DIR" "XXXXX" to your directory. Sample is given inside


#Bag download
http://data.ouster.io/sample-data-2018-08-29/index.html


# Build and Running:

`cd ~/catkin_ws/src/`

`git clone https://github.com/snakehaihai/LOAM_OUSTER64.git `  // this package

`git clone https://github.com/ouster-lidar/ouster_example.git `  //for convert packet to pointcloud



`$ cd ~/catkin_ws`

`$ source ~/catkin_ws/devel/setup.bash`

`$ roslaunch ouster_ros os1.launch replay:=true //convert packet to pointcloud`

`$ rosparam set /use_sim_time true `

`$ roslaunch loam_ouster loam_ouster.launch`

`$ rosbag play --clock -s 30 -r 0.2 '/home/snake/catkin_ws/OS1_bag/2018-08-29-16-46-17_0.bag' `


In their bag. first 30 sec has no movement. Need to run it at 0.2 so that my PC can work. or state estimation will be wrong all the way

Also Oyster IMU is in fucked up format at the moment, so dont use it. Other sample BAG can be found at http://data.ouster.io/sample-data-2018-08-29/index.html




# Acknowledgement
@conference{Zhang-2014-7903,
author = {Ji Zhang and Sanjiv Singh},
title = {LOAM: Lidar Odometry and Mapping in Real-time},
booktitle = {Robotics: Science and Systems Conference},
year = {2014},
month = {July},
}
[ROS & Loam_velodyne](https://ishiguro440.wordpress.com/2016/04/05/%E5%82%99%E5%BF%98%E9%8C%B2%E3%80%80ros-loam_velodyne/) 

