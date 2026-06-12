---
title: "Synaptics touchpad, disabling tap-to-click"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by jimcser on 2006-01-08
I'm running Badger on a Dell Inspiron 5100, and I'm trying to disable
the tap-to-click feature on the Synaptics touchpad.  I've gotten a
lot of good information from the forums, but I'm not quite there yet.

Here is the relevant section from /etc/X11/xorg.conf :
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
	Option 		"Device" 		"/dev/input/event1"
#	Option		"Protocol"		"auto-dev"
	Option 		"Protocol" 		"event"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
        Option		"MaxTapTime" 		"0"
EndSection

The touchpad actually works pretty well, I just don't like tap-to-click.
I first added the SHMConfig and MaxTapTime lines, but I was still
getting the "Can't access shared memory" error.   I then checked
/var/log/Xorg.0.log, and noticed that the touchpad was not even
being seen.  I eventually had to change the Device and Protocol
default values as shown to get synclient to run.  

As a test, I can toggle the touchpad on and off with
"sudo synclient TouchpadOff=1 or =0", so I know I'm getting close,
but I still can't make the tap-to-click go away.  

Any ideas?  Thanks.

---

### Post by vayu on 2006-01-09
I really don't know anything about this, but I've managed to get it disabled on my Inspiron 6000.  Here is my xorg listing.  Maybe you can find something there.  I thought it was the maxtaptime = 0, but you already have that.  Make sure you have the proper event #.

Section "InputDevice"
	Identifier "ALPS"
	Driver "synaptics"
	Option "AlwaysCore"
	Option "Device" "/dev/input/event3"
	Option "Protocol" "event"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
#	Option "MaxTapTime" "180"
	Option "MaxTapTime" "0"
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

---

### Post by jimcser on 2006-01-09
I tried changing the event number, with these results:
event0-- locked out the keyboard at the login screen
event1-- can run synclient, can toggle TouchpadOff, can't change tap-to-click
event2-- can run synclient, but can't toggle TouchpadOff 
event3-- can't access shared memory

So, event1 works best, but still not what I want.   My default install of
xorg-driver-synaptics is 0.14.3+revertedto+0.13.6-0ubuntu3, so maybe
a later one fixes it. 

This is my output from synclient:

Parameter settings:
    LeftEdge             = 1900
    RightEdge            = 5400
    TopEdge              = 1900
    BottomEdge           = 4000
    FingerLow            = 25
    FingerHigh           = 30
    MaxTapTime           = 0
    MaxTapMove           = 220
    MaxDoubleTapTime     = 180
    ClickTime            = 100
    EmulateMidButtonTime = 75
    VertScrollDelta      = 100
    HorizScrollDelta     = 0
    MinSpeed             = 0.02
    MaxSpeed             = 0.18
    AccelFactor          = 0.0015
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 200
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    TouchpadOff          = 0
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 2
    RBCornerButton       = 3
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 2
    TapButton3           = 3
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 0
    CircularPad          = 0

---

### Post by vayu on 2006-01-09
[QUOTE=jimcser]I tried changing the event number, with these results:
event0-- locked out the keyboard at the login screen
event1-- can run synclient, can toggle TouchpadOff, can't change tap-to-click
event2-- can run synclient, but can't toggle TouchpadOff 
event3-- can't access shared memory

So, event1 works best, but still not what I want.   My default install of
xorg-driver-synaptics is 0.14.3+revertedto+0.13.6-0ubuntu3, so maybe
a later one fixes it. 
[/QUOTE]

You've probably got the right event, but anyway, from this post: [http://ubuntuforums.org/showthread.php?t=78904]("http://ubuntuforums.org/showthread.php?t=78904")
It shows where to get the proper event number.

```
Next, use the following command to find the correct handler of the Alps touchpad:

cat /proc/bus/input/devices

on my system, it shows up something like the following

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse3 event5 ts2
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
```

Next to the H, see where it says event5, use whatever it shows there on your system.  I would do it to at least verify that event1 is the right one.

Good luck, sorry I can't be of more help.

---

