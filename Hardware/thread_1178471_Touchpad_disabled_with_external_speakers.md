---
title: "Touchpad disabled with external speakers"
date: 2009-06-04
forum: Hardware
---

### Post by Satrianix on 2009-06-04
Hi, this is my first post.
Ok the problem is this, I have an Acer Laptop with ubuntu 8.04 and everything works really fine, but, when i plug external speakers on the headphone jack, the touchpad beggins to work weirdly or it's disabled at all.
If i unplug the speakers it works back again, and if i plug it back it fails again and so on.

The problem only appears with external speakers because with actual headphones it remains working fine.

This is my Xorg.conf section for the touchpad


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


Any advise or help would be appreciated.

---

