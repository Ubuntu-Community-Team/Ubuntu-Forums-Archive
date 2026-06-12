---
title: "How to make the LCD show 24 bits colors"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by luispa on 2007-07-31
Hi,

I recently bought a ViewSonic VA1703wb. I can't find the way to make it show certain colors like light grays. I'm using an nVidia Riva TNT2 Model 64. This a fragment of my xorg.conf:
Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"VA1703wSERIE"
	Gamma	0.6
	Option		"DPMS"
	Horizsync	24	-	70
	Vertrefresh	50	-	75
  modeline  "1440x900" 106.5 1440 1520 1672 1904 900 903 909 934
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"VA1703wSERIE"
	Defaultdepth	16
	Option		"DigitalVibrance"	"50"
	SubSection "Display"
		Depth	1
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	32
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

I'll really appreciate any kind of help.

Thank you in advance.

Luis Pablo

---

### Post by NickArgyle on 2007-07-31
Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
Monitor "VA1703wSERIE"
Defaultdepth 16

change 16 to 24 and restart X

---

