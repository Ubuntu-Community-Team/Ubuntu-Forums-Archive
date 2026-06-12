---
title: "lcd and crt twinview for nvidia help"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by martinez9049 on 2005-04-15
Hi, I have a nvidia fx 5500 and what im trying to do is to set up an lcd as my primary display and a crt as my secondary. i've edited the xorg.conf file and im getting twinview the only problem being that my crt is the primary display. also, is it possible to have different resolutions on the monitors?

here's my xorgconfig file

---

### Post by martinez9049 on 2005-04-15
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"NvAGP"			"3"
	
EndSection

Section "Monitor"
	Identifier	"Samsung 173P"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"Samsung 173P"
	DefaultDepth	24
	Option		"TwinView"			"true"
	Option		"SecondMonitorHorizSync"	"30-70"
	Option		"SecondMonitorVertRefresh"	"50-120"
	Option		"MetaModes"	"1280x1024, 1280x1024; 1280x1024, 1280x1024;"
	Option		"TwinViewOrientation"	"RightOf"
#	Option		"ConnectedMonitor"	"DFP-0, CRT-1"


	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


sorry for posting the file like this....don't know how to make it in a scrollable window

---

