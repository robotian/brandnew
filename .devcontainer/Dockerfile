FROM osrf/ros:humble-desktop

ARG USERNAME=robotian
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get upgrade -y

# # Install a few handy tools
# RUN apt-get update \
#   && apt-get -y --quiet --no-install-recommends install \
#     bash-completion \
#     build-essential \
#     git \
#     glmark2 \
#     gnupg \
#     iputils-ping \
#     lsb-release \
#     mlocate \
#     software-properties-common \
#     sudo \
#     wget \
#     vim \
#   && rm -rf /var/lib/apt/lists/*

RUN groupadd --gid $USER_GID $USERNAME \
 && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
 && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
 && chmod 0440 /etc/sudoers.d/$USERNAME 
 

USER $USERNAME
ENV USER=$USERNAME

WORKDIR /home/$USERNAME
RUN mkdir -p workspace/src

WORKDIR /home/$USERNAME/workspace/src
RUN git clone -b humble-devel https://github.com/husky/husky.git

WORKDIR /home/$USERNAME/workspace


RUN echo "source /opt/ros/humble/setup.bash" >> /home/$USERNAME/.bashrc

