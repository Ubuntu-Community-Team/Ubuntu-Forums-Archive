---
title: "Dual Screen"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by c0mm0n on 2005-08-12
Hello,

I want to be able to use my two monitors. I've surfed all over the internet to find the right solution.
I have an ATI Radeon 9600 Card and have attached two monitors to this card.
The problem is that the two monitors show the same thing, but my mouse moves between the two monitors. I have included my xorg.conf, can someone please tell me what I'm doing wrong ? When I want to move a task to the other monitor, I see my mouse entering the other monitor, but not the task.


This is my xorg.conf, I've only copied the sections that are in use for the monitors

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)(secondary)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
    	Option 		"DDCMode" "on"
    	Option 		"DPMS"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"COMPAQ V75"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"RIGHT SCREEN"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)(secondary)"
	Monitor		"COMPAQ V75"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
    	Option 		"DDCMode" "on"
    	Option 		"DPMS"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"DELL M570"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"LEFT SCREEN"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"DELL M570"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual Screen"
	Screen 0	"LEFT SCREEN"	0	0
	Screen 1	"RIGHT SCREEN" RightOf "LEFT SCREEN"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "on"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by laue on 2005-08-12
hope this helps: [http://www.linuxquestions.org/questions/history/333550](http://www.linuxquestions.org/questions/history/333550)

---

