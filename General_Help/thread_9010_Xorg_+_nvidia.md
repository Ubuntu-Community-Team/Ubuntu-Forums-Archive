---
title: "Xorg + nvidia"
date: 2004-12-23
forum: General Help
---

### Post by 17th on 2004-12-23
hi, I'm having trouble with Xorg + nvidia on Hoary.

It was everything okay running good but 3 boot later resolution got messy and now it just show only "640x480" resolution.

I've checked /etc/X11/Xorg.conf but it seems X is ignoring this file.

I'm stuck, any ideas?

My nvidia card is: "NVIDIA Corporation NV15DDR [GeForce2 Ti]"
My /etc/X11/Xorg.conf is:
```

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection
Section "Device"
	Identifier	"NVIDIA Corporation NV15DDR [GeForce2 Ti]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "NoLogo"
EndSection

Section "Monitor"
	Identifier	"FLATRON 775F"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV15DDR [GeForce2 Ti]"
	Monitor		"FLATRON 775F"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

```

---

### Post by diebels on 2004-12-23
mv Xorg.conf xorg.conf

---

### Post by p!=f on 2004-12-23
And remove GLcore and dri entries in the modules section.

---

### Post by jbh on 2005-01-01
Your monitor section is missing the refresh rates too.

It should look something like this:

Section "Monitor"
	Identifier	"AOC 9Klr"
	HorizSync	30-95
	VertRefresh	50-160
	Option		"DPMS"
EndSection


But use whatever HorizSync and VertRefresh values from your actual monitor documentation.

---

