---
title: "widescreen 1024x800 not available"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by chris rowan on 2007-09-09
just installed 7.04 on my dell 5400. I can only get 1024x768 (not 1024x800) resolution so the desktop image is stretched. 

Here is the relevant section of xorg.conf


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


Help would be much appreciated!

---

### Post by El Rogueo on 2007-09-09
> **chris rowan said:**
>  I can only get 1024x768 (not 1024x800) resolution so the desktop image is stretched. 

Here is the relevant section of xorg.conf

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"


Are you using a restricted driver, or just a generic that ubuntu pulled up?

That said, are you sure you have the right drivers for the job? What kind of integrated graphics do you have, and does that match your xorg.conf readout?

according to [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html) it looks like your driver should be called "945GM", not "i810". I'd try to download the correct driver (might be in the restricted drivers part of Synaptic) and see if that helped first, maybe then go from there.

---

### Post by chris rowan on 2007-09-09
Thanks for prompt reply.

The driver is presumably one dragged from nowhere by ubuntu, as I did nothing to install graphics drivers! The entry in my hardware list  matches the one in xorg.conf so I guess I do need that 945gm driver. I'll have a look for it and see how I go, posting back here if I struggle ...

Thanks again

---

