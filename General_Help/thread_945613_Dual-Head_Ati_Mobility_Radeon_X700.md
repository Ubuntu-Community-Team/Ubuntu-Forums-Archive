---
title: "Dual-Head Ati Mobility Radeon X700"
date: 2008-10-12
forum: General Help
---

### Post by Geoffrey Juan on 2008-10-12
Hi,

I'm trying to set up a dual head on my laptop :
Acer Aspire 5022WLMI (AMD Turion 64) with ATI X700

I have been trying a lot of things and the only thing i achieved is to get confused. With the drivers that come with kubuntu (Hardy), i can duplicate the screen but i cannot choose the resolutions. So i tried fglrx and some modifications in the xorg.conf file (through nano because i can't edit it with sudo kate or sudo kwrite !!). With this driver, the system tray automatically doesn't work and none of what i found worked for the dual head. So far, it just stops when I reboot : i enter my password and then the loading stops when the KDE icon appears. But it boots normally when the second screen (Samsung 22") is not plugged.

Could anyone help me please, i don't have much experience... 
Thank you in advance.

Here is my xorg.conf file :
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Synaptics Touchpad"
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
	Option	    "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "DesktopSetup" "horizontal"
	Option      "PairModes" "1280x1024+1680x1050"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
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

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by Geoffrey Juan on 2008-10-12
Hi again,

I have also tried what follows here by commenting and uncommenting... :
Section "Device"
	Identifier	"ATI Technologies Inc M24 1P [Radeon Mobility X700]"
	Driver		"ati"
#	Option		"MonitorLayout"		"CRT, TMDS"
#	Option		"PanelSize"		"1680x1050"
#	Option	        "DesktopSetup" "horizontal"
#	Option          "PairModes" "1280x1024+1680x1050"
	Option 		"Metamodes" "1280x1024-1680x1050 800x600-800x600"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Subsection "Display"
		Virtual 2960 1074
        EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Please, any clue?
Thanks in advance.

---

### Post by Geoffrey Juan on 2008-10-13
Hi,

Good news : i did it! Everything is working perfectly now. The solution was xrandr and following any tutorial on how to set it up that can be found in the online ubuntu doc. :D

by!

---

### Post by lexe-cc on 2009-03-23
i'm having the same problem :)
after searching for the ubuntu documentation, i havent found anything.
Can you post a link of the doc you used?

thanks in advance!

---

