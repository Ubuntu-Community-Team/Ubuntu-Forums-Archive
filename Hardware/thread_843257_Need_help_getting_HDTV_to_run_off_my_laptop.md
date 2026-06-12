---
title: "Need help getting HDTV to run off my laptop"
date: 2008-06-28
forum: Hardware
---

### Post by alluran on 2008-06-28
Trying to set my laptop to run off my HDTV, I have a Toshiba 47" tv (only supports 1080i, NOT 1080p, so that will be important in my config). So far I haven't been able to get it to work.I'm running Ubuntu 8.04, with the nvidia proprietary drivers.
Specs Of the machine:
  Asus g2s
    64x Core 2 Duo T7700
    4gb ram
    Nvidia 8600m GT

The card has both SVideo and HDMI out, either would be fine, just as long as I can get video on the TV in high def so I can watch all my high def movies.

My xorg config file is as follows (had to comment a bunch out after it really broke it)

```

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Device[LCD]"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

#Section "Device"
#	Identifier	"Device[HDTV]"
#	Driver		"nvidia"
#	Screen		1
#	Option		"NoLogo"	"True"
#	Option		"ConnectedMonitor" "HDTV"
#	Option 		"TVStandard"	"1080i"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Monitor"
	Identifier	"Monitor[LCD]"
EndSection

#Section "Monitor"
#	Identifier	"Monitor[HDTV]"
#	HorizSync 15-45
#	VertRefresh 50-60
#	Mode "1080i"
#		Flags	"Interlace"
#	EndMode
#	# ModeLine
#EndSection

Section "Screen"
	Identifier	"Screen[LCD]"
	Monitor		"Monitor[LCD]"
	Device		"Device[LCD]"
	Defaultdepth	24
EndSection

#Section "Screen"
#	Identifier	"Screen[HDTV]"
#	Monitor		"Monitor[HDTV]"
#	Device		"Device[HDTV]"
#	Defaultdepth	24
#EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Screen[LCD]"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

```

---

