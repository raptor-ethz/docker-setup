FROM osrf/ros:foxy-desktop

RUN apt-get -y update; apt-get -y install wget

# # install MAVSDK
# RUN wget https://github.com/mavlink/MAVSDK/releases/download/v0.50.0/mavsdk_0.50.0_ubuntu20.04_amd64.deb
# RUN dpkg -i mavsdk_0.50.0_ubuntu20.04_amd64.deb
# RUN rm mavsdk_0.50.0_ubuntu20.04_amd64.deb

# RUN wget https://github.com/mavlink/MAVSDK/releases/download/v1.0.6/mavsdk_1.0.6_ubuntu20.04_amd64.deb
# RUN dpkg -i mavsdk_1.0.6_ubuntu20.04_amd64.deb

# RUN wget https://github.com/mavlink/MAVSDK/releases/download/v0.50.1/mavsdk_0.50.1_ubuntu20.04_amd64.deb
# RUN dpkg -i mavsdk_0.50.1_ubuntu20.04_amd64.deb

RUN wget https://github.com/mavlink/MAVSDK/releases/download/v1.0.0/mavsdk_1.0.0_ubuntu20.04_amd64.deb
RUN dpkg -i mavsdk_1.0.0_ubuntu20.04_amd64.deb


RUN mkdir -p /raptor_ws/src 
WORKDIR /raptor_ws/src

# RUN git clone https://github.com/raptor-ethz/PX4-Autopilot.git

# WORKDIR /raptor_ws/src/PX4-Autopilot
# RUN bash ./Tools/setup/ubuntu.sh && \
#     apt install -y libopencv-dev

# RUN git checkout -b RAPTOR origin/RAPTOR && \
#     git tag v1.9.1

WORKDIR /raptor_ws/src
RUN git clone https://github.com/raptor-ethz/raptor.git 

RUN cd / && ./ros_entrypoint.sh && \
    . /opt/ros/foxy/setup.sh && \
    cd /raptor_ws/src/raptor && \
    git checkout -b foxy origin/foxy && \
    chmod 777 -R . && \
    # colcon build --packages-select raptor_interface gripper_control quad_control vicon && \
    # . ./install/setup.sh
    colcon build --packages-select raptor_interface vicon && \
    . ./install/setup.sh

# WORKDIR /raptor_ws/PX4-Autopilot
# RUN HEADLESS=1 make px4_sitl gazebo_plane
