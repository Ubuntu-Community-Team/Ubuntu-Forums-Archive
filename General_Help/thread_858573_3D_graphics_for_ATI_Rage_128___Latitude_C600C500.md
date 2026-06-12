---
title: "3D graphics for ATI Rage 128 ???  Latitude C600/C500"
date: 2008-07-13
forum: General Help
---

### Post by bernasal on 2008-07-13
I have ubuntustudio installed on an old dell latitude C600/C500.  It has an ATI rage 128 video card and I can't the 3d graphics to work.  Everything I have found has led my xorg.conf file to look like this (see below).  Any ideas on how to get it working?

I also downloaded the package for envy as a post mentioned it offering help on this issue, but when i run "open application" and type it in it doesn't run??  I have looked over synaptic and believe i have everything i need, but I am new to linux and at a loss... help?

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Module"
	Load "dbe"
	Load "dri"
	Load "glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Rage 128"
	Driver		"r128"
	BusID		"PCI:1:0:0"	
	Screen		0
	Vendorname 	"ATI"
	Option 		"MergedFB" "off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

