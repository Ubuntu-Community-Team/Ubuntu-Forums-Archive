---
title: "ati+nvidia cards together"
date: 2008-11-03
forum: General Help
---

### Post by roflmaomayo on 2008-11-03
I'm not sure which forum to post this in, but I can't seem to figure this out.

I have an nVidia AGP card with one monitor, and an ATI PCI card with two screens attached.

The proprietary drivers are needed I guess for the desktop effects. I am fine with only the nvidia card having that; the other two don't need fancy enhancements.

Apparently I can't install both the nvidia and ati binary drivers at the same time; only one may reside at a time.

I have been able to get all 3 monitors working, each with a seperate desktop where icons can get moved, but active windows cannot. That is OK- but one of the monitors were stuck in 800x600 and the graphics were mangled... And, none of the "desktop effects" would work.

So, I am figuring that if I use the closed source nVidia driver, I can have the desktop enhancements on that single monitor, and use an open source ati driver on the other two which the quality is not as important.

Currently, the other monitors are not working and only my nvidia is... here is the xorg.conf file-
```
Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "screen_nvidia" 0 0
 Screen 1		"screen_ati1" RightOf "screen_nvidia"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
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
Section "Monitor"
	Identifier	"monitor_nvidia"
EndSection
Section "Monitor"
	Identifier	"monitor_ati2"
EndSection

Section "Monitor"
	Identifier	"monitor_ati1"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"dev_nvidia"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"device_ati1"
	Driver		"vesa"
	Busid		"PCI:2:4:0"
	Screen	0
EndSection

Section "Device"
	Identifier	"device_ati2"
	Driver		"vesa"
	Busid		"PCI:2:4:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"screen_ati1"
	Device		"device_ati1"
	Monitor		"monitor_ati1"
	Option		"DesktopSetup"	"horizontal"
	Option		"OverlayOnCRTC2"	"1"
	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"screen_ati2"
	Device		"device_ati2"
	Monitor		"monitor_ati2"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen_nvidia"
	Device		"dev_nvidia"
	Monitor		"monitor_nvidia"
EndSection
```

edit: alright, using the radeon driver instead of ATI and having...
 screen 1		"screen_ati1" RightOf "screen_nvidia"
 screen 2		"screen_ati2" leftOf "screen_nvidia"
in xorg makes all 3 desktop displays active, but they are just discolored with no background, and the mouse is an X on one, and the other's mouse is a big block. I think I read somewhere that there is not a window manager running on it or something?

But the enhanced graphics on my nvidia card work fine.

---

