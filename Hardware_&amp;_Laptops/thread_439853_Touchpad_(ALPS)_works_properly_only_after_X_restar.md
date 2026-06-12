---
title: "Touchpad (ALPS) works properly only after X restart (Ctrl-Alt-Backspace)"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by olegff on 2007-05-11
Hi,
I have a strange problem with my Xubuntu 6.10 on FS laptop with Alps touchpad:

When I start X-windows normally my xorg.conf settings for touchpad are not implemened (Option		"MaxTapTime"		"0" ) but then I press Ctlr-Alt-Backspace and after restart everthing works just fine - no tapping as I wanted!

Symptoms:
                                                               
synclient -m 100         Normal start  - no output;    After restart - normal output
touchpad sets to dev (auto-dev)      Normal start  - /dev/input/event3; After restart - /dev/input/event4

my xorg.conf:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
        Option          "SHMConfig"		"true"
EndSection

---

### Post by olegff on 2007-05-14
solved by upgrading to version 7.04  :)

---

