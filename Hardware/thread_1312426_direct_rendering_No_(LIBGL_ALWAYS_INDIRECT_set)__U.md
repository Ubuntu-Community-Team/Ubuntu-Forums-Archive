---
title: "direct rendering: No (LIBGL_ALWAYS_INDIRECT set) / Ubuntu 9.10"
date: 2009-11-03
forum: Hardware
---

### Post by naster4o on 2009-11-03
First, i'm sorry for my bad english.

I have ubuntu 9.10, with fglrx 8.66.10 (manual install, becose when i try to "active" from ubuntu tools my system freez), and HD4850.
Everything is okey, BUT when i type in console glxinfo | grep direct i see this thing: direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
If i type it from root direct rendering is set on YES
> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "AGP:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection

Section "DRI"
	Group        "users"
	Mode         0666
EndSection

---

### Post by naster4o on 2009-11-03
when i type unset LIBGL_ALWAYS_INDIRECT, direct rendering write YES but if i close the terminal and start it again direct rendering again says NO ?

---

