---
title: "HOWTO: Install/Configure Hardy Heron (8.04) Drivers on an Asus F9DC"
date: 2009-02-10
forum: Hardware
---

### Post by neal.s on 2009-02-10
Update your system first, then run:
sudo apt-get install build-essential

**Wireless Card (5007G) -**
System -> Admin -> Hardware Drivers -> Disable Both Atheros Drivers (HAL and Card)
sudo apt-get install linux-backports-modules-hardy-generic
sudo gedit /etc/modules/
add "ath5k" with no quotes to the bottom of the file.

**Graphics Card (NVIDIA 8400M) -**
Download driver from NVIDIA website (171.06.01 worked for me, 180.22 didn't). Extract.
CTRL-ALT-F1
sudo /etc/init.d/gdm stop
navigate to dir with driver
sudo chmod a+x driver
sudo ./driver
sudo /etc/init.d/gdm start

if the graphics card doesn't work properly:
sudo gedit /etc/X11/xorg.conf
Look to see if there's a line saying it wasn't configured properly. It should have a command below it to rebuild the xorg file.
After running that command, run sudo nvidia-xconfig #, which then ensures that the xorg file is configured properly for your card.

If this doesn't work
 
**Sound Card (ALC6600VD) -**
Go through the steps outlined here
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

