---
title: "Genius Tablet pen doesn't move unless pressed down"
date: 2012-09-30
forum: Hardware
---

### Post by Jan Snajder on 2012-09-30
Hi,

I'm trying to use Genius tablet G-Pen F610 on Ubuntu Precise. The tablet seems to be working out of the box, except for one small but annoying detail: the pen doesn't move unless it is pressed down. I've never used a tablet before, but I think the pen should move when hovering over surface, or shouldn't it?

Here is what I get from lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 005: ID 04f2:b217 Chicony Electronics Co., Ltd 
Bus 002 Device 014: ID 172f:0034 Waltop International Corp. Slim Tablet 12.1"
Bus 002 Device 013: ID 046d:0a0c Logitech, Inc. Clear Chat Comfort USB Headset
Bus 001 Device 007: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
```

Here is what I get from "xinput list":

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=13	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet stylus	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft  Compact Optical Mouse 500    	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Headset           	id=16	[slave  keyboard (3)]
```

and from "xinput list-props 15":

```
Device 'WALTOP International Corp. Slim Tablet stylus':
	Device Enabled (132):	1
	Coordinate Transformation Matrix (134):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (255):	0
	Device Accel Constant Deceleration (256):	1.000000
	Device Accel Adaptive Deceleration (257):	1.000000
	Device Accel Velocity Scaling (258):	10.000000
	Device Node (250):	"/dev/input/event13"
	Wacom Tablet Area (728):	0, 0, 20000, 12500
	Wacom Rotation (729):	0
	Wacom Pressurecurve (730):	0, 0, 100, 100
	Wacom Serial IDs (731):	52, 1, 0, 0, 0
	Wacom Serial ID binding (732):	0
	Wacom Pressure Threshold (733):	27
	Wacom Sample and Suppress (734):	2, 4
	Wacom Enable Touch (735):	1
	Wacom Hover Click (736):	1
	Wacom Enable Touch Gesture (737):	0
	Wacom Touch Gesture Parameters (738):	0, 0, 250
	Wacom Tool Type (423):	"STYLUS" (419)
	Wacom Button Actions (739):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Device Product ID (249):	5935, 52
	Wacom Debug Levels (740):	0, 0
```

Interestingly, the "Wacom Graphics Tablet" utility from System Settings says "No tablet detected".

Any help is greatly appreciated!

---

### Post by Favux on 2012-10-01
Hi Jan Snajder,

Welcome to Ubuntu forums!


> the pen doesn't move unless it is pressed down. I've never used a tablet before, but I think the pen should move when hovering over surface, or shouldn't it?
I think you are correct.  I believe at least one other person has reported that.  That sounds like there is something off with proximity detection for the Waltop pen on the Wacom X driver.

I wonder if we should try running evtest to see if that shows something?
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest)
I would think it would show coordinate changes without the pen touching (i.e. not report pressure values) if the cursor was tracking while the pen hovered over the tablet.
> Interestingly, the "Wacom Graphics Tablet" utility from System Settings says "No tablet detected".

That's because the data file for your Waltop tablet is not in libwacom.  I submitted several non-wacom data files a while ago that still aren't in libwacom.  I probably have it around somewhere and you could try adding it to libwacom.

---

### Post by Jan Snajder on 2012-10-01
Favux,

Many thanks for the fast reply. I've run evtest as you suggested. Here is a snippet of what I've got:

