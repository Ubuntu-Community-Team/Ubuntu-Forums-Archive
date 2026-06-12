---
title: "wrong primary monitor plz help"
date: 2011-11-20
forum: Hardware
---

### Post by inmate#001 on 2011-11-20
Here is my xorg.conf

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen         "amdcccle-Screen[1]-1" 1360 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1360x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

I want to make the CRT the primary display what do I need to Change to make that happen, I have tried changing -# in the identifier row in the device sections and that works to change the primary monitor but its on the wrong side (The CRT is left of the TV). Then I Tried switching the monitors position in CCC and then changing xorg.conf, but after I rebooted and the mouse would not leave the TV in any direction. 
any ideas

---

### Post by trenul on 2012-11-30
I suspect this happens because the HDMI/DFP port on your video card is activated first, and the VGA/CRT got less priority, so the AMD utility will define the devices in that order and also the screens associated with those devices. You will just need to change your Layout section so that the screen on the device you want will be the leftmost (that screen is receiving the desktop). Remember to change the horizontal coordinate value aswell if your 2 screens got different resolutions.

Solution would be:

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-1" 0 0
    Screen         "amdcccle-Screen[1]-0" 1440 0
EndSection

PS always backup your working (former) xorg.conf before editing it ! That way you can restore it from command line if something goes wrong.

PPS I also added Option "Primary" "True" to the relevant Monitor section but I suspect that option is obsolete nowadays.

---

