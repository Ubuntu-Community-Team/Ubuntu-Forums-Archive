---
title: "(Another) External monitor problem on Gateway T-1625 Laptop"
date: 2008-11-26
forum: Hardware
---

### Post by subpar on 2008-11-26
I've been all over the web looking for a solution to this. I am running Ubuntu Hardy (8.04) on a Gateway T-1625 Laptop. I also have the Windows Vista install that came with the Laptop as a dual boot (damn proprietary software!). When I am in Vista, I usually hook up my keyboard, mouse, and external Moniter (which runs at 1680x1050), close the laptop lid, and use it more like a desktop. I want to be able to do the same thing with Ubuntu.

As I said, I have been all over the web looking for a solution, have tried several, and it doesn't change my situation. Currently, the external monitor mirrors what's on the laptop LCD at the same resolution. This causes the panel to go off the bottom of the screen, and look generally grainy. I would like it to work like windows does, if possible. This would require:

1.) External moniter works as an extension (not necessarily in 1680x1050, but if it did, it would one up Vista) when LCD screen is active. 
2.) When LCD screen is inactive, the external monitor works as the main monitor.

To complicate things a little, I am running compiz, but I am going to set up another account without compiz to work out the kinks when I get out of work tonight.

Here is my xorg.conf, with the changes I've made:

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
	Identifier	"device0"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Option	   	"DesktopSetup"	"horizontal"
	Option		"OverlayOnCRTC2"	"1"
EndSection
Section "device" 
	Identifier	"device1"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
EndSection
Section "Monitor"
	Identifier	"monitor0"
	Modelname	"LCD Panel 1280x1024"
EndSection
Section "Monitor" 
	Identifier	"monitor1"
	Modelname	"LCD Panel 1680x1050"
EndSection
Section "Screen"
	Identifier	"screen0"
	Device		"device0"
	Monitor		"monitor0"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x800@60"	"1440x900@60"	"1280x720@60"	"1600x1024@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection
Section "screen"  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 	0 	"screen0" 0 0
	Option	    	"Dualhead" "true"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"dri"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

...and here is my xorg.conf, before I changed anything:
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
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Any help with this problem, would be greatly appreciated.

---

### Post by subpar on 2008-11-26
Update: I'm going to upgrade to 8.10 to see if this changes anything.

---

