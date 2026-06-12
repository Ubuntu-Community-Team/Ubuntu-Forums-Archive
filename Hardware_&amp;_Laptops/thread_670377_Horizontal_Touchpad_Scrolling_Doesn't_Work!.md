---
title: "Horizontal Touchpad Scrolling Doesn't Work!"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by nate_2001 on 2008-01-17
When I use synclient HorizEdgeScroll=1 in a terminal, horizontal scrolling begins to work immediately.  I tried to edit my xorg.conf to make this happen automatically when I start the system, but nothing seems to make it work.  I hope someone can help me with the configuration!

thanks!
> 

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"BottomEdge" "4000"
	Option		"HorizEdgeScroll" "true"
	Option		"SHMConfig"	"True"

EndSection

---

### Post by nate_2001 on 2008-01-18
Figured out the problem:


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"BottomEdge" "4000"
	Option		"HorizEdgeScroll" "1"
	Option		"HorizScrollDelta" "100"
	Option		"SHMConfig"	"True"

EndSection


Needed to add the "HorizScrollDelta" option!

---

