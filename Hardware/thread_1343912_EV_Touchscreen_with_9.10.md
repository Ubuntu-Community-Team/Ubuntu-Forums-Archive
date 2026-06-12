---
title: "EV Touchscreen with 9.10"
date: 2009-12-02
forum: Hardware
---

### Post by MelIrizarry on 2009-12-02
Been trying to solve getting the evtouchscreen working on the Panasonic Toughbook CF-30 using Ubuntu 9.10.  Here is my solution if anyone needs it.

1) From synaptic or apt-get install xserver-xorg-input-evtouch
2) Log out
3) ctrl-alt-F1 into a terminal session and log in.
4) sudo stop gdm (or kdm)
5) sudo calibrate_touchscreen
6) run pointer along all edges until the min/max x/y values stop moving
7) press enter and wait for the top left X to turn red.
8) press the red X's as they appear
9) note the min x/y and may x/y values.
10) sudo X -configure
11) edit the xorg.conf.new file created
12) enter:
	```
InputDevice    "touchscreen"
```
in the "InputDevice" section
13) enter
```
Section "InputDevice"
	Identifier	"touchscreen"
	Driver		"evtouch"
	Option		"device"	"/dev/input/event3"
	Option		"TapTimer"	"10"
	Option		"LongTouchTimer"	"1500"
	Option		"MinX"	"XXXX" (replace with your MinX)
	Option		"MinY"	"XXXX" (replace with your MinY)
	Option		"MaxX"	"XXXX" (replace with your MaxX)
	Option		"MaxY"	"XXXX" (replace with your MaxY)
	Option		"ReportingMode" "Raw"
	Option		"Emulate3Buttons" "false"
	Option		"Emulate3Timeout" "50"
	Option		"SendCoreEvents" "on"
	Option		"MoveLimit" "0"
EndSection

```
!!Be sure to change the MinX, MinY, MaxX, MaxY values to the ones you noted in step 9!!

14)Save your modified file.
15)sudo cp xorg.conf.new /etc/X11/xorg.conf
16)sudo start gdm

That should do it.

Hope it is useful for some.

Mel

---

