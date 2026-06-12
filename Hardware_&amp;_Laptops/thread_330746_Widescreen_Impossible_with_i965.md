---
title: "Widescreen Impossible with i965?"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by gamx on 2007-01-03
My PC has an ASUS P5B-VM motherboard that has the intel 965 chip. Is it possible with this chip to have a widescreen monitor working? All the howto's I have found rely on the 915resolution package, which does not support this intel chip. Does it? Is there another way to do it?
To make things worse my (new) 19inch widescreen monitor doesn't seem to exist. I am not kidding. It is an ASUS VW192S, and I haven't found information anywhere. I only know it is real because I am staring at it at the moment. There is no way I can find information anywhere about refresh rates and so on.](*,) 
Right now, I can only get a 1024x768 resolution, so as you might expect the image is awful. By going to System>Preferences>Screen Resolution, there is not a higher one (even with a normal screen format) being offered. For what it is worth, I am posting my (non-working) xorg.conf file.
I would really appreciate any help. 

Section "Device"
	Identifier	"Intel i965"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Asus VW192s"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i965"
	Monitor		"Asus VW192s"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by torekiki on 2007-01-24
same problem!!!:(

---

### Post by alamue on 2007-01-27
try 

Section "Device"
Identifier "Intel i965"
Driver "i965"
BusID "PCI:0:2:0"
Option "UseFBDev" "true"
EndSection

i am using edgy and there is a i965.so

---

