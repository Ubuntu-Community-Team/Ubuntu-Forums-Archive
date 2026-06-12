---
title: "ProBook 4520s: ATI driver - problem with video"
date: 2010-07-05
forum: Hardware
---

### Post by Argonisius on 2010-07-05
Hello,
I have a laptop HP ProBook 4520s with Ubuntu 10.04. I installed ATI proprietary driver, but it causes a problem with video playback: When I play video, there are (mainly during action scenes) horizontal stripes on the screen. 

Can you help me?

---

### Post by Argonisius on 2010-07-07
I found, that there must be a problem with vertical sync.... do you know how to solve it?

xorg.conf:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "TexturedVideoSync" "on"
	Option	    "Capabilities" "0x00000800"
	BusID       "PCI:1:0:0"
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

---

