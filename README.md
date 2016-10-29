# gazebo_camera_timestamp_issue
Dedicated package to demonstrate gazebo camera timestamp issue https://bitbucket.org/osrf/gazebo/issues/1748/significant-sensor-data-timestamp-accuracy with a minimal example

# Installation
The package can be added to a ROS workspace and works without any further dependencies, provided the ROS packages`gazebo_ros_control`, `ros_controllers` and `gazebo_plugins` are available. Easiest is to get them via `apt-get`:
<pre>
sudo apt-get install ros-$ROS_DISTRO-gazebo-ros-control ros-$ROS_DISTRO-ros-controllers ros-$ROS_DISTRO-gazebo-plugins 
</pre>

# Test Setup

The test setup consists of a single URDF model that is equipped with a depth sensor mounted on a continuously spinning joint. Along the x axis, a pole is mounted in exactly 1m distance (distance between camera and closest point on pole). To the left, along the y axis, a box is mounted. The test can be started by running
<pre>
roslaunch gazebo_camera_timestamp_issue run_test.launch
</pre>
A rviz window shows sensor data and robot model. The expected/intended result is that sensor data aligns with the robot model. This is what happens when using Gazebo2 as shown in this video:

[![Alt text](https://img.youtube.com/vi/P1Iyd-b9EsU/0.jpg)](https://www.youtube.com/watch?v=P1Iyd-b9EsU)

With later Gazebo versions, the intended behavior is not observed anymore and there is a significant offset, with the most likely cause appearing to be an offset between camera and joint timestamps:

[![Alt text](https://img.youtube.com/vi/ECSa2iOGzGE/0.jpg)](https://www.youtube.com/watch?v=ECSa2iOGzGE)
