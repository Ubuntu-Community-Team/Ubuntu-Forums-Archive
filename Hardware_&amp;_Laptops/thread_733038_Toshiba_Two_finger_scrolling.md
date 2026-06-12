---
title: "Toshiba Two finger scrolling"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by avdzm on 2008-03-23
Hey All,

I have a Toshiba A200-10X with ubuntu 7.10 and i would like to get the two finger scrolling to work on my touch pad.

Has anyone with a toshiba got it working?

I have tried adding and disabling edge scrolling
```

Option		"HorizEdgeScroll"	"0"
Option		"VertEdgeScroll"	"0"
Option          "VertTwoFingerScroll"   "1"
Option          "HorizTwoFingerScroll"  "1"

```

and nothing...

I was wondering maybe i should install something or i am using the wrong driver.

any help would be greatly appreciated.

this is my xorg touch pad section
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	option		"HorizScrollDelta" "0"
	Option 		"CorePointer"
EndSection

```

---

### Post by avdzm on 2008-03-24
bump

---

