---
title: "[Xinerama] SecondMonitor on standby"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by Lifetech on 2005-08-20
I'm trying to get my second monitor (a Fujitsu 772) to work under Ubuntu. The problem is, i did everything that i needed to do in my xorg.conf file (maybe i forgot something, but i don't know what). 

At first my xserver wouldn't start because i made a few mistakes in my xorg.conf file. Now my Xserver starts but only on one screen and my second monitor goes on standby (flashing orange light). 

If I go in Ubuntu without a Xserver my secondmonitor doesn't go on standby but also doesn't go on. It just shows a orange light instead of a yellow one.

If someone knows what the problem is, please help me out!

Here is my xorg.conf file:

```

Section "Device"
	Identifier	"Screen0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"hp L1730"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"Fujitsu"
	Option		"DPMS"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Screen0"
	Monitor		"hp L1730"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Screen1"
	Monitor		"Fujitsu"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section		"Device"
	Identifier	"Screen1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"	
EndSection

Section "ServerLayout"
	Identifier	"dual"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen		"Screen0"
	Screen		"Screen1" RightOf "screen0"
EndSection

Section "ServerFlags"
	Option	"Xinerama"
EndSection	
Section "DRI"
	Mode	0666
EndSection

```

My videocard is a Leadtek 6800LE.
And i know my second monitor is broken because it works in Windows

---