```
Testing ... (interrupt to exit)
Event: time 1349100428.019361, type 1 (EV_KEY), code 320 (BTN_TOOL_PEN), value 1
Event: time 1349100428.019367, type 3 (EV_ABS), code 0 (ABS_X), value 6009
Event: time 1349100428.019370, type 3 (EV_ABS), code 1 (ABS_Y), value 7715
Event: time 1349100428.019374, -------------- SYN_REPORT ------------
Event: time 1349100428.051409, type 4 (EV_MSC), code 4 (MSC_SCAN), value d0042
Event: time 1349100428.051411, type 1 (EV_KEY), code 330 (BTN_TOUCH), value 1
Event: time 1349100428.051420, type 3 (EV_ABS), code 0 (ABS_X), value 6010
Event: time 1349100428.051423, type 3 (EV_ABS), code 1 (ABS_Y), value 7716
Event: time 1349100428.051427, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 15
Event: time 1349100428.051429, -------------- SYN_REPORT ------------
Event: time 1349100428.059409, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 18
Event: time 1349100428.059412, -------------- SYN_REPORT ------------
Event: time 1349100428.067406, type 4 (EV_MSC), code 4 (MSC_SCAN), value d0042
Event: time 1349100428.067409, type 1 (EV_KEY), code 330 (BTN_TOUCH), value 0
Event: time 1349100428.067424, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 0
Event: time 1349100428.067425, -------------- SYN_REPORT ------------
Event: time 1349100428.091404, type 4 (EV_MSC), code 4 (MSC_SCAN), value d0042
Event: time 1349100428.091407, type 1 (EV_KEY), code 330 (BTN_TOUCH), value 1
Event: time 1349100428.091415, type 3 (EV_ABS), code 0 (ABS_X), value 6075
Event: time 1349100428.091418, type 3 (EV_ABS), code 1 (ABS_Y), value 7672
Event: time 1349100428.091422, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 19
Event: time 1349100428.091423, -------------- SYN_REPORT ------------
Event: time 1349100428.099328, type 3 (EV_ABS), code 0 (ABS_X), value 6084
Event: time 1349100428.099332, type 3 (EV_ABS), code 1 (ABS_Y), value 7670
Event: time 1349100428.099336, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 20
Event: time 1349100428.099338, -------------- SYN_REPORT ------------
Event: time 1349100428.107410, type 3 (EV_ABS), code 0 (ABS_X), value 6099
Event: time 1349100428.107414, type 3 (EV_ABS), code 1 (ABS_Y), value 7660
Event: time 1349100428.107418, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 21
Event: time 1349100428.107420, -------------- SYN_REPORT ------------
Event: time 1349100428.115409, type 3 (EV_ABS), code 0 (ABS_X), value 6118
Event: time 1349100428.115413, type 3 (EV_ABS), code 1 (ABS_Y), value 7649
Event: time 1349100428.115419, -------------- SYN_REPORT ------------
Event: time 1349100428.123325, type 3 (EV_ABS), code 0 (ABS_X), value 6142
Event: time 1349100428.123329, type 3 (EV_ABS), code 1 (ABS_Y), value 7633
Event: time 1349100428.123333, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 19
Event: time 1349100428.123334, -------------- SYN_REPORT ------------
Event: time 1349100428.131407, type 3 (EV_ABS), code 0 (ABS_X), value 6169
Event: time 1349100428.131411, type 3 (EV_ABS), code 1 (ABS_Y), value 7616
Event: time 1349100428.131415, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 22
Event: time 1349100428.131417, -------------- SYN_REPORT ------------
Event: time 1349100428.139415, type 3 (EV_ABS), code 0 (ABS_X), value 6200
Event: time 1349100428.139419, type 3 (EV_ABS), code 1 (ABS_Y), value 7592
Event: time 1349100428.139423, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 26
Event: time 1349100428.139424, -------------- SYN_REPORT ------------
Event: time 1349100428.147409, type 3 (EV_ABS), code 0 (ABS_X), value 6233
Event: time 1349100428.147413, type 3 (EV_ABS), code 1 (ABS_Y), value 7574
Event: time 1349100428.147416, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 33
Event: time 1349100428.147418, -------------- SYN_REPORT ------------
Event: time 1349100428.155406, type 3 (EV_ABS), code 0 (ABS_X), value 6251
Event: time 1349100428.155410, type 3 (EV_ABS), code 1 (ABS_Y), value 7562
Event: time 1349100428.155414, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 37
Event: time 1349100428.155415, -------------- SYN_REPORT ------------
Event: time 1349100428.163323, type 3 (EV_ABS), code 0 (ABS_X), value 6287
Event: time 1349100428.163326, type 3 (EV_ABS), code 1 (ABS_Y), value 7541
Event: time 1349100428.163330, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 45
Event: time 1349100428.163332, -------------- SYN_REPORT ------------
Event: time 1349100428.171416, type 3 (EV_ABS), code 0 (ABS_X), value 6324
Event: time 1349100428.171421, type 3 (EV_ABS), code 1 (ABS_Y), value 7523
Event: time 1349100428.171425, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 58
Event: time 1349100428.171427, -------------- SYN_REPORT ------------
Event: time 1349100428.179414, type 3 (EV_ABS), code 0 (ABS_X), value 6368
Event: time 1349100428.179418, type 3 (EV_ABS), code 1 (ABS_Y), value 7502
Event: time 1349100428.179423, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 71
Event: time 1349100428.179424, -------------- SYN_REPORT ------------
Event: time 1349100428.187409, type 3 (EV_ABS), code 0 (ABS_X), value 6414
Event: time 1349100428.187414, type 3 (EV_ABS), code 1 (ABS_Y), value 7471
Event: time 1349100428.187418, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 82
Event: time 1349100428.187420, -------------- SYN_REPORT ------------
Event: time 1349100428.195407, type 3 (EV_ABS), code 0 (ABS_X), value 6468
Event: time 1349100428.195411, type 3 (EV_ABS), code 1 (ABS_Y), value 7450
Event: time 1349100428.195415, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 94
Event: time 1349100428.195417, -------------- SYN_REPORT ------------
Event: time 1349100428.203394, type 3 (EV_ABS), code 0 (ABS_X), value 6495
Event: time 1349100428.203398, type 3 (EV_ABS), code 1 (ABS_Y), value 7439
Event: time 1349100428.203401, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 100
Event: time 1349100428.203403, -------------- SYN_REPORT ------------
Event: time 1349100428.211409, type 3 (EV_ABS), code 0 (ABS_X), value 6551
Event: time 1349100428.211413, type 3 (EV_ABS), code 1 (ABS_Y), value 7417
Event: time 1349100428.211417, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 110
Event: time 1349100428.211419, -------------- SYN_REPORT ------------
Event: time 1349100428.219413, type 3 (EV_ABS), code 0 (ABS_X), value 6609
Event: time 1349100428.219417, type 3 (EV_ABS), code 1 (ABS_Y), value 7398
Event: time 1349100428.219421, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 117
Event: time 1349100428.219422, -------------- SYN_REPORT ------------
Event: time 1349100428.227411, type 3 (EV_ABS), code 0 (ABS_X), value 6667
Event: time 1349100428.227415, type 3 (EV_ABS), code 1 (ABS_Y), value 7378
Event: time 1349100428.227419, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 123
Event: time 1349100428.227420, -------------- SYN_REPORT ------------
Event: time 1349100428.235328, type 3 (EV_ABS), code 0 (ABS_X), value 6726
Event: time 1349100428.235332, type 3 (EV_ABS), code 1 (ABS_Y), value 7360
Event: time 1349100428.235336, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 128
Event: time 1349100428.235338, -------------- SYN_REPORT ------------
Event: time 1349100428.243410, type 3 (EV_ABS), code 0 (ABS_X), value 6788
Event: time 1349100428.243414, type 3 (EV_ABS), code 1 (ABS_Y), value 7333
Event: time 1349100428.243417, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 135
Event: time 1349100428.243419, -------------- SYN_REPORT ------------
Event: time 1349100428.251413, type 3 (EV_ABS), code 0 (ABS_X), value 6815
Event: time 1349100428.251417, type 3 (EV_ABS), code 1 (ABS_Y), value 7319
Event: time 1349100428.251421, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 139
Event: time 1349100428.251422, -------------- SYN_REPORT ------------
Event: time 1349100428.259410, type 3 (EV_ABS), code 0 (ABS_X), value 6883
Event: time 1349100428.259414, type 3 (EV_ABS), code 1 (ABS_Y), value 7289
Event: time 1349100428.259418, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 147
```

