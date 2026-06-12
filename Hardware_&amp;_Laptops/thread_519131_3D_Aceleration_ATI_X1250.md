---
title: "3D Aceleration ATI X1250"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by abrarey on 2007-08-06
Hi I´m looking 3d Acceleration on my laptop. I tired of looking older post and google but anything yet.
I have the latest Drivers from ATI website.
The log of my xorg had some errors and warnings:

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards.
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
```

Any help!!

---

### Post by greybit on 2007-08-06
You might give the program Envy a try:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
(You can select the ATI driver installation.)

It will try to do all of the work for you.

---

### Post by dougfractal on 2007-08-06
Update: I don't recommend Envy for this card as It will try to install the latest driver.  Although if it works it would make life easier. 
just make a backup of your xorg.conf as it may BSOD.

Any tweak to xorg can BSOD so be prepared for it.


Read this thread
[http://ubuntuforums.org/showthread.php?t=396751](http://ubuntuforums.org/showthread.php?t=396751)
> 
it says you need ati driver 8.34.8 ... not the latest.

and this 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)
> Install Xgl (This is the main problem with ATI cards. The fglrx driver will not support the built-in Compiz feature in Ubuntu and we need Xgl to run our new version of Beryl with an ATI card.):


--------------------------------------------------------------------------

**Testing X** (I'm testing this please feedback)
In this method you can trial an xorg.conf without losing X.

Save your new xorg.conf in your home folder as ~/xorg.conf.new

Code:

chmod u+s /usr/X11R6/bin/Xorg    #  add sticky bit to Xorg

Code:

[ctrl+alt+f1]
startx -- :1 -config ./xorg.conf.new
 
#  potential crash if hotswap nv to nvidia, so restart X between goes.
[ctrl+alt+F7]   normal login
[ctrl+alt+F9]   new X session  (check F8 )

[ctrl+alt+f2]
DISPLAY=:1 xterm &    # start xterm in case gnome fails
killall startx
sudo /etc/init.d/dgm restart    #  potential crash if hotswap nv to nvidia, so restart X

logs for is test at /var/log/Xorg.1.log

If X is good then
Code:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
cd ~
sudo cp ./xorg.conf.new  /etc/X11/xorg.conf
sudo /etc/init.d/dgm restart

---

### Post by abrarey on 2007-08-09
Im going to test.
Thanks

---

### Post by dougfractal on 2007-08-09
> **abrarey said:**
> Im going to test.
Thanks


I have a new way to test for you. Its a script called **testx**
[http://ubuntuforums.org/showpost.php?p=3157811&postcount=167](http://ubuntuforums.org/showpost.php?p=3157811&postcount=167)

---

