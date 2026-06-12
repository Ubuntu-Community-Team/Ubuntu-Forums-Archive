---
title: "Pointer speed too fast"
date: 2017-06-23
forum: Hardware
---

### Post by ajlongstreet on 2017-06-23
Hi folks,

I've tried a bunch of different remedies to no avail and the mouse speed is much too fast for me.

I'm hoping you guys have an idea on how to cut my pointer speed in half.

Ubuntu 17.04

```
misteraj@misteraj-Z87X-UD5H:~$ xinput -list-props 9Device 'Razer Razer Naga Hex':
    Device Enabled (153):    1
    Coordinate Transformation Matrix (155):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Natural Scrolling Enabled (292):    0
    libinput Natural Scrolling Enabled Default (293):    0
    libinput Send Events Modes Available (272):    1, 0
    libinput Send Events Mode Enabled (273):    0, 0
    libinput Send Events Mode Enabled Default (274):    0, 0
    Device Node (275):    "/dev/input/event15"
    Device Product ID (276):    5426, 65
    libinput Drag Lock Buttons (303):    <no items>
    libinput Horizontal Scroll Enabled (304):    1
misteraj@misteraj-Z87X-UD5H:~$ xinput -list-props 8
Device 'Razer Razer Naga Hex':
    Device Enabled (153):    1
    Coordinate Transformation Matrix (155):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Accel Speed (287):    0.000000
    libinput Accel Speed Default (288):    0.000000
    libinput Accel Profiles Available (289):    1, 1
    libinput Accel Profile Enabled (290):    1, 0
    libinput Accel Profile Enabled Default (291):    1, 0
    libinput Natural Scrolling Enabled (292):    0
    libinput Natural Scrolling Enabled Default (293):    0
    libinput Send Events Modes Available (272):    1, 0
    libinput Send Events Mode Enabled (273):    0, 0
    libinput Send Events Mode Enabled Default (274):    0, 0
    libinput Left Handed Enabled (294):    0
    libinput Left Handed Enabled Default (295):    0
    libinput Scroll Methods Available (296):    0, 0, 1
    libinput Scroll Method Enabled (297):    0, 0, 0
    libinput Scroll Method Enabled Default (298):    0, 0, 0
    libinput Button Scrolling Button (299):    2
    libinput Button Scrolling Button Default (300):    2
    libinput Middle Emulation Enabled (301):    0
    libinput Middle Emulation Enabled Default (302):    0
    Device Node (275):    "/dev/input/event14"
    Device Product ID (276):    5426, 65
    libinput Drag Lock Buttons (303):    <no items>
    libinput Horizontal Scroll Enabled (304):    1
misteraj@misteraj-Z87X-UD5H:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Naga Hex                        id=9    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Naga Hex                        id=8    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Orbweaver Chroma                id=11    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Orbweaver Chroma                id=12    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Ornata Chroma                   id=17    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Ornata Chroma                   id=19    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Razer Razer Naga Hex                        id=13    [slave  keyboard (3)]
    &#8627; Razer Razer Orbweaver Chroma                id=14    [slave  keyboard (3)]
    &#8627; Razer Razer Orbweaver Chroma                id=10    [slave  keyboard (3)]
    &#8627; Logitech Webcam C930e                       id=15    [slave  keyboard (3)]
    &#8627; Razer Razer Ornata Chroma                   id=16    [slave  keyboard (3)]
    &#8627; Razer Razer Ornata Chroma                   id=18    [slave  keyboard (3)]



```

---

### Post by Autodave on 2017-06-23
Have you tried the easy way by going into Settings -> Mouse & Touchpad -> Acceleration?

---

### Post by ajlongstreet on 2017-06-23
Unfortunately, I only have 3 options in that menu

Primary Button
Double-click
Pointer speed(already at min)

---

### Post by ajlongstreet on 2017-06-23
SOLVED!

I booted into Windows, lowered the DPI in the Razer app and increased the Windows pointer speed to compensate. Restarted back into Ubuntu and it works!!

500DPI in the Razer app and 1 tick left of max speed in Windows settings and Minimum pointer speed in Ubuntu. Seems to be the same speed in both Operating systems now!

---

### Post by pqwoerituytrueiwoq on 2017-06-25
This is the script i use to adjust my mouse speed to make a high dpi feel right (usable) to me
```
#!/bin/sh
ID=$(xinput list|grep MOUSE|sed 's/^.*id=//'|awk '{print $1}') # change MOUSE to a unique string that matched the device you are using
PROP=$(xinput list-props $ID|grep 'Device Accel Constant Deceleration'|sed 's/[(:)]//g'|awk '{print $5}')
xinput set-prop $ID $PROP 2.0
```
After looking up this script i noticed it had broke as my mouse no longer had HID where i changed it to MOUSE, maybe i don't need it anymore?
my moue has 3 dpi settings, 400, 800, and 1600, 800 is what feels right to me for normal use
by setting the value to 2.0 1600 feels like 800; 1600 at 1.0 it way too much for me to use

to me a 800 dpi mouse fells right on both ubuntu and windows under there default configurations

---

### Post by efflandt on 2017-06-26
I think it was Ubuntu 16.04 on that made the mouse more sensitive (acceleration 5 vs. 2) which may work fine for a mousepad, but too sensitive for a mouse. So I set a Startup Application to change acceleration for my mouse to 2, without affecting mousepad on alternate (wireless) keyboard (since wireless mice have no gui sensitivity adjustment).```
xinput --set-ptr-feedback 11 5 2 1
```

But I already knew that my mouse was id=11```
~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® SiderWinderTM X4 Keyboard    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech K400                               id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech MX Master                          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® SiderWinderTM X4 Keyboard    id=8    [slave  keyboard (3)]
```

---

### Post by ajlongstreet on 2017-06-26
Awesome, thanks for the info guys!

---

### Post by pamdemonia on 2017-07-21
Ubuntu forums, once again solving a problem I didn't even know I could solve!

thnanks

pam

---

