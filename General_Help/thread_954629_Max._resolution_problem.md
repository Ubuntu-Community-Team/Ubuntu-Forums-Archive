---
title: "Max. resolution problem"
date: 2008-10-21
forum: General Help
---

### Post by Kono on 2008-10-21
Hello there :)

I'm having weird problems with my maximum resolution settings. I have a monitor capable of a res. of 1920x1600. It worked fine for a while having that resolution and then out of a sudden, the maximum resolution went down to 1600x1200. Then sometimes, after a restart, it's back again at 1920x1600, after another one or two restarts its again back at 1600x1200. I can see absolutely no pattern in this. I even reinstalled Ubuntu after formatting my disc, and the problem is still there. I'm using the fglrx driver for a HD4850 card, however I don't think the fglrx driver is causing this, because the max. resolution even changes randomly before I installed the driver. Also, I don't think the monitor is causing this, since I have this monitor *twice* at two different locations and and the problem started on both at the same time, although they were bought at different stores/points in time. 

My /etc/X11/xorg.conf file does not change between system starts where it works and where it does not. I checked that with 'diff'. Also, I tried to add Modes "1920x1600" in the SubSection "Display", which did not work any better than without it.

Any help what could cause this is *HIGHLY* appreciated, because the monitor does not give me a sharp image unless it's at a resolution of 1920x1600. I'm using Ubuntu stable 8.04 (alternate installer).

Here's my xorg.conf:

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
	Option	    "XkbLayout" "de"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
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

