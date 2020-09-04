# DF_Linemod_ROS
**densefusion with ros using linemod format on custom dataset with chainer mask-rcnn for segmentation**
* tested on Ubuntu 18.04, ROS Melodic, RTX 2080-Ti, CUDA 10.1, Python3.6.9, PyTorch 1.5.1
* refer `environment.yml` for other anaconda packages
* git clone in your catkin_ws https://github.com/avasalya/DF_Linemod_ROS.git

## adapted from
* https://github.com/j96w/DenseFusion
* https://github.com/hygxy/ma_densefusion
* https://github.com/wkentaro/chainer-mask-rcnn

## create conda environment
`conda env create -f environment.yml`

## install realsense ROS package
* https://github.com/IntelRealSense/realsense-ros

## download and unzip `txonigiri` folder containing weights
* https://www.dropbox.com/sh/wkmqd0w1tvo4592/AADWt9j5SjiklJ5X0dpsSILAa?dl=0

# with ROS
### 1. launch camera
* `roslaunch realsense2_camera rs_rgbd.launch align_depth:=true`

### 2. launch rviz along with publisher/subscriber services
* `roslaunch densefusion_ros densefusion.launch`
*  it publishes estimated pose as geometry_msgs/PoseArray and sensor_msgs/pointCloud2
*  also possible via
    * `rosrun densefusion_ros densefusion_ros.py` or
    * `./scripts/eval.sh` or 
    * `python3 densefusion_ros.py`



# without ROS
## Test with realsense D435
`python3 densefusion_cam.py`

## Test with rgbd images
`python3 densefusion_img.py`
