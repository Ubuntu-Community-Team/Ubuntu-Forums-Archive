---
title: "Lack of touch support for Lenovo x61t on 11.04"
date: 2011-04-29
forum: Hardware
---

### Post by marca311 on 2011-04-29
It seems that after I upgraded to 11.04 this morning, I could not use my touchscreen like I was used to. I tried using cutecom to get a serial dump of the touchscreen, but it seems that the screen is no longer mapped as a serial port if at all.
I can provide any details you need.
Thanks in advance

(At least I got rid of that Unity menu thing.)

---

### Post by marca311 on 2011-05-01
For the archive, this post helped

[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

---

### Post by mkjmkj on 2011-05-13
Hi marca311,

I, too, was taken aback by the loss of touch-support. But having read some of the thread that helped you I didn't feel like this was the right solution.
Now, this is what I found:
```
xsetwacom get 'Serial Wacom Tablet touch' all
```
gave me:
```

Option "Area" "55 95 942 933"
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "4"
Option "RawSample" "2"
Property 'Wacom Pressurecurve' does not exist on device.
Option "Mode" "Absolute"
Property 'Wacom Hover Click' does not exist on device.
[COLOR="Red"]Option "Touch" "off"[/COLOR]
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Option "Capacity" "-1"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "RawFilter" "on"
Option "Threshold" "27"
Option "ToolID" "292"
Option "ToolSerial" "0"
Option "TabletID" "147"

```
xsetwacoms manual page advised me to enter:
```

xsetwacom set 'Serial Wacom Tablet touch' Touch on

```
If I remember correctly touch worked just fine after this one-liner!
Since I didn't know where to activate option in order to activate touch each time I reboot I simply put it in my personal script for calibration of the touchscreen:
```

#!/bin/bash
# This script ought to configure touch and stylus functionality to my needs.
# by mkj

# Remap the side button to bring up context menu.
#xsetwacom set "Serial Wacom Tablet stylus" Button1 "button 1"
#xsetwacom set "Serial Wacom Tablet stylus" Button2 "button 3"

# Fix the "Serial Wacom Tablet eraser" button to paste
xsetwacom set "Serial Wacom Tablet eraser" Button 1 "button 2"

# Calibrate the touchscreen on multitouch X61
xsetwacom set 'Serial Wacom Tablet touch' Touch on
xsetwacom --set 'Serial Wacom Tablet touch' Area '55' '95' '942' '933'

# Calibrate the stylus
xsetwacom --set 'Serial Wacom Tablet stylus' Area '140' '50' '24600' '18428'

# Done

```
which I run on login.
This is not ideal because it doesn't activate touch for gdm! Does anybody have a better solution?

Anyways, hope this helps other X61t-users!

---

### Post by Favux on 2011-05-13
Hi mkjmkj,

The driver should have touch should on by default.

I wonder if adding an Option to the relevant serial snippet in 50-wacom.conf would work?
```
Option  "Touch"  "on"
```

---

### Post by mkjmkj on 2011-05-18
Hi Favux, unfortunately that didn't change anything. Not even an error in Xorg.0.log about that Option. Thanks anyways

---

