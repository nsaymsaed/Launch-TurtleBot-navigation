# Launch-TurtleBot-navigation

first open the terminal with Ctrl+alt+T

second enter this 4 commands one at a time.

$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
$ chmod 755 ./install_ros_noetic.sh 
$ bash ./install_ros_noetic.sh

eache one of this commend in single line.

## step 2: install dependent ROS packages

$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers

this commend you should write it in one line.

## step 3: Install TurtleBot3 Packages

now you should Install TurtleBot3 via Debian Packages.

$ sudo apt-get install ros-kinetic-dynamixel-sdk
$ sudo apt-get install ros-kinetic-turtlebot3-msgs
$ sudo apt-get install ros-kinetic-turtlebot3

( not in one line, each code is on a separate line )

##  Install Simulation Package

TurtleBot3 Simulation Package requires turtlebot3 and turtlebot3_msgs packages as prerequisite. you should know that ( Without these prerequisite packages, the Simulation cannot be launched ).

$ cd ~/catkin_ws/src/
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make

( like i said before each cde is on a separate line ).

## Launch Simulation World

you have 3 simulation environments are prepared for TurtleBot3.

1- Empty World.

2- TurtleBot3 World.

3- TurtleBot3 House.

( TurtleBot3 World ) let's see what the result of running it is.

$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
![Screenshot 2024-08-05 084831](https://github.com/user-attachments/assets/490c39cf-69d7-4b60-9546-96020b7fceb4)


## Now Opening SLAM

using 

roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
![Screenshot 2024-08-05 084818](https://github.com/user-attachments/assets/b0f5b114-f9b6-4b13-9b25-3b2623ba5991)
create a map and save it.

rosrun map_server map_saver -f ~/map

then you shouls run this command 
rosrun map_server map_saver -f ~/map
![Screenshot 2024-08-05 084759](https://github.com/user-attachments/assets/47b0711e-4787-45c3-b247-0ea6ba3b6fad)

## navigation 

start, load the save map, write this command:
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:='/home/muh/map.yaml'
![Screenshot 2024-08-05 084729](https://github.com/user-attachments/assets/5f6a0b1e-7a75-4cc4-a927-54a69228bf40)

Finally you can use and move the robot as you want.





