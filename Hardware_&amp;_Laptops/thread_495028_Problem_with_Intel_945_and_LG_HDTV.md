---
title: "Problem with Intel 945 and LG HDTV"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by ayahuazca on 2007-07-07
Hello!

I get perfect 1280x800 resolution on the laptop using the 810 driver but when I change to 1024x768 (which is the native resolution for the TV (which is a LGPC1RR)) the picture becomes all blurry and doesn't fit the screen on either the laptop nor the TV even though it should according to the TVs specs.

I've previously tried the "Intel" driver instead of "810" which gave me right resolution for the TV but I was unable to choose 1280x800 for the laptop even when the TV wasn't connected. I 

I just made a fresh install of Feisty 7.04 and xorg.conf shows the following:
```

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

I've been trying to edit the xorg.conf over the last couple of days without any real results using both the 810 and Intel driver, but then again I'm a complete Ubuntu newbie so I'd really appreciate if someone could guide me along the way.

I'm using a HP nx7400 laptop and connect to the TV through a VGA cable, Intel 945 card and 810 driver.

Any ideas? Thanks!

---

