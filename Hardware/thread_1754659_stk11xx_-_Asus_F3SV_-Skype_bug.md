---
title: "stk11xx - Asus F3SV -Skype bug"
date: 2011-05-10
forum: Hardware
---

### Post by djdill on 2011-05-10
Hey Guys

Looking for a fix for the current problem I am having with the Web Cam driver.. I was able to get it working fine in 10.10 and 10.04 with Skype however I can't get it to work with 11.04.

I can install the driver fine and get it to work with VLC and Camorama. The problem I have is that it does not work with Skype.. Now I know a new Skype patch was pushed out fairly recently this may have broken it? 

INFO:
This is how i got it to work with 11.04 :
[http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

mkdir syntek
svn co [https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver)
cd syntek
Get the custom make file : [http://ubuntuone.com/p/pQQ/](http://ubuntuone.com/p/pQQ/)
(some times have to edit the stk11xx-sysfs.c and stk11xx-v4l.c)
make -f Makefile-syntekdriver
sudo make -f Makefile-syntekdriver install
sudo modprobe stk11xx

... works fine works for VLC etc..

When opening Skype it finds the Cam, but when testing it only turned on LED for 1.5 sec and drops to black screen:
dmesg |tail
[ 2175.466500] stk11xx: Error : Register 0x0001 = 02
[ 2175.669142] stk11xx: Error : Register 0x0001 = 02
[ 2175.869143] stk11xx: Error : Register 0x0001 = 02
[ 2176.067998] stk11xx: Error : Register 0x0001 = 02
[ 2176.267859] stk11xx: Error : Register 0x0001 = 02
[ 2176.467866] stk11xx: Error : Register 0x0001 = 02
[ 2176.667861] stk11xx: Error : Register 0x0001 = 02
[ 2176.866606] stk11xx: Error : Register 0x0001 = 02
[ 2177.065370] stk11xx: Error : Register 0x0001 = 02
[ 2177.263962] stk11xx: Error : Register 0x0001 = 02

Web cam info:

[   16.949112] stk11xx: Syntek USB2.0 webcam driver startup
[   16.949115] stk11xx: Copyright(c) 2006-2009 Nicolas VIVIEN
[   16.949137] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[   16.949139] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A31.
[   16.949141] stk11xx: Release: 0005
[   16.949143] stk11xx: Number of interfaces : 1
[   16.949432] stk11xx: Initialize USB2.0 Syntek Camera
[   16.972398] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008/0x0
[   17.012927] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
'


If anyone can help that would be great!

Dj Dill

---

### Post by _arsen_ on 2011-05-30
Seems like I have the very same problem on my Asus F3SA. Webcam works everywhere but not in Skype. Its really annoying. Please help some1.

PS. lsusb gives:
Bus 001 Device 002: ID 174f:6a33 Syntek Web Cam - Asus F3SA, F9J, F9S

Webcam info from dmesg:

[ 5264.743709] stk11xx: Syntek USB2.0 webcam driver startup
[ 5264.743712] stk11xx: Copyright(c) 2006-2009 Nicolas VIVIEN
[ 5264.743734] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[ 5264.743736] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A33.
[ 5264.743739] stk11xx: Release: 0005
[ 5264.743741] stk11xx: Number of interfaces : 1
[ 5264.744319] stk11xx: Initialize USB2.0 Syntek Camera
[ 5265.354784] stk11xx: Syntek USB2.0 Camera is ready
[ 5265.354977] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[ 5265.355064] usbcore: registered new interface driver usb_stk11xx_driver
[ 5265.355070] stk11xx: v2.2.0 : Syntek USB Video Camera

PPS Running skype with command: LD_PRELOAD=/usr/lib32/libv4l/v4l2compat.so
wont work also.

---

### Post by nikola.borisof on 2011-05-31
Same problem please help.

---

