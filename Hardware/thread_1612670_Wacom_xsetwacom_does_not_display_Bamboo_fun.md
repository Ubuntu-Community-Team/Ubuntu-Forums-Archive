---
title: "Wacom xsetwacom does not display Bamboo fun"
date: 2010-11-03
forum: Hardware
---

### Post by dsavi on 2010-11-03
So I got my Bamboo fun medium working just fine on Maverick, with twinview and everything. Then I suppose the kernel was updated or something, I'm not sure.

I recompiled the kernel module (Perhaps unnecessarily, I don't know), and now xsetwacom doesn't seem to recognize any of my devices- Which is strange, as it works fine otherwise (Other than twinview, which is why I'm posting here).

I used to use commands like
```
xsetwacom set 12 twinview horizontal
xsetwacom set 13 twinview horizontal
```
and it would work great. Now it gives the error
```
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'

```
Fair enough, the device id could possibly have changed. So I tried using xsetwacom to find the device names (With a variety of commands like xsetwacom --list --verbose which worked in Lucid, and xsetwacom list). None of them return anything.

Output of xinput --list

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Pen eraser      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Pen stylus      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Finger pad      	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Finger touch    	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                  	id=9	[slave  keyboard (3)]
    &#8627; Creative Technology Creative USB Headset	id=10	[slave  keyboard (3)]

```

Thanks for any help.

Edit: It may be worth noting that at first I had problems with xsetwacom not finding libwacomcfg.so.0, however later that library appeared, and xsetwacom worked again.

---

### Post by Favux on 2010-11-03
Hi dsavi,

The new kernel has a new modules directory that has the default non-working wacom.ko in it.  So you do need to compile linuxwacom against the new kernel and copy the resulting wacom.ko into place.

My guess is you didn't do that successfully and the Wacom devices aren't on the Wacom driver which is why xsetwacom isn't working.  Let's what driver this output shows us:
```
xinput list-props "Wacom BambooFun 2FG 6x8 Pen stylus"
```

---

### Post by dsavi on 2010-11-04
Thanks for the response. Here's the output:

```
Device 'Wacom BambooFun 2FG 6x8 Pen stylus':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (243):	1.000000
	Device Accel Velocity Scaling (244):	10.000000
	Wacom Tablet Area (268):	0, 0, 21648, 13530
	Wacom Rotation (269):	0
	Wacom Pressurecurve (270):	0, 0, 100, 100
	Wacom Serial IDs (271):	211, 0, 2, 0
	Wacom TwinView Resolution (272):	0, 0, 0, 0
	Wacom Display Options (273):	-1, 0, 1
	Wacom Screen Area (274):	0, 0, 3360, 1050
	Wacom Proximity Threshold (275):	42
	Wacom Capacity (276):	-1
	Wacom Pressure Threshold (277):	27
	Wacom Sample and Suppress (278):	2, 4
	Wacom Enable Touch (279):	0
	Wacom Hover Click (280):	1
	Wacom Enable Touch Gesture (281):	0
	Wacom Touch Gesture Parameters (282):	50, 20, 250
	Wacom Tool Type (283):	"STYLUS" (285)
	Wacom Button Actions (284):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
```

Where should wacom.ko be now? I have it in /lib/modules/2.6.35-22-generic/kernel/drivers/input/tablet/.

---

### Post by Favux on 2010-11-04
That would seem to be the right location.  The list-props show the device (stylus) is on the Wacom driver.

Say, by any chance did you also clone the xf86-input-wacom git repository in addition to compiling linuxwacom for a new wacom.ko?

---

### Post by dsavi on 2010-11-05
Nope, I just use the official latest source.

---

### Post by Favux on 2010-11-05
OK, because they dropped the TwinView support from xf86-input-wacom about 3 weeks ago.  You're suppose to use a new xsetwacom command that I've never used before.  But that doesn't apply to you.

When you compiled the linuxwacom did your dependency line include libxrandr-dev?:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

```
Starting with 0.8.5-11 a wacom XRandR daemon was added.

---

### Post by dsavi on 2010-11-05
I didn't have that, recompiled and still didn't work.

I used [this]("http://kishalmi.net/cms/node/90") guide originally to compile it for twinview, is there possibly something wrong there?

---

### Post by Favux on 2010-11-05
Yes there is a missing ./configure flag.  It should be:
```
./configure --enable-wacom --prefix=/usr
```
See the Bamboo P&T HOW TO:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

Edit:  Oh, and if you're reusing the linuxwacom source code tar run a 'make clean' before the ./configure line.

---

### Post by dsavi on 2010-11-05
Yep done all this (Including the make clean), but xsetwacom still doesn't want to show my device. Just to make sure that I'm doing this right, is the current command "xsetwacom list" or "xsetwacom --verbose --list"? I've tried both (And more).

Thanks for all the help, btw.

---

### Post by Favux on 2010-11-05
'xsetwacom list' should work.  But don't use that output in the xsetwacom commands.  Use the device names from 'xinput --list' in quotes in the xsetwacom commands.

---

### Post by dsavi on 2010-11-05
xsetwacom set "Wacom BambooFun 2FG 6x8 Pen stylus" TwinView horizontal, the crucial command, still doesn't work. I run it and it returns no errors, but it doesn't do anything either I'm afraid. :(

---

### Post by Favux on 2010-11-05
It sounds like it's working if:
```
xsetwacom set "Wacom BambooFun 2FG 6x8 Pen stylus" TwinView horizontal
```
no longer complains about unrecognized device.  Are you combining that with:
```
xsetwacom set "Wacom BambooFun 2FG 6x8 Pen stylus" Sceen_No 0
```
where 0 is the monitor you want, 0 or 1?  Or maybe the integer is suppose to be in quotes ("0")?

---

### Post by dsavi on 2010-11-05
Those don't return errors, but they don't have any effect either. :(
(By the way it's Screen_No, and no quotes around the integer)

---

### Post by Favux on 2010-11-05
> By the way it's Screen_No, and no quotes around the integer
Thanks for clearing that up.

Well, I'm out of ideas, for now anyway.

---

