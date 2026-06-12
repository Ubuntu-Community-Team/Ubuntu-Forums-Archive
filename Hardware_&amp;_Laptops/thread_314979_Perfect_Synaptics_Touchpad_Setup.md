---
title: "Perfect Synaptics Touchpad Setup"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by EPOX123 on 2006-12-08
**Taken from the following site:**
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

I used this set up and seamed so perfect, so I thought I would share it with you guys.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"LeftEdge"		"1700"
	Option		"RightEdge"		"5300"
	Option		"TopEdge"		"1700"
	Option		"BottomEdge"		"4200"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"0"
	Option		"MaxTapMove"		"0"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"0"
	Option		"MinSpeed"		"0.09"
	Option		"MaxSpeed"		"0.18"
	Option		"AccelFactor"		"0.0015"
	Option		"SHMConfig"		"on"
EndSection
```

---

### Post by raldz on 2006-12-11
Thanks a bunch.. I've been looking for such tips...

---

### Post by shane2peru on 2006-12-23
Hey, thanks for the post, that is great!  Worked with my Toshiba Satellite.

Shane

---

