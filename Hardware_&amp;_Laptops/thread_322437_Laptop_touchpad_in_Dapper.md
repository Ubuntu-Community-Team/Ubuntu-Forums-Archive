---
title: "Laptop touchpad in Dapper"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by saxsux on 2006-12-20
Under Windows, I can run my finger down the right side of the touchpad to scroll vertically, but in Ubuntu it doesn't work.
I've tried adding:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```
to xorg.conf, but it's had no effect.

How could I make the touchpad scroll vertically?

Thanks :D

---

### Post by spier on 2006-12-20
This works (most the time :/ -still have issues after awake)

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"

	Option		"MaxTapTime"	"180"
	Option		"MaxTapMove"	"150"

	Option		"VertScrollDelta" "10"
	Option		"HorizScrollDelta"	"10"

	Option 		"LeftEdge" 	"120"
	Option 		"RightEdge" 	"910"
	Option 		"TopEdge" 	"120"
	Option 		"BottomEdge" 	"650"
	
	Option          "EmulateMidButtonTime"  "75"	
	Option          "LBCornerButton"        "2" # emulate middle button at LeftBottomCorner	
	Option		"SHMConfig"	"on"
EndSection


The VertScrollDelta option should do the trick. Other configurations are personal


HTH

---

### Post by saxsux on 2006-12-21
That doesn't seem to have worked...

I tried commenting out the entry for "Configured Mouse" (I thought they might be conflicting, or something), and X wouldn't start.... :-(

But yeah, adding that code hasn't helped.

---

