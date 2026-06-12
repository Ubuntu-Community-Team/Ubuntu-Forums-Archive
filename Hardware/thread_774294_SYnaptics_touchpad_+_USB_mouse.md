---
title: "SYnaptics touchpad + USB mouse"
date: 2008-04-29
forum: Hardware
---

### Post by laggerzero on 2008-04-29
I know this question is probably already answered but i couldn't find it in the search. I had to reconfigure my Xorg.conf file to get my touchpad working and now my USB mouse is not working. I only changed Mouse0:

```
Section "InputDevice"
  Driver  	"synaptics"
  Identifier  	"Mouse0"
  Option	"Device"  		"/dev/psaux"
  Option	"Protocol"		"auto-dev"
  Option	"LeftEdge"		"120"
  Option	"RightEdge"		"830"
  Option	"TopEdge"		"120"
  Option	"BottomEdge"		"650"
  Option	"FingerLow"		"14"
  Option	"FingerHigh"		"15"
  Option	"MaxTapTime"		"0"
  Option	"MaxTapMove"		"110"
  Option	"EmulateMidButtonTime"	"75"
  Option	"VertScrollDelta"	"20"
  Option	"HorizScrollDelta"	"20"
  Option	"MinSpeed"		"0.3"
  Option	"MaxSpeed"		"0.75"
  Option	"AccelFactor"		"0.015"
  Option	"EdgeMotionMinSpeed"	"200"
  Option	"EdgeMotionMaxSpeed"	"200"
  Option	"UpDownScrolling"	"1"
  Option	"CircularScrolling"	"1"
  Option	"CircScrollDelta"	"0.1"
  Option	"CircScrollTrigger"	"2"
EndSection
```

any ideas on how I can get my USB mouse to work again? I'm sure it is a quick fix

---

