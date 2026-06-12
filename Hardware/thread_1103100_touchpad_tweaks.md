---
title: "touchpad tweaks"
date: 2009-03-22
forum: Hardware
---

### Post by themagicmanfromtrent on 2009-03-22
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"		"true"
	Option "HorizEdgeScroll" "on"
	Option "VertEdgeScroll" "on"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "VertTwoFingerScroll" "1"
	Option "HorizTwoFingerScroll" "1"
	Option "EmulateTwoFingerMinZ"  "90"
	Option "CornerCoasting" "on"
	Option "PalmDetect" "on"
	Option "CircularScrolling" "on"
	Option "CircScrollTrigger" "3"
EndSection
```

Above is the Synaptics part of xorg.conf. I'm not really sure which is applicable to my laptop and which isn't, and which is compatible with Hardy.

I put the "EmulateTwoFingerMinZ"  "90" part there so that when it detects a pressure of more than 90, it scrolls instead of moves the cursor, but that doesn't seem to work. Neither does the circular scrolling I configured in the touchpad settings. Why is this?

Basically, what can I do to get 2 finger scrolling to work, circular scrolling to work, and what is there in xorg which isn't really needed?

---

### Post by themagicmanfromtrent on 2009-03-22
Actually, I just figured it out. The Horizontal Scroll was off. "HorizEdgeScroll" refers to the lines on the side of the touchpad.

I can now scroll with two fingers!

For the record: Dell XPS M1530

---

