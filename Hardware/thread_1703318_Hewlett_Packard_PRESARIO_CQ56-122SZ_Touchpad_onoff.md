---
title: "Hewlett Packard PRESARIO CQ56-122SZ Touchpad on/off"
date: 2011-03-09
forum: Hardware
---

### Post by poljpocket on 2011-03-09
Hi everybody,

I got an Hewlett Packard PRESARIO CQ56-122SZ laptop which I use for programming when travelling and which I like a lot.

First - of course - there was Windows 7 Home Premium on it, which I wiped out as fast I could ;-) There were many drivers including a trackpad driver which let me disable/enable the trackpad via a button placed on the upper left edge of the trackpad. I had to double click this region of the trackpad and the device would be disabled (the Windows sound of removing a device was played) and a red light would come up on the "button".

Now I wonder if there is a possibility to get this functionality to Ubuntu (10.10 x64). It seems Ubuntu doesn't recognize the region as a button since the button is actually ON the trackpad itself. I can move the pointer when moving my finger over this region, but the speed is lowered (maybe to enable the driver recognizing the clicks there better since there's less movement registered).

I analyzed the device as follows:

```

~$ xinput list | grep TouchPad
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
~$ xinput list-props 13
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (125):    1
    Coordinate Transformation Matrix (127):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (252):    0
    Device Accel Constant Deceleration (253):    1.000000
    Device Accel Adaptive Deceleration (254):    1.000000
    Device Accel Velocity Scaling (255):    10.000000
    Synaptics Edges (271):    1781, 5579, 1648, 4604
    Synaptics Finger (272):    24, 29, 255
    Synaptics Tap Time (273):    180
    Synaptics Tap Move (274):    246
    Synaptics Tap Durations (275):    180, 180, 100
    Synaptics Tap FastTap (276):    0
    Synaptics Middle Button Timeout (277):    75
    Synaptics Two-Finger Pressure (278):    280
    Synaptics Two-Finger Width (279):    7
    Synaptics Scrolling Distance (280):    111, 111
    Synaptics Edge Scrolling (281):    1, 1, 0
    Synaptics Two-Finger Scrolling (282):    0, 0
    Synaptics Move Speed (283):    0.400000, 0.700000, 0.008937, 40.000000
    Synaptics Edge Motion Pressure (284):    29, 159
    Synaptics Edge Motion Speed (285):    1, 447
    Synaptics Edge Motion Always (286):    0
    Synaptics Button Scrolling (287):    1, 1
    Synaptics Button Scrolling Repeat (288):    1, 1
    Synaptics Button Scrolling Time (289):    100
    Synaptics Off (290):    0
    Synaptics Guestmouse Off (291):    0
    Synaptics Locked Drags (292):    0
    Synaptics Locked Drags Timeout (293):    5000
    Synaptics Tap Action (294):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (295):    1, 1, 2
    Synaptics Circular Scrolling (296):    0
    Synaptics Circular Scrolling Distance (297):    0.100000
    Synaptics Circular Scrolling Trigger (298):    0
    Synaptics Circular Pad (299):    0
    Synaptics Palm Detection (300):    0
    Synaptics Palm Dimensions (301):    10, 199
    Synaptics Coasting Speed (302):    0.000000
    Synaptics Pressure Motion (303):    29, 159
    Synaptics Pressure Motion Factor (304):    1.000000, 1.000000
    Synaptics Grab Event Device (305):    1
    Synaptics Gestures (306):    1
    Synaptics Capabilities (307):    1, 0, 1, 0, 0
    Synaptics Pad Resolution (308):    90, 58
    Synaptics Area (309):    0, 0, 0, 0
    Synaptics Jumpy Cursor Threshold (310):    0

```With xinput test I tested the device. It seems that taps aren't recognized on the region where the on/off button is. Taps there are just registered as small movements.

I can assing edge clicks to the region as I could in all other three edges without problems.

Now my question: Can I assign an edge click to some script or program? Has Ubuntu integrated functionality to turn trackpads on/off by keystroke?


Thanks in advance, cheers Julian

---

### Post by pslat on 2011-05-08
Hi Julian, I couldn't find any info on using the top left pad area on  the CQ56 to enable / disable the keypad but since you didn't get any replies, - I just use a script that toggles  the pad on or off. I added a menu item with menu  editor and set a keyboard shortcut of ctrl+alt+t. Pressing the key combination turns on or off the touchpad when I want. The only problem is it asks  for your password but I don't find that a problem, especially compared to trying to type with the pad enabled. Note that it does not affect an external mouse if attached.
Here's the script:
```

#!/bin/sh
#Script to enable/disable the touchpad (touchpad.sh)
if [ $(lsmod | grep psmouse | wc -l) -eq 0 ]
then
    gksudo "modprobe -i psmouse"

else
    gksudo "modprobe -i psmouse"
 
fi
exit 0

```I know it's not what you're looking for but thought it might be useful for some Presario users.

---

### Post by jncneo on 2011-06-27
Hi everybody. I also have CQ56 with the same problem. Good news are that I bought it with SUSE pre-installed and touchpad button was working there - so there is a solution ;)

While I was trying to find it I was able to find few interesting things. First is that there is a possibility to turn on/off touchpad using command:

```

command&#65306;synclient touchpadoff=1 &#65293; disable touchpad

command&#65306;synclient touchpadoff=0 &#65293; enable touchpad

```

(this article helped me: [http://www.linuxine.com/2008/06/how-to-disable-touchpad-in-ubuntu.html](http://www.linuxine.com/2008/06/how-to-disable-touchpad-in-ubuntu.html))

And the second nice thing I found using xev - it looks like kernel reacts on double-click on top left corner:


KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967215 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

I'm not sure in second one but I hope I'm right :)

---

