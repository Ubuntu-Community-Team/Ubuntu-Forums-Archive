---
title: "Dell 630, Intel 965GM graphics, 3D"
date: 2008-08-19
forum: Hardware
---

### Post by ssls6 on 2008-08-19
I put ubuntu 8.04.1 on my dell 630.  I'm using the AMD64 bit version.  I can't seem to figure out how to get 3D working.  I'm not interested in running the enhanced desktop effects but I do want google earth and other programs to use 3D.

I had 3D working on this computer using suse SLED with the i810 driver but could not use compiz without weird things happening.

My xorg.conf looks like this.
*************************************************
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
***************************************************

Not a lot of information there.  Is there an app that allows a person to select the video driver?  I can't tell what ubuntu is using.

thanks,
richard

---

### Post by ssls6 on 2008-08-19
Is there a way to turn 3D on in the xorg.conf?

---

