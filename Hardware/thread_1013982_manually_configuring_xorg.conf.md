---
title: "manually configuring xorg.conf"
date: 2008-12-17
forum: Hardware
---

### Post by AuronGrande on 2008-12-17
I cannot alter my screens refresh rate using Gnomes Screen Resolution program in the system menu because my screen isn't being detected.

What do I do to configure xorg.conf so that my screen is more comfortable to be viewed?

the current details in my xorg.conf file is as follows.

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

bear in mind, I am new, and know next to nothing of using Terminal which I know is required to make the alterations.

My monitor is as follows depicted by Catalyst Control Centre through fglrx;

Monitor - Xerox XM3-19w
Maximum resolution - 1440x1024
Maximum refresh rate - 75hz

I need the screen at 1440x900 because it's a widescreen monitor, and the refresh rate at 75hz. Even though I can alter the resolution which is currently at 1440x900, I cannot alter the refresh rate which is fixed at 60hz.

---

