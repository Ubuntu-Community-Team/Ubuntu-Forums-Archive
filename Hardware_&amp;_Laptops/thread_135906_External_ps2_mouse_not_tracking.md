---
title: "External ps/2 mouse not tracking"
date: 2006-02-24
forum: Hardware &amp; Laptops
---

### Post by SodomizedPeanut on 2006-02-24
I'm a newcomer to linux, running 5.10 on a HP Omnibook XE2. The touchpad works like a dream, but my external ps/2 mouse refuses to work at all. The buttons work intermittently, when clicked, but otherwise there is no response whatsoever.

The relevant section of my xorg.conf

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"

Any help would be appreciated.

---

