---
title: "Tablet touch not working"
date: 2011-05-02
forum: Hardware
---

### Post by WG- on 2011-05-02
Yesterday I upgraded 10.10 to 11.04 and since that moment I can not use my finger (single touch screen) anymore to control my tablet. I still can use my stylus but not my finger. Here is my xinput --list and the list-props.

```
xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; CNA7157                                 	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=18	[slave  keyboard (3)]

```

```
xinput list-props "Serial Wacom Tablet touch"
Device 'Serial Wacom Tablet touch':
	Device Enabled (125):	1
	Coordinate Transformation Matrix (127):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (249):	0
	Device Accel Constant Deceleration (250):	1.000000
	Device Accel Adaptive Deceleration (251):	1.000000
	Device Accel Velocity Scaling (252):	10.000000
	Wacom Tablet Area (309):	0, 0, 4096, 4096
	Wacom Rotation (310):	0
	Wacom Serial IDs (312):	147, 0, 3, 0
	Wacom Capacity (313):	-1
	Wacom Pressure Threshold (314):	27
	Wacom Sample and Suppress (315):	2, 4
	Wacom Enable Touch (316):	0
	Wacom Enable Touch Gesture (317):	0
	Wacom Touch Gesture Parameters (318):	50, 20, 250
	Wacom Tool Type (319):	"TOUCH" (322)
	Wacom Button Actions (320):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (321):	0, 0
```

Futhermore, I know there is a calibration app for the stylus for ubuntu anyone knows where I can get it? Couldn't find it :(

---

### Post by Favux on 2011-05-02
Hi WG-,

The driver should have turned touch on automatically.  Have you tried turning it on manually?
```
xsetwacom set "Serial Wacom Tablet touch" Touch on
```
Touch is on the wacom X driver according to list-props so it should be working.
> Futhermore, I know there is a calibration app for the stylus for ubuntu anyone knows where I can get it?
See Calibration at the mediawiki HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)

---

### Post by WG- on 2011-05-02
> **Favux said:**
> Hi WG-,

The driver should have turned touch on automatically.  Have you tried turning it on manually?
```
xsetwacom set "Serial Wacom Tablet touch" Touch on
```
Touch is on the wacom X driver according to list-props so it should be working.

See Calibration at the mediawiki HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)

Oh that was pretty easy this time. I assume it was by default then off? I must remember that for next time.

And thanks for the link: i was refering to this application:
[http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

---

### Post by Favux on 2011-05-02
Good.  :)

How 'bout that!  I just checked and xinput_calibrator is in the repos now as xinput-calibrator.  And it's been updated!

---

