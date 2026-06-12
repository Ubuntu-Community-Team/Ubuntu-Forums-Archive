---
title: "driver for main intel 946gz"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by thanhthanh on 2007-07-10
my MB use INTEL GMA 3000 graphic card [http://en.wikipedia.org/wiki/Intel_graphics_media_accelerator](http://en.wikipedia.org/wiki/Intel_graphics_media_accelerator)
i dont know which driver should I use. and where cani get it ?
please help me!

---

### Post by starscalling on 2007-08-05
hey i have the d946gzis board - i use either the intel or i810 driver - should be included there already ;P

sudo dpkg-reconfigure xserver-xorg

or even better:
gksu gedit /etc/X11/xorg.conf

go down to the device section and change a bit here's how mine looks:

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-92
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1856x1392" "1792x1344" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