When I just hover the pen closely over the surface, without touching the surface, there are no events reported at all. So I think it might indeed be the case that proximity detection is not working.

Should I now try to use your non-wacom data files?

---

### Post by Favux on 2012-10-01
Looks like that's the problem.  Let me see if I can find my BambooPT evtests to compare with.  Or else I'll run a new one.

What we may want to do is report this to the DIGImend-users mailing list and see what Nick thinks:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  That's probably a better first choice rather than the linuxwacom-discuss mailing list:  [http://sourceforge.net/mail/?group_id=69596](http://sourceforge.net/mail/?group_id=69596)

The libwacom data files are in /usr/share/libwacom.  Rather than send you the patches I've attached the data files.  Let's see what happens if you just copy the **slim-tablet-12.1.tablet** data file there and restart.

---

### Post by Favux on 2012-10-01
This is an evtest on my BambooPT I just ran.  The BambooPT has an LED that changes from blue to orange when the pen is in proximity.  Does your tablet have a similar LED?  Started with the pen in the upper right corner and drew a diagnal to bottom left corner with the pen hovering.  Then reversed with the pen in contact:
```
top right
Event: time 1349103214.750290, type 3 (EV_ABS), code 0 (ABS_X), value 274
Event: time 1349103214.750292, type 3 (EV_ABS), code 1 (ABS_Y), value 8575
Event: time 1349103214.750294, type 3 (EV_ABS), code 25 (ABS_DISTANCE), value 27
Event: time 1349103214.750297, -------------- SYN_REPORT ------------
Event: time 1349103214.758291, type 3 (EV_ABS), code 0 (ABS_X), value 257
Event: time 1349103214.758293, type 3 (EV_ABS), code 1 (ABS_Y), value 8578
Event: time 1349103214.758297, -------------- SYN_REPORT ------------
Event: time 1349103214.766293, type 3 (EV_ABS), code 0 (ABS_X), value 246
Event: time 1349103214.766295, type 3 (EV_ABS), code 1 (ABS_Y), value 8593
Event: time 1349103214.766297, type 3 (EV_ABS), code 25 (ABS_DISTANCE), value 26
..........
Event: time 1349103217.946182, type 3 (EV_ABS), code 1 (ABS_Y), value 634
Event: time 1349103217.946185, type 3 (EV_ABS), code 25 (ABS_DISTANCE), value 2
Event: time 1349103217.946187, -------------- SYN_REPORT ------------
Event: time 1349103217.950178, type 3 (EV_ABS), code 1 (ABS_Y), value 637
Event: time 1349103217.950182, -------------- SYN_REPORT ------------
Event: time 1349103217.958178, type 3 (EV_ABS), code 1 (ABS_Y), value 647
Event: time 1349103217.958180, type 3 (EV_ABS), code 25 (ABS_DISTANCE), value 1
Event: time 1349103217.958182, -------------- SYN_REPORT ------------
Event: time 1349103217.966178, type 3 (EV_ABS), code 0 (ABS_X), value 14194
Event: time 1349103217.966183, -------------- SYN_REPORT ------------
Event: time 1349103217.974175, type 1 (EV_KEY), code 330 (BTN_TOUCH), value 1
Event: time 1349103217.974180, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 163
Event: time 1349103217.974183, -------------- SYN_REPORT ------------
Event: time 1349103217.982178, type 3 (EV_ABS), code 0 (ABS_X), value 14193
Event: time 1349103217.982181, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 199
Event: time 1349103217.982183, -------------- SYN_REPORT ------------
Event: time 1349103217.990177, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 206
Event: time 1349103217.990180, -------------- SYN_REPORT ------------
Event: time 1349103217.998178, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 209
Event: time 1349103217.998182, -------------- SYN_REPORT ------------
Event: time 1349103218.006181, type 3 (EV_ABS), code 24 (ABS_PRESSURE), value 214
Event: time 1349103218.006183, type 3 (EV_ABS), code 25 (ABS_DISTANCE), value 0

```
You can see it reports ABS_DISTANCE (which your evtest isn't) right up until the inflection point:
```
Event: time 1349103217.974175, type 1 (EV_KEY), code 330 (BTN_TOUCH), value 1
```
when the stylus tip contacts the tablet and it switches to reporting ABS_PRESSURE and an ABS_DISTANCE of 0.

---

### Post by Jan Snajder on 2012-10-02
Favux,

I've copied the slim-tablet-12.1.tablet data file into /usr/share/libwacom (and changed its ownership to root:root) and restarted. Unfortunately, the tablet still doesn't detect pen hovering.

Genius G-Pen F610 has a blue LED that blinks when the tablet is on stand by, and stops blinking when the pen is touching the surface. I don't really know if it should change the color when the pen is in proximity.

Any suggestions what to try next?

Btw., I've noticed that if I press a button on the pen (the lower one; there are two buttons), then the tablet does detect the pen hovering (but only while the button is being pressed).

---

### Post by Favux on 2012-10-02
Does the GNOME applet now use the tablet's name instead of "No tablet detected"?

I think what I suggested to the other tablet user was to look at his instructions and see if his pen had a proximity adjustment.  Some of them do.  Might be a little screw or something in the pen that you turn to adjust proximity.  Might be yours is just set very low.

If there is proximity detection for the tablet, and it sounds like it given what pressing the button does, then there might be a software setting for proximity in Windows.  If there is one that would tell us it might be missing from linux.

---

### Post by Jan Snajder on 2012-10-02
Unfortunately, GNOME still reports "No tablet detected". Why is this?

How can I check whether the device is actually using the new data file that you provided me with?

The user manual is not much of a help: quick installation guide for Windows in 23 languages. It does not mention any adjustments at all.

---

### Post by Favux on 2012-10-02
> Unfortunately, GNOME still reports "No tablet detected". Why is this?
Did you restart?

> The user manual is not much of a help: quick installation guide for Windows in 23 languages. It does not mention any adjustments at all. 
So no help there.  I did find instructions on how to do that for at least one pen with googling, pictures and all.  Don't know if your pen has that though.

I just checked an Aiptek tablet I have.  I placed it on the evdev driver instead of the Aiptek driver.  And the cursor follows the pen without the pen contacting the tablet.  We could try placing your pen on the xf86-input-evdev driver instead of the Wacom X driver and see if hover then works.  That would imply the problem is with how the Wacom X driver is handling proximity detection with your Waltop tablet.

---

### Post by Jan Snajder on 2012-10-03
Yes, I did restart. Still, GNOME says "No tablet detected"

> So no help there. I did find instructions on how to do that for at least one pen with googling, pictures and all. Don't know if your pen has that though.

I've stumbled on the same web page, but now I cannot find it anymore. Can you give me the link?

Btw. this seems also to be an issue on Windows:
[http://www.fixya.com/support/t3916910-tablet_not_recognizing_pen_unless](http://www.fixya.com/support/t3916910-tablet_not_recognizing_pen_unless)

> We could try placing your pen on the xf86-input-evdev driver instead of the Wacom X driver and see if hover then works. That would imply the problem is with how the Wacom X driver is handling proximity detection with your Waltop tablet.

Yes, let's do that. How should I proceed?

---

### Post by Favux on 2012-10-03
Well how 'bout that!  Amazingly I found the bookmark without much trouble.  Even more amazing it appears to be for your tablet, Waltop Slim Tablet 12.1/Genius G-Pen F610!  Info. on tablet:  sourceforge.net/apps/mediawiki/digimend/index.php?title=Waltop_Slim_Tablet_12.1"  And it appears to be the same issue!  See:  [http://forum.deviantart.com/technology/hardware/1538233/](http://forum.deviantart.com/technology/hardware/1538233/)

Good find with the Windows link.  Tends to make it look more like a tablet/pen problem, not the software.

> Yes, let's do that. How should I proceed?

This should be easy.  Just go to /usr/share/X11/xorg.conf.d and open the 50-wacom.conf:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
The 50-wacom.conf file should look something like:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
	Identifier "Waltop class"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```
Just comment out the Waltop snippet and restart:
```
# Waltop tablets
#Section "InputClass"
#	Identifier "Waltop class"
#	MatchProduct "WALTOP"
#	MatchIsTablet "on"
#	MatchDevicePath "/dev/input/event*"
#	Driver "wacom"
#EndSection
```
That should let the tablet fall through to the evdev driver after a restart.

---

### Post by Jan Snajder on 2012-10-04
Favux, 

many thanks again. Today I've tried the tablet on Windows and found out that it doesn't work there either. So, I guess it's a hardware thing after all, and the fix you found will probably do the trick. Now I only need to find a precision screwdriver :p I will be very happy if this works out, but also very angry with Genius.

Regarding the switch from Wacom X driver to xf86-input-evdev driver: still gnome pannel says "No tablet detected".

Best,
Jan

---

### Post by Jan Snajder on 2012-10-19
Ok, this is how the story ended: I've got the precision screwdriver, I did as suggested in the previous post, and... WOW... the proximity detection works now. So the problem was in the pen after all. Anyhow, I think it's amazing that Genius makes no mention of this issue whatsoever...

Jan

---

### Post by Favux on 2012-10-19
Nice job Jan.

I agree.  Genius (KYE) should include that in the instruction manuals.

I'll see if I can come up with a way to add mechanical proximity adjustment to the [DIGImend wiki]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend").

---

