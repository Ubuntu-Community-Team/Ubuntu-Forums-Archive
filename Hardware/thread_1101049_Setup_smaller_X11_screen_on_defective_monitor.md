---
title: "Setup smaller X11 screen on defective monitor"
date: 2009-03-19
forum: Hardware
---

### Post by mkwa on 2009-03-19
I have a 1920x1200 LCD monitor which has defective driver chip or flexible ribbon for the top 200 lines. So to avoid nonworking lines, I would like to set up my X11 screen with smaller size 1920x1000, and at vertical offset +200. How do I do it in xorg.conf? My current xorg.conf is a very simple:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

