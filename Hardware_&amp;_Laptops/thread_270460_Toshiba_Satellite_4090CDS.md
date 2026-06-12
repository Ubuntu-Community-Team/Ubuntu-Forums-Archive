---
title: "Toshiba Satellite 4090CDS"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by thebananaking on 2006-10-03
I have installed Ubuntu to a Toshiba 4090CDS laptop with only one problem, the display. There is a horizontal band of "interference" across the bottom of the screen. This band is about 15mm thick and is about 10mm from the bottom of the screen. If I plug an external monitor into the laptop and activate that display only, there is no problem at all. This laptop has been able to run the various versions of windows without trouble. Can anyone help? :confused:

---

### Post by mbernardi on 2006-10-27
> **thebananaking said:**
> I have installed Ubuntu to a Toshiba 4090CDS laptop with only one problem, the display. There is a horizontal band of "interference" across the bottom of the screen. This band is about 15mm thick and is about 10mm from the bottom of the screen. If I plug an external monitor into the laptop and activate that display only, there is no problem at all. This laptop has been able to run the various versions of windows without trouble. Can anyone help? :confused:

I have the same problem having just installed Xubuntu 6.10 (Edgy) The problem **only** occurs at the maximum resolution 800x600@56. If the lower res of 640x480@60 is used the same part of the screen is fine, but the display has a black border.
Suggestions?

---

### Post by bflat on 2007-09-02
The problem was solved for me after hacking from a XF86file proposed in a very good site on Linux on laptops. Checking this xorg.conf, and applying the significant changes should work. Feisty Fawn Xubuntu with 128 mg ram makes a fair and swinging Satellite 4090CDS even before a monolithic custom kernel compilation.


> 
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
#	Driver		"vesa"
	BusID		"PCI:00:04:0"
        VideoRam	2048
	Option		"noaccel"
EndSection

Section "Monitor"
	Identifier	"Toshiba LCD"
	Option		"DPMS"
	HorizSync	31.5-53.7
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Toshiba LCD"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"800x600"
#	EndSubSection
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
EndSection

---

