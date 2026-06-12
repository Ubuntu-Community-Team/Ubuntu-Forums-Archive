---
title: "After three years, still no Syntek webcam"
date: 2010-06-18
forum: Hardware
---

### Post by randcoop on 2010-06-18
Asus is a well known laptop brand that makes (made?) the F3 series laptops that came with Syntek webcams built in.  For at least the past three years (that I can easily count), the Ubuntu forums, the bug reporting system, and other help sites on the Internet for Linux distros have been replete with complaints from users who cannot get their Syntek webcams to work properly.

There are at least two persistent problems with the Syntek webcams in Linux.  The first is that it is very difficult to install the drivers.  The only good instructions for doing so can be found on a French language site.  As a result, most users are unable to get the drivers installed.

Those who do get the driver installed find that the camera works only with certain software (Cheese, perhaps, or Skype, maybe).  

And then there's the terrible problem that the camera might be activated (turned on) simply by visiting a certain web site (France 24, for example, or Skype.com).  Once on, the camera cannot be turned off except by completely shutting down the laptop (re-starting won't do it).  

I wonder if there is anyone out there connected to the Ubuntu development team who might be able to get someone to work a bit on this problem.  After all, three years is not a short period of time and Asus is not a small manufacturer of laptops (Synteks also are installed on HP laptops sometimes).

As I said, this has already been reported in the bug system, but no one seems to be doing (have done) anything about it.

---

### Post by dino99 on 2010-06-18
maybe you already have found it, sorry, but its an uptodated doc with usefull links

google translate can help in case

---

### Post by dpanario on 2010-06-19
> **randcoop said:**
> 
I wonder if there is anyone out there connected to the Ubuntu development team who might be able to get someone to work a bit on this problem.  After all, three years is not a short period of time and Asus is not a small manufacturer of laptops (Synteks also are installed on HP laptops sometimes).

As I said, this has already been reported in the bug system, but no one seems to be doing (have done) anything about it.

hi, i'm not in ubuntu developing area but i have the damn syntek ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W, aka d-max 1135

after 3 years of being fighting with this webcam, i made a script and don't seems to have problems.
I tryied it on jaunty, karmic and lucid with driver 2.1.0 :)

if you want to try, just copy and execute 

----------------------------------------------------------

#!/bin/sh

# Dependencias
sudo apt-get install build-essential

# Controlador
wget [http://downloads.sourceforge.net/pro..._mirror=freefr](http://downloads.sourceforge.net/pro..._mirror=freefr)
tar xvzf stk11xx-2.1.0.tar.gz && cd stk11xx-2.1.0 && wget [http://bookeldor-net.info/merdier/Makefile-syntekdriver](http://bookeldor-net.info/merdier/Makefile-syntekdriver) && make -f Makefile-syntekdriver && sudo make -f Makefile-syntekdriver install
sudo modprobe stk11xx && sudo lsusb -v | grep -A 8 Syntek && sudo addgroup $USER video && cat /sys/class/video4linux/video0/vflip && echo 1 >/sys/class/video4linux/video0/vflip
sudo echo "Syntek Webcam" | sudo tee -a /etc/modprobe.d/options && sudo echo "options stk11xx vflip=1 brightness=0xBBBB" | sudo tee -a /etc/modprobe.d/options

# Camorama
sudo apt-get install camorama

# Mensaje
zenity --info --title="finished" --text="just try, camorama." \

-----------------------------------------------------------

hope it helps, 

regards

---

### Post by randcoop on 2010-07-01
Thanks for this.  But I don't think it solves some of the problems I mentioned, especially the one where the camera comes on and cannot be turned off.  

My hope remains that someone who develops Ubuntu will someday address this problem.

---

### Post by Farotz on 2012-06-04
Hi Dpanairo,

I have tried your script but it doesn't work on my laptop.
I have a Packard Bell Easynote BU45 with a Syntek camera. I has recently installed Ubuntu 12.04 and the camera is totally dead, not detected by the system. I've try to open it with Cheese, GUVCView and Skype, but I always get something like: device not detected.
If if run a lsusb I get:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 12d1:142d Huawei Technologies Co., Ltd. 
Bus 001 Device 004: ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W
Bus 002 Device 002: ID 1d57:0008  
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
farotz@farotz-EasyNote-BU45:~$ 

Any advice?
Thank you

---

