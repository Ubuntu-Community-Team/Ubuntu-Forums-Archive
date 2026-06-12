---
title: "Console problems..."
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by kumpooterjooser on 2005-05-29
I had the issue of fuzzy/shaky fullscreen display in some movies...

followed instructions on the link [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) 

1.     sudo apt-get install nvidia-glx
2.     sudo nvidia-glx-config enable

the fuzzy/shaky problem in fullscreen mode went away...
But now I landed in another mess...

whenever I want to go into console by pressing ctrl-alt-f1, I am taken to a blank 
screen filled with random green squares....the same happens if i try to restart X 
(ctrl-alt-backspace)

graphic card: nvidia GeForce FX Go5200...
screen resolution: 1280*800@60
laptop: Toshiba M35-S359

Would highly appreciate help/suggestions...


Thanks

kumpooterjooser

**********************************
here is the relevant part of xorg.conf...

```
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
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

---

