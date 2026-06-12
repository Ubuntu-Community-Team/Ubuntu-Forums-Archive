---
title: "Touch Screen input in Portrait mode- Has anyone done this?"
date: 2012-11-08
forum: Hardware
---

### Post by GeneralShenanigans on 2012-11-08
I've been trying to get a touch screen monitor working in Xubuntu for the past few weeks. The device is a Planar PX2230MW. I have written a bash script that allows me to enable the monitor, enable touch screen input, and mirror the primary display to the TS monitor. However, this only seems to work in landscape orientation.

Below is my current script:
```
#!/bin/bash

REGULAR_MONITOR=VGA-1
TOUCHSCREEN_MONITOR=DVI-I-1

# Load the touchscreen module
modprobe hid-multitouch
echo 3 0408 3001 104 > /sys/module/hid_multitouch/drivers/hid\:hid-multitouch/new_id

# Enable the touchscreen display
xrandr --output $TOUCHSCREEN_MONITOR --auto --output $REGULAR_MONITOR --auto

# Enable touchscreen input with CTM for landscape (0* rotation)
xinput set-prop "QUANTA OpticalTouchScreen" --type=float "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1

exit 0

```

I have tried a few options for rotating the screen (and subsequently, its input) 90 degrees clockwise, but I've had issues:

If I change the xrandr/xinput commands to the following: ```
xrandr --output $TOUCHSCREEN_MONITOR --auto --rotate left --output $REGULAR_MONITOR --auto
# Enable touchscreen input with CTM for 90* cw rotation
xinput set-prop "QUANTA OpticalTouchScreen" --type=float "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1

```

I determined this CTM to be correct after much research. With this, X renders the screen correctly on the TS monitor, and rotated touch input *mostly* works, but it appears there is a bug where the touch input jumps around between the actual touch location, and another location (which I would assume is the where the touch input would be if the X screen was in portrait mode but the TS input was still being processed as landscape). 

Apparently there is a documented bug somewhere in the bowels of the internet, which I'm unable to find at the moment.

Has anyone successfully gotten rotated touch screen input calibrated correctly?

---

### Post by Favux on 2012-11-08
Hi GeneralShenanigans,

Welcome to Ubuntu forums!


> there is a bug where the touch input jumps around between the actual touch location, and another location
That sounds very familiar.

Right, there was a X Server bug that was affecting CTM with xf86-input-evdev.  I assume your touchscreen uses the evdev driver?  Since that was affecting graphics tablets the [DIGI*mend* project]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend") supports Nick reported it bugzilla.  That was fixed for X Server 1.13.  I believe the bug report you are referring to is:  [https://bugs.freedesktop.org/show_bug.cgi?id=49347](https://bugs.freedesktop.org/show_bug.cgi?id=49347)

However I have a graphics tablet user reporting that while the fix works in landscape the problem reappears as soon as he rotates a monitor with CTM.  His tablet pen uses the evdev driver's tablet snippet.  I think I also just got a N-Trig (touch on evdev) reporting the same problem when screen orientation changed with rotation and CTM applied to rotate touch.  It is looking like the valuator mask fix only partially addressed the issue.

Sounds like a new bug report needs to be filed for the rotation problem, citing the old one, and cc'ing Peter.

---

### Post by Favux on 2012-11-09
Rereading the bug report thread just realized a patch for touchscreens was submitted yesterday by Yuly Novikov.  Don't know if that works after a rotation.

---

