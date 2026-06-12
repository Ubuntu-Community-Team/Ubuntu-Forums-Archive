---
title: "problem: Dualview with IBM T22: does not connect to second desktop"
date: 2008-09-12
forum: Hardware
---

### Post by Der Jens on 2008-09-12
Hey guys,
I try to expand my desktop to dualview, I use a IBM T22 and a second desktop (Fujitsu Siemens Scaleoview L17-3). My VGA controler is a 86C270-294 Savage/IX-MV (Thinkpad T20/T22) from IBM (savage 3). I've looked up different forum such as [www.ubuntuusers.de;](www.ubuntuusers.de;) [http://www.thinkwiki.org/wiki/Category:T22](http://www.thinkwiki.org/wiki/Category:T22) but I couldn't find the answer to my problem.
My xconf.org:

[I][I][COLOR="Navy"]
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection
[/COLOR][/I][/I]


Maybe I have to change something in "device" but I started just two days ago so I'm a bit afraid of changing important things by myself.

I hope this post got in the right category.
Thanks for the help
Der Jens

---

