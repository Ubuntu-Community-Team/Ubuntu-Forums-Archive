---
title: "Can't Activate Visual Effects (Dual Monitors)"
date: 2008-09-02
forum: General Help
---

### Post by shipitkthx on 2008-09-02
Just installed Ubuntu last week so pretty much a noob. I have 2 Dell 2007FPs running off a ATI Radeon x300se card, both at 1600x1200. When I try to activate advanced visual effects I get a popup saying "Desktop Effects Could Not Be Enabled" I've tried for searching but havent found a method to fix this. Here is the output of entering "compiz" on the terminal:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 06:00.0 0300: 1002:5b60 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3200x1200) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 


And here is my Xorg.conf:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
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
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:6:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:6:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768"
	EndSubSection
EndSection


Any ideas on how to fix this?

---

