# apriltags_ros
apriltags ros package for usb camera detection

ubuntu16.04 ROS kinetic 

#Demo videos

[![apriltags_detections](https://github.com/xenobot-dev/apriltags_ros/blob/master/software/apriltags_launch.png](https://youtu.be/dY6OzeA6rb4)

##Installation

###1.apriltags-cpp 
Building
========

git clone 


To compile the code, 
```
    cd apriltags_ros/software/apriltags-cpp
    mkdir build
    cd build
    cmake .. -DCMAKE_BUILD_TYPE=Release
    make
```
Demo/utility programs
=====================

###2.apriltags ROS packages
```
    cd ~/apriltags_ros/apriltags_ws
    source environment.sh
    catkin_make 
    source environment.sh
```

##Usage
Print out tag36h11.pdf  in apriltags_ros/software/  with your desire size.

edit tag size in  apriltags_ros/apriltags_ws/src/launch/usb_cam_apriltags.launch

For example The tag ID 1 inner width is 82mm  set 0.082m
```
   <rosparam param="tag_data">
      "1": 
        size: 0.082  
      "2":
        size: 0.048
    </rosparam>
 ```

also remap right  topic for your camera device
the default using usb_cam.
ex:
    <remap from="~image" to="/usb_cam/image_raw"/>
    <remap from="~camera_info" to="/usb_cam/camera_info"/>

Open 4 terminal shows like this, you can utilize byobu tool.

T1: `roslaunch usb_cam usb_cam-test.launch`
T2: `roslaunch apriltags usb_tag.launch`
T3: `rostopic echo /apriltags/detections`
T4: `rosrun image_view image_view image:=/usb_cam/image_raw`
