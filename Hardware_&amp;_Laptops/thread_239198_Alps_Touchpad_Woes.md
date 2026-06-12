---
title: "Alps Touchpad Woes"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by gwayne on 2006-08-18
So I installed Ubuntu on my Toshiba Satellite 1135-S155 about a month and a half ago and am loving it but I have one relatively minor issue.  I cannot, for the life of me, get my Alps Touchpad to work.  I always keep a USB mouse plugged into the machine so its not so bad but I really want to get the touchpad working for when I take it out on the balcony or somewhere else.  The touchpad just doesnt work, its like its not even being detected.  Does anyone have some advice?  I have been trolling these forums for a few weeks, read the_blue_pills guide, and many other posts, but nothing seems to work.

Here is the output from 'vi /proc/bus/input/devices'

```
I: Bus=0003 Vendor=045e Product=0040 Version=0300
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse2 event3 ts2
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
```

Im not sure why it detects three devics, all I have are the USB Intellieye and the touchpad.

Here are the relevant sections from my xorg.conf:

```
Section "InputDevice"
	Identifier	"USB Mouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	#Option		"Device"		"/dev/input/mouse2"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section	"InputDevice"
	Identifier	"Alps Glidepoint"
	Driver		"synaptics"
	#Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/event3"
	Option		"Protocol"		"event"
	Option		"SHMConfig"		"on"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"600"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"MaxDoubleTapTime"	"180"
	Option		"ClickTime"		"100"
	Option		"FastTaps"		"1"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"20"
	Option		"MinSpeed"		"0.2"
	Option		"MaxSpeed"		"2.5"
	Option		"AccelFactor"		"0.06"
	Option		"EdgeMotionMinZ"	"30"
	Option		"EdgeMotionMaxZ"	"160"
	Option		"EdgeMotionMinSpeed"	"15"
	Option		"EdgeMotionMaxSpeed"	"15"
	Option		"EdgeMotionUseAlways"	"0"
	Option		"UpDownScrolling"	"1"
	Option		"LeftRightScrolling"	"1"
	Option		"TouchpadOff"		"0"
	Option		"GuestMouseOff"		"1"
	Option		"LockedDrags"		"1"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"LTCornerButton"	"2"
	Option		"LBCornerButton"	"2"
	Option		"TapButton1"		"1"
	Option		"TapButton2"		"1"
	Option		"TapButton3"		"3"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.08"
	Option		"CircScrollTrigger"	"0"
	Option		"CircularPad"		"0"
	Option		"PalmDetect"		"1"
	Option		"PalmMinWidth"		"10"
	Option		"PalmMinZ"		"200"
	Option		"CoastingSpeed"		"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"USB Mouse"
	InputDevice     "Alps Glidepoint"
EndSection

```

Thanks for any advice. :D

---

### Post by gwayne on 2006-08-19
oh man, turns out all those how-tos worked, all i had to do was turn on the touchpad with the laptops function key.  

](*,)  but hey at least it works now.

---

