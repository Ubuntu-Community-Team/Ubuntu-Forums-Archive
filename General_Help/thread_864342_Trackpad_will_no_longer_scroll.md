---
title: "Trackpad will no longer scroll"
date: 2008-07-19
forum: General Help
---

### Post by Vegabondsx on 2008-07-19
My trackpad on my ASUS Eee PC will no longer scroll when I run my finger along the right side of the trackpad. If I go under the Mouse control panel the tab that lets me configure it is no longer there.

I downloaded GSynaptics and it tells me I need to set 'SHMConfig to 'true' in xorg.conf, but I added that line under the trackpad and it doesn't help.

Anyone know how to turn this back on?

Thanks

Ryan

---

### Post by aashay on 2008-07-19
Here is the particular section from my xorg.conf
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        Option          "SHMConfig"             "true"
	Option 		"MinSpeed" 		"1.0"
	Option 		"MaxSpeed" 		"1.0"
	Option 		"AccelFactor" 		"0.3"
	Option		"VertScrollDelta"	"3"
	Option		"FingerLow"		"20" 
	Option		"FingerHigh"		"35"
	Option		"VertEdgeScroll"	"on"
	Option		"GuestMouseOff"		"on"
	Option		"LockedDrags"		"on"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"GrabEventDevice"	"on"
EndSection
```
VertScrollDelta and VertEdgeScroll is all you need imo

---

### Post by Vegabondsx on 2008-07-19
It still has no effect. It seems like it's ignoring xorg.conf... at least for the trackpad.


UPDATE
Ok, I reset xorg.conf by running the command found in it, but now right click doesn't work on the desktop >_>

UPDATE2
I reset xwindows a second time and it seems ok...

---

