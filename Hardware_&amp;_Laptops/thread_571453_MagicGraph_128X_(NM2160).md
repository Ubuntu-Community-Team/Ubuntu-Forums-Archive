---
title: "MagicGraph 128X (NM2160)"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by K5KS on 2007-10-09
Installed Ubuntu on Gataway 2500 Solo PII 266.  Everything works well except the display is very fuzzy.  I have read many post on Drivers/ and video cards and all of those containing Neomagic etc...

The Laptop TFT is only up to 800x600 which is ok if it was not so fuzzy.  I have read post about the XFree86 driver for this chip set.

1. how do I know if I have that driver
2. how do I get/install if I don't
3. is there more detailed setting that I need to adjust to clear up the fuzzy display.

---

### Post by K5KS on 2007-10-09
All right...did not get any response to that....doing more digging...the xorg.conf is pasted below.  the max screen res is 800x600 for the TFT laptop monitor (the card can support 1024x768 on external monitor) I am trying to fix the fuzzy screen (text and graphic) is there a setting I need to change here.  Thanks to anyone that can lend a hand on this one.
> 
Section "Device"
	Identifier	"Neomagic Corporation NM2160 [MagicGraph 128XD]"
	Driver		"neomagic"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Neomagic Corporation NM2160 [MagicGraph 128XD]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

---

