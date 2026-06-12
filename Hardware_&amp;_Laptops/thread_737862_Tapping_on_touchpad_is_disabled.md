---
title: "Tapping on touchpad is disabled"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by m3alnemer on 2008-03-28
Hi !:)

My touch pad doesn't respond for tapping after some changes in the tapping time in the "touchpad configuration." I think i did something wrong in my xorg.conf or it is because I installed *touchpad configuration tool*.

My buttons are working.

my touchpad  is probably an Alps touch pad.

I have touch pad configuration tool installed on my machine.

and those are my codes :

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"MinSpeed" 		"0.55"
	Option		"MaxSpeed" 		"1.0"
	Option		"AccelFactor" 		"0.049"
	Option		"MaxTapTime" 		"0"
	Option	 	"SHMConfig" 		"on"
```

Can Anyone help Please?:(

---

### Post by m3alnemer on 2008-03-28
I got it working now, but with fast scrolling. by remove the configuration tool and changing the code to:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"MinSpeed" 		"0.55"
	Option		"MaxSpeed" 		"1.0"
	Option		"AccelFactor" 		"0.049"
	Option	 	"SHMConfig" 		"off"

```

any idea how to change the scrolling speed ?

---

### Post by Whiffle on 2008-03-28
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Additional_Settings](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Additional_Settings)

looks like there is some info available in "man synaptics"

---

### Post by m3alnemer on 2008-03-29
This was helpful
I had to remove the touchpad configuration tool

```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option  "LeftEdge"              "120"
    Option  "RightEdge"             "830"
    Option  "TopEdge"               "120"
    Option  "BottomEdge"            "650"
    Option  "FingerLow"             "25"
    Option  "FingerHigh"            "30"
    Option  "MaxTapTime"            "180"
    Option  "MaxTapMove"            "220"
    Option  "MaxDoubleTapTime"      "0"
    Option  "ClickTime"  	    "0"
    Option  "EmulateMidButtonTime"  "75"
    Option  "VertScrollDelta"       "100"
    Option  "HorizScrollDelta"      "0"
    Option  "MinSpeed"              "0.45"
    Option  "MaxSpeed"              "0.75"
    Option  "AccelFactor"           "0.020"
    Option  "EdgeMotionMinZ"    "30"
    Option  "EdgeMotionMaxZ"    "160"
    Option  "EdgeMotionMinSpeed"    "200"
    Option  "EdgeMotionMaxSpeed"    "200"
    Option  "EdgeMotionUseAlways"    "0"
    Option  "UpDownScrolling"       "1"
    Option "LockedDrags" "0"
    Option "RTCornerButton" "2"
    Option "RBCornerButton" "3"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    Option "TapButton1" "1"
    Option "TapButton2" "0"
    Option "TapButton3" "0"
    Option  "CircularScrolling"     "0"
    Option  "CircScrollDelta"       "0.1"
    Option  "CircScrollTrigger"     "2"
    Option  "CircularPad"     "0"
    Option  "SHMConfig"  "true"
EndSection

```

---

