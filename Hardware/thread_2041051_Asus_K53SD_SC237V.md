---
title: "Asus K53SD SC237V"
date: 2012-08-11
forum: Hardware
---

### Post by jtdaling on 2012-08-11
Hello,

a little while ago I purchased an Asus K53S laptop and I have installed Ubuntu 12.04 on it.
Here are the specs of the K53S:

CPU Intel Corei7-2670QM
Operating System  Ubuntu 12.04 (64-bit)
RAM 8GB
RAM Upgradable to 8GB
Hard Drive Size 750GB
Hard Drive Speed 5,400rpm
Hard Drive Type SATA Hard Drive
Display Size 15.6 LED
Native Resolution1366x768
Graphics Card nVidia GeForce 610M                                                                                                                                                                                                                      
Video Memory 2048MB
Optical Drive DVD+/-RW DL
Optical Drive Speed8X
Wi-Fi 802.11 a/g/n (2,4 Ghz only)
 
Touchpad Size    3.3 x 1.9
Ports (excluding USB) Audio-in; Audio-out; DVI; Ethernet; HDMI;VGA; Smart Card Reader
USB Ports 3 (1x USB 3.0)

Everything worked out of the box after installing Ubuntu except the Nvidia video card which uses optimus.
The internal intel graphics are supported and used by default.
To make use of the Nvidia card I initiall installed the proprietary driver which crashed my system.
After this I discovered that the open source driver will support the graphic card after installing bumblebee.
In the new kernels (3.5 and above) optimus should be supported by default but I haven't tried it so far.

To install bumblebee you have to follow the following steps: 
first add the bumblebee[]("http://bumblebee-project.org/") repository:  sudo add-apt-repository ppa:bumblebee/stable


  Then you have to update and thereafter install bumblebee: 

sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia


Your Nvidia card will be used if you add optirun before the application command.
For example: optirun firefox will start firefox with accelleration.


As GUI I choose Gnome3 and this also runs out of the box.

---

### Post by jaithehulk on 2012-09-08
Thanks I have a Asus K53SD laptop with Nvidia 610m and was searching for drivers for my 610m. I will surely try bumblebee.
Can u tell me the effects of upgrading my kernel to 3.5?

---

### Post by jaithehulk on 2012-09-10
I installed kernel 3.5 and the display drivers are working properly.. thanks!

---

