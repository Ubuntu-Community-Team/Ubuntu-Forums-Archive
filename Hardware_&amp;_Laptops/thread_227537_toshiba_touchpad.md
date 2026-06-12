---
title: "toshiba touchpad"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by cope on 2006-08-01
Hey, 

I've installed ubuntu on a toshiba a100, i've got my touchpad working, the scroll works, but in windows i can assign zones, so if i double tap the bottom right hand corner, it middle clicks, etc. etc. 

is there anything like this available for ubuntu yet? I'm sick of right click open in the new tab for links in firefox...

---

### Post by spier on 2006-08-01
All you need is edit /etc/X11/xorg.conf. The middle button thing you get adding this line

```
	Option          "RBCornerButton"        "2" # emulate middle button at RightBottomCorner
```

to Synaptics device section, i.e.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"

	Option	"MaxTapTime"	"180"
	Option	"MaxTapMove"	"150"
	Option	"VertScrollDelta" "10"
	Option	"HorizScrollDelta"	"10"
	Option          "EmulateMidButtonTime"  "75"	
	Option          "RBCornerButton"        "2" # emulate middle button at RightBottomCorner	
	Option		"SHMConfig"	"on"

```

A better explanation and a good reference of possible options you get in this[gentoo-wiki page]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad").

HTH,

---

### Post by cope on 2006-08-05
that did the trick, thanks!

---

