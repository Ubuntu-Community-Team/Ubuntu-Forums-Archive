---
title: "Do I need to install NVIDIA driver"
date: 2020-12-03
forum: Hardware
---

### Post by satimis on 2020-12-03
Hi all,

Ubuntu 20.04 desktop
Dell 32" 4K Display

My new MSI GeForce GTX 1650 super display card doesn't work properly with following faults;

1. To start -> Activities (top menu bar) -> Settings or some other applications
The display turns to a dark screen -> then logout automatically.  I have to re-login and I can't start those applications.

2. Occasionally to save a text document, the display screen turns to a dark screen and then login out automatically.  I have to re-login resulting in lost of work.

3. Scrolling fast on webpage or document the display screen flickers.

Do I need to install its driver?  If YES, to install its driver on Ubuntu Repo or download its driver on Nvidia website?

I found following links on Internet;

Nvidia drivers not working with GeForce GTX 1650 Mobile / Max-Q 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-440/+bug/1871041](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-440/+bug/1871041)

How to install the NVIDIA drivers on Ubuntu 20.04 Focal Fossa Linux
[https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux)

How to Install Nvidia Driver on Ubuntu 20.04 
[https://linoxide.com/linux-how-to/how-to-install-nvidia-driver-on-ubuntu/](https://linoxide.com/linux-how-to/how-to-install-nvidia-driver-on-ubuntu/)

NVIDIA GTX 1650 SUPER Driver Debian Installation Guide
[https://tutorialforlinux.com/nvidia-gtx-1650-super-driver-debian-installation-guide/](https://tutorialforlinux.com/nvidia-gtx-1650-super-driver-debian-installation-guide/)

Please advise.  Thanks in advance.

Regards

---

### Post by mikewhatever on 2020-12-04
Yes, use the Additional Drivers tool to install it from the repositories. There is no need to download and install a driver manually, unless there is a special need for a specific driver.

---

### Post by satimis on 2020-12-04
> **mikewhatever said:**
> Yes, use the Additional Drivers tool to install it from the repositories. There is no need to download and install a driver manually, unless there is a special need for a specific driver.
Hi mikewhatever,

Thanks for your advice.

I followed the "Command Line Nvidia Installation Method" on below document;
How to install the NVIDIA drivers on Ubuntu 20.04 Focal Fossa Linux 
[https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux)

Steps performed:-

1) 
$ ubuntu-drivers devices```

== /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0 ==
modalias : pci:v000010DEd00002187sv00001462sd00003850bc03sc00i00
vendor   : NVIDIA Corporation
model    : TU116 [GeForce GTX 1650 SUPER]
driver   : nvidia-driver-455 - distro non-free recommended
driver   : nvidia-driver-440-server - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-450 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

2)
~$ sudo apt install nvidia-driver-455```

.....
.....
Setting up libnvidia-decode-455:i386 (455.38-0ubuntu0.20.04.1) ...
Setting up libnvidia-encode-455:i386 (455.38-0ubuntu0.20.04.1) ...
Setting up mesa-vulkan-drivers:i386 (20.0.8-0ubuntu1~20.04.1) ...
Setting up libgl1-mesa-dri:i386 (20.0.8-0ubuntu1~20.04.1) ...
Setting up libglx-mesa0:i386 (20.0.8-0ubuntu1~20.04.1) ...
Setting up libglx0:i386 (1.3.1-1ubuntu0.20.04.1) ...
Setting up libgl1:i386 (1.3.1-1ubuntu0.20.04.1) ...
Setting up libnvidia-ifr1-455:i386 (455.38-0ubuntu0.20.04.1) ...
Setting up libnvidia-fbc1-455:i386 (455.38-0ubuntu0.20.04.1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
Processing triggers for initramfs-tools (0.136ubuntu6.3) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-56-generic

```

$ sudo reboot

Now I can start -> Activities (top menu) -> Settings and other application without logout automatically

Also I can save .txt documents and scrolling on webpages/documents without problem.

$ xrandr | more```

....
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-4 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 
697mm x 392mm
   3840x2160     60.00*+  29.98  
   2560x1440     59.95  
   2048x1280     59.96  
   2048x1080     24.00  
   1920x1200     59.88  
   1920x1080     60.00    59.94    50.00    23.98  
   1600x1200     60.00  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x720      59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  

```

I'll continue observing its operation.

Thanks again

Regards

---

