---
title: "Wacom tablet help?"
date: 2012-12-15
forum: Hardware
---

### Post by Senabun on 2012-12-15
I have an old Wacom CTE-440 and Bamboo Fun tablets.
I've tried installing the driver for them, file name "xf86-input-wacom-0.17.0", yet I don't know how to successfully get it to work. 

At this moment, there's:
-No pen pressure
-Hyper recognition (I can hover, not touch, my pen above the tablet and it'll recognize it as if it's being touched) 
-I have the Graphics Tablet setting on Linux, however, it doesn't help for my problems

I /really/ miss drawing and coloring on the computer. =( Please help.

I'm using Ubuntu 11.10 32-bit

---

### Post by Favux on 2012-12-15
Hi Senabun,

Your model should work out of the box in Oneiric.

Is pressure absent in all applications or just some like Gimp and/or Inkscape?

What is the output of the following commands, run in a terminal, with the tablet plugged in?
```
lsusb

xinput list
```

---

### Post by Senabun on 2012-12-15
In Gimp, the pressure doesn't work. Though, it still doesn't explain why the pen is being recognized when not touching the tablet itself. 

When I put your code in, this is what it says. I have other usb connections in the other ports. 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 154b:000d PNY 
Bus 002 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 002 Device 004: ID 14cd:121c Super Top microSD card reader
Bus 005 Device 003: ID 056a:0015 Wacom Co., Ltd Graphire 4 4x5

---

### Post by Favux on 2012-12-15
Okay, the **xinput list** output would be helpful for the proximity problem.

In some applications you have to configure the extended input device such ast in Gimp and Inkscape.

For Gimp go to:  Edit > Preferences > Input Devices.  Click on the "Configure Extended Input Devices" button.  In the "Device:" drop down menu select the stylus and change it to 'Screen' in the "Mode:" drop down menu.  Do the same for eraser if you have one.

---

### Post by Senabun on 2012-12-15
My apologies. I thought I included the xinput list.

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 stylus                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 eraser                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 cursor                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 pad                     id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]
    &#8627; ENE eHome Infrared Remote Receiver          id=14    [slave  keyboard (3)]

---

### Post by Favux on 2012-12-15
So for proximity let's see what **list-props** tells us.  Run this command in a terminal and post the output.
```
xinput list-props 15
```
We're using the ID # of the stylus from **xinput list** as a shortcut but that can change if you hot plug or restart.

---

### Post by Senabun on 2012-12-15
Device 'Wacom Graphire4 4x5 stylus':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (238):    0
    Device Accel Constant Deceleration (239):    1.000000
    Device Accel Adaptive Deceleration (240):    1.000000
    Device Accel Velocity Scaling (241):    10.000000
    Wacom Tablet Area (730):    0, 0, 10208, 7424
    Wacom Rotation (731):    3
    Wacom Pressurecurve (732):    0, 0, 100, 100
    Wacom Serial IDs (733):    21, 0, 2, 0
    Wacom Capacity (734):    -1
    Wacom Pressure Threshold (735):    27
    Wacom Sample and Suppress (736):    2, 4
    Wacom Enable Touch (737):    1
    Wacom Hover Click (738):    1
    Wacom Enable Touch Gesture (739):    0
    Wacom Touch Gesture Parameters (740):    50, 20, 250
    Wacom Tool Type (741):    "STYLUS" (363)
    Wacom Button Actions (742):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (743):    0, 0

---

### Post by Favux on 2012-12-15
So the pen is drawing lines even when not in contact with the tablet?  How far away can it be for that to happen?

The CursorProx parameter is only suppose to apply the the Graphire's puck/wacom tablet mouse.  But I dimly recall there may have been some issue.  Hmm.

Let's see what xsetwacom has to tell us about the current parameters on the stylus.
```
xsetwacom get "Wacom Graphire4 4x5 stylus" all
```

---

### Post by Senabun on 2012-12-15
It can be about an inch away from the tablet, and be recognized. I tried my tablet on my friend's Windows computer a couple of days ago, and it worked fine. 

Option "Area" "0 0 10208 7424"
'Button' requires exactly 1 value(s).
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "2"
Option "RawSample" "4"
Option "PressureCurve" "0 0 100 100"
Option "Mode" "Absolute"
Option "TabletPCButton" "on"
Option "Touch" "on"
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Option "Capacity" "-1"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "half"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "Threshold" "27"
Option "ToolID" ""
Option "ToolSerial" ""
Option "TabletID" ""

It seems like now when I hover above or touch the tablet, the pen direction is opposite from the direction I'm going unless I turn my tablet upside down. However, I think that may be an issue with the pen itself. Thanks so much for all the help thus far, btw.

---

### Post by Favux on 2012-12-15
Not a problem.

> I tried my tablet on my friend's Windows computer a couple of days ago, and it worked fine. 
Good, you've established it is not a hardware problem with your tablet's proximity sensing.

Unfortunately still drawing a blank on where and when I saw this issue before, if I did.

My suggestion would be to update xf86-input-wacom (the xserver-xorg-input-wacom package) to the latest release or clone it.  Part II. of the [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408") will tell you how to do either, or you could use this [older version]("http://ubuntuforums.org/showthread.php?t=1515562") if you also apply the updated information in post # 1081:  [http://ubuntuforums.org/showpost.php?p=12374240&postcount=1081](http://ubuntuforums.org/showpost.php?p=12374240&postcount=1081)  If that alone doesn't do the trick we can also try updating the kernel driver wacom.ko using input-wacom (part I.).

---

### Post by Senabun on 2012-12-15
I'll give your suggestions a go. I'm pretty illiterate when it comes to Linux still, so hopefully I do things right! Thanks!

---

### Post by Favux on 2012-12-15
Alright.  Ask if you have questions.

By the way do you still see the proximity issue when you don't have the tablet rotated to left-handed?

---

