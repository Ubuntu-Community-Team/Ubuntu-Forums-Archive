---
title: "Screen resolution problem"
date: 2009-02-20
forum: Hardware
---

### Post by BonRouge on 2009-02-20
Hi there,
I hope someone can help with my screen resolution problem. I've done lots of searching and tried lots of things to fix the problem and I've failed, so here I am.

Hardware:
Video card: ATI All-In-Wonder (X1900?)
Monitors: ACER X223W (1680x1050), Buffalo (1280x1024)

What I want:
Basically, I want to make full use of both monitors, using the highest resolutions.

What I have:
It's almost as I want it. I have the dual head, extended desktop set up that I use with Windows, but the current resolution of the two monitors goes like this: 1280x1024, 1024x768.

If I touch the 'display' option in the system settings, what I have breaks down, giving me a lower resolution on the main monitor and a clone on the second monitor. Then, I have to restore the backup that I made of the xorg.conf file.

Here's the xorg.conf file as it is right now. You may notice my feeble attempts to edit it.

Thanks for any help with this.

```


Section "Monitor"
	Identifier   "Configured Monitor"
	Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1680x1050" "1600x1200" "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1280x1024"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Option "MetaModes" "1600x1200-1280x1024"
	Option "MergedFB" "true" #Enable MergedFB function
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:5:0:0"
	Option "MetaModes" "1680x1050-1280x1024"
	Driver	"fglrx"
EndSection


```

---

