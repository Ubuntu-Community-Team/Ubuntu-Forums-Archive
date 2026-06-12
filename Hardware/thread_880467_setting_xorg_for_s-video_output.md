---
title: "setting xorg for s-video output"
date: 2008-08-05
forum: Hardware
---

### Post by jcdavo on 2008-08-05
hey everyone...

I have been trying to set up my lap to be able to use s-video to de tv with no luck so far... i have an hp dv2125la with i945 chipset, i'm posting my xorg.config any help would be great

thanks

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
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

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Daelyn on 2008-08-06
According to your laptop spec there is a Intel GMA950 gfx card in it.

If you look on this page, there is a explendid description in how to configure dual screens/switch output on Intel cards.

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by jcdavo on 2008-08-06
thanks Daelyn, i managed to get vga output working but still no svideo output... i still cant get that to work... i'll post my new xorg.config for any help

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
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

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
        # ADD THIS IF YOUR LAPTOP DOES NOT HAVE A TV CONNECTOR or DOCKING STATION 
	Option		"UseFBDev"     "true"
	Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "VGA"
        Option "Ignore" "false"
EndSection

Section "Monitor"
        Identifier      "LVCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option  "Ignore" "false"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"LVCD"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

