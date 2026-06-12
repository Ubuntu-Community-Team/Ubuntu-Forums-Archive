---
title: "A new Acer H233H monitor and dual boot"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Canuck.old on 2009-07-03
Hello one and all!
I bought a Acer H233H 23" monitor and a Gforce 9800GT video card. I
would like to assemble this into a dual head machine running:
Release 8.04 (hardy)
Kernel Linux 2.6.24-24-generic
I have got the monitor to work single head but dual head escapes me.
Can anybody out there tell me what is wrong with this:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"LHS Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Device"
	Identifier	"RHS Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Acer H233H Monitor"
	Option		"DPMS"
	HorizSync	54.2 - 83.8
	VertRefresh	49 - 75
EndSection

Section "Monitor"
	Identifier	"ViewSonic P95f+ Monitor"
	VendorName	"ViewSonic"
	ModelName	"P95f+"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"LHS Screen"
	Monitor		"Acer H233H Monitor"
	Device		"LHS Device"
	Defaultdepth	24
	SubSection	"Display"
		Modes	"1920x1080" "1680x1050" "1600x900" "1440x900" "1365x768" "1280x720" "852x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"RHS Screen"
	Monitor		"ViewSonic P95f+ Monitor"
	Device		"RHS Device"
	Defaultdepth	24
	SubSection	"Display"
		Modes	"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Dual Head Layout"
        Screen          0 "LHS Screen" 0 0
        Screen          1 "RHS Screen" RightOf "LHS Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "ServerFlags"
 	Option      "Xinerama"  "ON"
EndSection

Thank you for your time!

dkr

---

