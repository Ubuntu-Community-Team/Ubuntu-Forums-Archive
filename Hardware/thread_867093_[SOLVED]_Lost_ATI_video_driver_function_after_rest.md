---
title: "[SOLVED] Lost ATI video driver function after restart, how do I get it back?"
date: 2008-07-22
forum: Hardware
---

### Post by bg86 on 2008-07-22
I have an ATI x1950xt graphics card that was detected upon install and worked properly for 2 days after I installed the drivers with EnvyNG. 

Irrelevant probably, but I accidentally typed a wine command improperly and instantly got a garbled screen so I hit the reset button on the box. Upon return to Ubuntu and before login I got the dialog telling me it can't detect my video card or screen, so I tried setting it to Radeon fglxr in the dialog but still no driver enabled in Ubuntu. After uninstalling the driver in EnvyNG and reinstalling, still nothing. Even using the Ubuntu Hardware Drivers dialog to install the proprietary drivers I get nothing upon restart, just the same undetectable card/screen dialog and very low screen res in Ubuntu.

Any help would be greatly appreciated, and I will pass the knowledge on to fellow users in the future.


xorg.conf :
```
 Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
 
```

---

### Post by Rocket2DMn on 2008-07-23
I would make sure the fgrlx drivers are completely uninstalled - disable from Hardware Drivers and make sure the uninstall is complete from EnvyNG.  You can then also run
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Now reconfigure X with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
You should reboot your computer to finish unloading any driver changes with kernel modules.
Once you are rebooted into Ubuntu, you can try again with the restricted drivers.  You should try first with the Hardware Drivers program since this should adjust automatically when you get kernel upgrades.  If you need to use EnvyNG again, go ahead.  If you install the drivers manually, I suggest checking out vor's post here - [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by bg86 on 2008-07-23
I was due for giving up after trying nearly EVERYTHING. In uninstalling some of the other BS in an attempt to install the binaries straight from the ati site I received an error I couldn't diagnose. From there I ran envyNG and restarted and fglrxinfo'd and saw the ATI Technologies in the opengl vendor and knew I had it.

I have a feeling your post could have solved my problem, so I am bookmarking this page and listing it as solved, although by accident. Thanks so much, I just know I'll be referencing back to this post in the near future because of how easy this problem set in. I'm pretty sure I tried that method, but the purge thing might make a difference.

This linux stuff can drive you straight up a wall. I feel like I need to get Johnny Number Five in here to fix things. Sometimes it feels this stuff wasn't made for real humans.

---

