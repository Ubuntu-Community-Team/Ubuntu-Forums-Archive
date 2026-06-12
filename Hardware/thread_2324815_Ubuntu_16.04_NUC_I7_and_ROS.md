---
title: "Ubuntu 16.04 NUC I7 and ROS"
date: 2016-05-16
forum: Hardware
---

### Post by Stephen_Wilkerson on 2016-05-16
Does ROS run on the Nuc I7 with ubuntu 16.04 
if not will it work with ubuntu 14.04?

Thanks
:confused:

---

### Post by QDR06VV9 on 2016-05-16
have not heard anything bad yet..but still early.
Have you had a chance to see this yet?  [http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)

---

### Post by Stephen_Wilkerson on 2016-05-16
Yes I used this to write the image and then I booted into ubuntu on the NUC from the dongle.  From there I installed ubuntu 16.04 and all is wonderful.  Then I tried to follow the standard ROS over the internet and bang there's where it stopped.  
When I get to:
sudo apt-get install ros-jade-desktopI get back Unable to locate package ros-indigo-desktop-full
not sure why that is?

---

### Post by QDR06VV9 on 2016-05-16
I have not tried this as of yet...but dependices maybe?

>  [h=2][Kinetic Kame (May 2016 - May 2021)]("http://www.ros.org/reps/rep-0003.html#id18")[/h] Required Support for:
 
[LIST]
[*]Ubuntu Wily (15.10)
[*]Ubuntu Xenial (16.04)
[/LIST]
 Minimum Requirements:
 
[LIST]
[*]C++11
[LIST]
[*]GCC 4.9 on Linux, as it's the version that Debian Jessie ships with
[/LIST]
 
[*]Python 2.7
[LIST]
[*]Python 3.4 not required, but testing against it is recommended
[/LIST]
 
[*]Lisp SBCL 1.2.4
[*]CMake 3.0.2
[LIST]
[*]Debian Jessie ships with CMake 3.0.2
[/LIST]
 
[*]Boost 1.55
[LIST]
[*]Debian Jessie ships with Boost 1.55
[/LIST]
 
[/LIST]
 Exact or Series Requirements:
 
[LIST]
[*]Ogre3D 1.9.x
[*]Gazebo 7
[*]PCL 1.7.x
[*]OpenCV 3.1.x
[*]Qt 5.3.x
[*]PyQt5
[/LIST]
 Buildsystem support:
 
[LIST]
[*]catkin:
[LIST]
[*]build from source
[*]release for binary packaging
[*]wiki documentation
[*]continuous integration
[/LIST]
 
[*]rosbuild:
[LIST]
[*]build from source
[/LIST]
 
[/LIST]
 

> The primary platforms for ROS are Canonical's Ubuntu releases, and our intent is to track these releases as best as possible while also allowing for current, thirdparty libraries to be used.

More Here [http://www.ros.org/reps/rep-0003.html#indigo-igloo-may-2014](http://www.ros.org/reps/rep-0003.html#indigo-igloo-may-2014)
Also take a look Here: [http://answers.ros.org/question/217485/ros-indigo-on-ubuntu-140403-e-unable-to-locate-package-ros-indigo-desktop-full/](http://answers.ros.org/question/217485/ros-indigo-on-ubuntu-140403-e-unable-to-locate-package-ros-indigo-desktop-full/)

---

### Post by QDR06VV9 on 2016-05-16
Here is the one I have been trying to find: 
InstallingandConfiguringROSEnvironment
[http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment](http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment)

---

