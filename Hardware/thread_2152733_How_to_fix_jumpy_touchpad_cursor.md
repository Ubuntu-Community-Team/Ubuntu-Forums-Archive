---
title: "How to fix jumpy touchpad cursor?"
date: 2013-06-08
forum: Hardware
---

### Post by csete on 2013-06-08
I have a bit of a problem with the touchpad on my Sony VAIO SVT15115CXS running 13.04.  In many cases, when I'm trying to tap to click, the cursor will jump around causing me to miss the click target.  I've tweaked lots of setting to try to improve this, but I can't seem to find the best values to keep this from happening.  I'm explicitly setting the following values as part of the gsettings-daemon hotplug script.

```

xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Scrolling Distance" -107 -107
xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Move Speed"  0.1 1.7 0.015 40 # 0.25 1.75 0.037126 40
xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Palm Detection"  1
xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Finger" 25 30 256
xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Noise Cancellation" 2 2

```

In addition, I've tried to set the hysteresis settings in /usr/share/X11/xorg.conf.d/50-synaptics.conf like:

```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"
      Option "HorizHysteresis" "1"
      Option "VertHysteresis" "1"
EndSection

```

The resulting settings from xinput are:

```

Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (133):	1
	Coordinate Transformation Matrix (135):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (261):	1
	Device Accel Constant Deceleration (262):	2.500000
	Device Accel Adaptive Deceleration (263):	1.000000
	Device Accel Velocity Scaling (264):	12.500000
	Synaptics Edges (285):	1766, 5388, 1643, 4535
	Synaptics Finger (286):	25, 30, 256
	Synaptics Tap Time (287):	180
	Synaptics Tap Move (288):	237
	Synaptics Tap Durations (289):	180, 180, 100
	Synaptics ClickPad (290):	1
	Synaptics Tap FastTap (291):	0
	Synaptics Middle Button Timeout (292):	0
	Synaptics Two-Finger Pressure (293):	282
	Synaptics Two-Finger Width (294):	7
	Synaptics Scrolling Distance (295):	-107, -107
	Synaptics Edge Scrolling (296):	1, 0, 0
	Synaptics Two-Finger Scrolling (297):	1, 0
	Synaptics Move Speed (298):	0.100000, 1.700000, 0.015000, 40.000000
	Synaptics Edge Motion Pressure (299):	30, 160
	Synaptics Edge Motion Speed (300):	1, 430
	Synaptics Edge Motion Always (301):	0
	Synaptics Off (302):	2
	Synaptics Locked Drags (303):	0
	Synaptics Locked Drags Timeout (304):	5000
	Synaptics Tap Action (305):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (306):	1, 3, 0
	Synaptics Circular Scrolling (307):	0
	Synaptics Circular Scrolling Distance (308):	0.100000
	Synaptics Circular Scrolling Trigger (309):	0
	Synaptics Circular Pad (310):	0
	Synaptics Palm Detection (311):	1
	Synaptics Palm Dimensions (312):	10, 200
	Synaptics Coasting Speed (313):	20.000000, 50.000000
	Synaptics Pressure Motion (314):	30, 160
	Synaptics Pressure Motion Factor (315):	1.000000, 1.000000
	Synaptics Resolution Detect (316):	1
	Synaptics Grab Event Device (317):	1
	Synaptics Gestures (318):	1
	Synaptics Capabilities (319):	1, 0, 0, 1, 1, 1, 1
	Synaptics Pad Resolution (320):	71, 46
	Synaptics Area (321):	0, 0, 0, 0
	Synaptics Soft Button Areas (322):	3577, 0, 4164, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (323):	2, 2
	Device Product ID (250):	2, 7
	Device Node (251):	"/dev/input/event6"

```

Can anyone offer suggestions to tone down the jumpiness of the cursor when I attempt to tap to click?  After all of the various tweaks, I've still not found the right setting that improves that situation.

Thanks,
Craig

---

### Post by csete on 2013-06-09
I'm still testing, but this seems to have calmed things down a bit for me.  I had this set previously, but not quite so high.

```

xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Noise Cancellation" 20 20

```

---

### Post by virtualx on 2013-09-13
Unplug the power supply.   Do you still have the problem?  Call your manufacturer and ask for a better powersupply.   see: [http://ubuntuforums.org/showthread.php?t=898832](http://ubuntuforums.org/showthread.php?t=898832)

---

