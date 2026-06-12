---
title: "GSynaptics Won't Initialize (Driver Problem?) (Side Scroll on Inspiron 6000 Touchpad"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by kirkio on 2006-12-27
After updating a few programs in Edgy and restarting, my Alps touchpad on my Dell Inspiron 6000 began moving very slowly, to the point that it is almost rendered useless. Additionally, the side scroll zone on the pad did not function. I tried modifying the sensitivity and acceleration in "System --> Preferences --> Mouse" but even on the highest settings the mouse moved very slowly. When I plug in a USB mouse, the USB mouse works fine at a decent speed. The section from my xorg.conf is below:
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

After some searching, I decided to try using someone else's xorg.conf that they had posted. That code is below:
```
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/input/event2"
Option "Protocol" "event"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "15"
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "true"
EndSection
```
That code _did_ speed up my cursor, but now the side scroll zone still does not work. On one reboot, it did begin working and I was able to configure it in GSynaptics, but now whenever I try to load GSynaptics I get the error: **GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics**. Why won't it start even though SHMConfig is true?

I have tried restarting X by doing Alt-Ctrl-Backspace.

Why can't I get my sidescroll zone (the zone on the right-side of the touchpad that allows scrolling) to work and how can I fix it? Would copying and pasting someone else's xorg.conf work?

Thanks,
Kirk

---

### Post by cam_tram on 2007-01-09
Here's my xorg.conf section, GSynaptics works fine:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection
```

---

