---
title: "Help removing nvidia-glx and installing ATI"
date: 2008-10-16
forum: Hardware
---

### Post by cocopuffz on 2008-10-16
I've uninstalled my nvidia 9600gt from my system because I'm going to plop it into another machine I'm building. I'm reinstalling the old ATI HD 2400XT that used to be in this machine.

I've tried remove --purge, but always get an error when it gets to the nvidia-glx section. That's the only thing that won't uninstall.

I thought installing the ATI drivers would fix this, but no luck. This machine used to run the ATI card just fine, before I had the Nvidia card in it. 

There is no mention of nv or nvidia in my xorg.conf file. Any recommendations would be great. 

Right now I'm running the ATI at the proper res, but at a horrible refresh rate. I suspect it's actually running off of software...
-------------------
this is what I get when I run fglrxinfo

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault
--------------------

this is my xorg.conf file

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Option	    "UseFBDev" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Any Ideas?

---

