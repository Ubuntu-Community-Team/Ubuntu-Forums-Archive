---
title: "VMWare Ubuntu Guest with Synaptics Touchpad"
date: 2008-09-26
forum: General Help
---

### Post by OldJohnRobertson on 2008-09-26
Hi,

I'm wondering if anyone has succeeded in getting scrolling working with a Synaptics touchpad through VMware?

Basically, I'm running Windows Vista Home Basic as a host and Ubuntu 8.04 as a guest. Here is the relevant part of my xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"Buttons"	"5"
	Option		"ZAxisMapping"	"4 5"
EndSection

This configuration works fine if I'm running an external mouse, but this configuration does not work if I use the built-in Synaptics touchpad. I'm assuming it's because "edge scrolling" on a touchpad isn't the same as having an actual wheel.

Anyway, does anyone have any ideas how I can get the edge scrolling on the touchpad to work?

Any info is appreciated! Thanks in advance.

---

### Post by OldJohnRobertson on 2008-09-27
Bump. Any takers? :)

---

### Post by OldJohnRobertson on 2008-09-27
Anyone? :)

---

### Post by OldJohnRobertson on 2008-09-28
Sunday bump. :)

---

