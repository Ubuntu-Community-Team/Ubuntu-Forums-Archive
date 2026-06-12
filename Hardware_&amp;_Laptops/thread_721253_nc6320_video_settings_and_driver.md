---
title: "nc6320 video settings and driver????"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by smoothcne on 2008-03-11
Hi folks, need ur help please.
I'm running an HP/Compaq nc6320 with Gutsy 7.10.
For some reason, and I'm absolutely not an expert on Linux, I can't get my resolution above 1024x768. I'm running the standard Intel 945 driver so it will work but every time I try to modify my settings, my screen goes blank on boot up and just hangs, I cant switch out to term or do anything short of powering it off.

Has anybody had this same problem and what did you do to fix it so you can see 1400x1050 Res?

Maybe a copy of your xorg.conf file would also help.

Here is a sample of my current file:


Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

---

