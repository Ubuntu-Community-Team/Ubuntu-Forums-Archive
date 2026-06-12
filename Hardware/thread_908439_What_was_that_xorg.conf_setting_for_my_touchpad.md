---
title: "What was that xorg.conf setting for my touchpad?"
date: 2008-09-02
forum: Hardware
---

### Post by davekra on 2008-09-02
I've got my Alps touchpad working will with the synaptics stuff in xorg.conf.

One thing that's bothering me is the cursor doesn't move when I move.  I start a move and the cursor starts moving after my finger moves about 1/4".   I remember seeing a setting that specified how many pixels your finger should move before the cursor but can't find it now.  

Anyone remember what the setting is?

Thanks,
davidk
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option       "LeftEdge"              "130"
	Option       "RightEdge"             "840"
	Option       "TopEdge"               "130"
	Option       "BottomEdge"            "640"
	Option       "FingerLow"             "17"
	Option       "FingerHigh"            "18"
	Option       "MaxTapTime"            "200"
	Option       "MaxTapMove"            "240"
#	Option       "MaxTapMove"            "110"
	Option       "ClickTime"             "10"
	Option       "MaxDoubleTapTime"      "200"
#	Option       "MaxDoubleTapTime"      "100"
	Option       "EmulateMidButtonTime"  "75"
	Option       "VertScrollDelta"       "20"
	Option       "HorizScrollDelta"      "20"
	Option       "MinSpeed"              "0.85"
#	Option       "MinSpeed"              "0.60"
	Option       "MaxSpeed"              "1.00"
#	Option       "MaxSpeed"              "1.10"
	Option       "AccelFactor"           "0.020"
#	Option       "AccelFactor"           "0.030"
	Option       "EdgeMotionMinSpeed"    "200"
	Option       "EdgeMotionMaxSpeed"    "200
	Option       "UpDownScrolling"       "1"
	Option       "CircularScrolling"     "1"
	Option       "CircScrollDelta"       "0.1"
	Option       "CircScrollTrigger"     "2"
	Option       "SHMConfig"             "true"
	Option       "Emulate3Buttons"       "on"
EndSection
```

---

