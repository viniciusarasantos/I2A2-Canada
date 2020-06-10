# Configuring ROS in Ubuntu 18.04

- Support Standard Markdown / CommonMark and GFM(GitHub Flavored Markdown);

![](https://pandao.github.io/editor.md/images/logos/editormd-logo-180x180.png)

![](https://img.shields.io/github/stars/pandao/editor.md.svg) ![](https://img.shields.io/github/forks/pandao/editor.md.svg) ![](https://img.shields.io/github/tag/pandao/editor.md.svg) ![](https://img.shields.io/github/release/pandao/editor.md.svg) ![](https://img.shields.io/github/issues/pandao/editor.md.svg) ![](https://img.shields.io/bower/v/editor.md.svg)

## Installation

### Configuring your Ubuntu repositories

Configure your Ubuntu repositories to allow "restricted," "universe," and "multiverse." You can [follow the Ubuntu guide](https://help.ubuntu.com/community/Repositories/Ubuntu) for instructions on doing this.

### Setup your sources.list

Setup your computer to accept software from packages.ros.org.

`$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`

### Set up your keys

`$ sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654`

If you experience issues connecting to the keyserver, you can try substituting hkp://pgp.mit.edu:80 or hkp://keyserver.ubuntu.com:80 in the previous command.

**Alternatively**, you can use curl instead of the apt-key command, which can be helpful if you are behind a proxy server:

`$ curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -`

### Installation

First, make sure your Debian package index is up-to-date:

`$ sudo apt update`

There are many different libraries and tools in ROS. We provided four default configurations to get you started. You can also install ROS packages individually.

In case of problems with the next step, you can use following repositories instead of the ones mentioned above [ros-shadow-fixed](http://wiki.ros.org/ShadowRepository).

*Option 1* | **Desktop-Full Install (Recommended)** : ROS, rqt, rviz, robot-generic libraries, 2D/3D simulators and 2D/3D perception

`$ sudo apt install ros-melodic-desktop-full`

*Option 2* | **Desktop Install** : ROS, rqt, rviz, and robot-generic libraries.

`$ sudo apt install ros-melodic-desktop`

*Option 3* | **ROS-Base (Bare Bones)** : ROS package, build, and communication libraries. No GUI tools.

`$ sudo apt install ros-melodic-ros-base`

*Option 4* | **Individual Package** : You can also install a specific ROS package (replace underscores with dashes of the package name):

e.g.

`$ sudo apt install ros-melodic-slam-gmapping`

To find available packages, use:

`$ apt search ros-melodic`

### Initialize rosdep

Before you can use ROS, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS.

 `$ sudo rosdep init` 
 `$ rosdep update`

### Environment setup

*Option 1 * | It's convenient if the **ROS environment variables are automatically added to your bash session** every time a new shell is launched:

`$ echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc`
`$ source ~/.bashrc`

*If you have more than one ROS distribution installed, ~/.bashrc must only source the setup.bash for the version you are currently using.*

*Option 2 * | If you **just want to change the environment of your current shel**l, instead of the above you can type:

`$ source /opt/ros/melodic/setup.bash`

*Option 3 * | ** If you use zsh instead of bash** you need to run the following commands to set up your shell:

`$ echo "source /opt/ros/melodic/setup.zsh" >> ~/.zshrc`
`$ source ~/.zshrc`

###End
