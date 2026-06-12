---
title: "[SOLVED] Asus N10 Dealing with 2 video cards"
date: 2008-12-08
forum: Hardware
---

### Post by viralata00 on 2008-12-08
Hello,

I have the new Asus N10 laptop an it comes with 2 video cards (Intel and Nvidia). It's possible to choose what the card to use via a switch and rebooting.
The problem is when I switch from Nvidia to Intel the SO fails to boot normally. I have to reconfigure thought a series of windows.
And from Intel to Nvidia the proprietary drivers aren't activated automatically. 

**It is possible to make a script to detect the card in use and change my xorg.conf automatically?**

regards


**MY SOLUTION - use at your own risk**

install this package **xresprobe**. Allows you to use ddcprobe.

then create this script and name it selectVideoCard:

#! /bin/sh
### BEGIN INIT INFO
# Provides:          skeleton
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Select Video Card
# Description:       This script allows to switch video cards automatically on Asus N10
### END INIT INFO

# Author: Luís Alves <viralata00@gmail.com>

# Do NOT "set -e"

#Select
echo 'Script for detecting video card initialized'
card=$(ddcprobe | grep oem: )
echo $card #for debug
if [ "$card" = "oem: NVIDIA" ]
then
  echo 'Using NVIDIA card'
  cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf  
else
   echo 'Using Intel card'
   cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
fi

**Note:** To use this script you must have 2 xorg.conf files with the following names:
xorg.conf.nvidia    <-with the nvidia conf
xorg.conf.intel     <-intel/default conf

I've created mine booting with Intel and copy the xorg.conf to xorg.conf.intel
And the same for NVIDIA (activating the restricted drivers)

Now just chmod 744 selectVideoCard

copy the script to /etc/init.d

go to /etc/init.d and run: 
sudo update-rc.d selectVideoCard defaults

and its done.

---

