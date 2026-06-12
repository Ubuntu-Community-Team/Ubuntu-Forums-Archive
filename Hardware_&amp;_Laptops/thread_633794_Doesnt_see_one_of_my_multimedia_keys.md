---
title: "Doesnt see one of my multimedia keys"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by Nu7a on 2007-12-06
Im on Gutsy on a Asus C90s, all my multimedia keys were seen perfectly except one for some reason. Its my touchpad disable key, When I do set keyboard hotkeys and try to set one with it, nothing happens, its like it doesnt see it at all. I've been searching for about 2 days and Ive seen ppls problems where they dont have any keys working. Any help would be greatly appreciated.

Thanks, Tyler

---

### Post by NateMan on 2007-12-15
There is an issue with the way the xorg.conf is written for the button to work. here is the part of my xorg.conf for the synaptics touchpad. just copy this over the old synaptics touchpad section.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"	"on"
EndSection


Enjoy.

---

### Post by Nu7a on 2007-12-29
omg, worked perfectly, thanks allot

---

