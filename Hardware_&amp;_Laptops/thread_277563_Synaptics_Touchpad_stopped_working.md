---
title: "Synaptics Touchpad stopped working"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by klato on 2006-10-14
Update: rebooted, working again :) 
Update2: stopped working again :(

My Synaptics touchpad has stopped working since yesterday.

I have a USB mouse plugged in, and that works ok.

Here's my xorg.conf file:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection


What could have happened?  The reason I'm asking is because I have an external HD and would like to be able to unmount it (I've only 1 USB port...)

---

### Post by linduxed on 2007-12-29
If you're lucky, this is a nobrainer; it sounds a lot like my problem i had earlier:

[http://www.daniweb.com/forums/thread25588.html](http://www.daniweb.com/forums/thread25588.html)

---

