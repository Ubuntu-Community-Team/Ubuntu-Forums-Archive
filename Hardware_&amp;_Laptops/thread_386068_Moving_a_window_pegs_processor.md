---
title: "Moving a window pegs processor"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by Kindly Killer on 2007-03-16
After installing a Radeon 9550, using driver xorg-driver-fglrx, the display is beautiful but it is taxing my CPU. when i have nothing open but the system monitor, moving the SM window can get the CPU usage as high as 60%

i don't want to take any power away from the CPU because this is to be just an audio production machine. i got the radeon because my old card died and this was the cheapest one that i could also use on windows for 3d modeling (i do some graphic design, too).

how can i figure out what is using all that power and fix it? i don't care if the display is substandard; i just want to tax the CPU less.

btw i am still on dapper 

here is the stuff from my xorg.conf that i believe is relevant :
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1600x1200" "1440x1440" "1440x900" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1600x1200" "1440x1440" "1440x900" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1600x1200" "1440x1440" "1440x900" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1600x1200" "1440x1440" "1440x900" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1600x1200" "1440x1440" "1440x900" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1600x1200" "1440x1440" "1440x900" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by brettr on 2007-03-16
Hmm interesting i actually just noticed after reading this that my cpu also jumps from 600Mhz to 1.6GhZ(full Speed) when i move a window around. I am using an intel i915 though....

---

