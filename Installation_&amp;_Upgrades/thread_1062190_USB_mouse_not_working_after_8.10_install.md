---
title: "USB mouse not working after 8.10 install"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by deangl on 2009-02-06
After running 8.04LTS for a while, I upgraded to 8.10.  AMD64
Now when I boot, the mouse does not work (USB fob with wireless mouse - Logitech).

I enter username and password a login page.  Desktop displays with cursor in the middle of screen as expected.  Mouse does not move the cursor.  If I unplug USB fob and plug it back in, mouse works fine.

This is extremely inconvenient.  I have searched other threads, but nothing helps so far.

All help would be appreciated - I would like to get this resolved as soon as possible.

Thanks,
Dale

---

### Post by TheDumbening on 2009-02-06
What mouse do you use? My logitech V220 worked fine after 8.10 installation.

---

### Post by deangl on 2009-02-06
I believe it is an MX610.  We have used this mouse for a year or two and it has worked great until I installed 8.10.  It still works great if I unplug the USB connection and then plug it back in.  Sounds like something changed in the kernel for handling USB.  

Any help would be appreciated.

Thanks,
Dale

---

### Post by deangl on 2009-02-09
Additional info: When logging of of one user and logging on as another, the mouse stops working.

This sounds more like an X Server problem now...

Any thoughts or help would be greatly appreciated.

Thanks,
Dale

---

### Post by deangl on 2009-02-21
Anybody have any ideas on this USB mouse not working after GDM starts?

---

### Post by rdilliker on 2009-02-21
I have the same issue with both my mouse and keyboard and have been searching for quite some time. Unfortunately, on these forums there are a few threads about this but no one seems to know exactly what the problem is. 

If I restart gdm my mouse and keyboard actually work. As suggested on another website it seems to be some issue where the HAL is not initialized soon enough. I did fix my issue by following the information [here]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254840"). Basically I uncommented the mouse and keyboard sections in xorg.conf and had to add the inputdevices under the serverlayout section. The serverlayout section part seems to be the key. I am surprised more people aren't seeing this issue.

Here's my xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 		"Default Screen"
	InputDevice 	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:5:0:0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by deangl on 2009-03-28
Never did get this working.  It has been a while since we did a clean install (been doing upgrades...).  So just did a clean 8.10 install.  Mouse works fine after reboots.

---

