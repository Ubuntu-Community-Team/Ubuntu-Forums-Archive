---
title: "Is my vid card's driver installed correctly?"
date: 2008-06-12
forum: Hardware
---

### Post by finalhit on 2008-06-12
I have ATI IGP 320M and I've been doing some searches, and not quite sure if my video card has been set up properly or not. This is a fresh CD installation of Hardy Heron, and I haven't done much modification other than installing drivers for my brodcom wifi card.

Anyway, I run "glxinfo" and I got "Direct Rendering : Yes" so I figured I'm set up for 3D acceleration. However, when I tried enabling System > Appearance > Visual Effects, i get "Desktop Effects cannot be enabled" error.

I also noticed that my xorg.conf doesn't have any explicit references to my video card.

> Section "InputDevice"
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
	Option		"UseFBDev"		"true"
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

Can anyone point me to the right direction? I would really like to get compiz fusion to work if possible. 

If not, please let me know as well, to save me a little trouble.

UPDATE: i found something called glxgears, and it seems to be working fine for me


thanks

---

