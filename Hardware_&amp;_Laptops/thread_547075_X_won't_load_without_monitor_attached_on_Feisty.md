---
title: "X won't load without monitor attached on Feisty"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by PaleDavid on 2007-09-09
I've been running Feisty happily for a month or so on my Packard Bell EasyNote laptop. Two weeks ago, I attached my external monitor (an LG widescreen) and couldn't get its resolution working. After some (probably unwise) mucking about, and one restored xorg.conf, I got multiple resolutions working. 

However, I've finally unhooked the monitor, and now X won't load until the monitor is attached. It freezes before Nautilus starts up, and keeps crashing and returning to the username and password prompt. If I attach the monitor it loads fine. Basically, my laptop now insists on being a desktop. 

The odd thing is that even if the monitor is switched off but attached, X loads okay. I've tried restoring my old xorg.conf to no avail. Numerous restarts and a lot of searching forums later, I'm totally stuck. Can anyone help? 

Here are the relevant lines in my current xorg.conf:


[INDENT]Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection[/INDENT]

---

