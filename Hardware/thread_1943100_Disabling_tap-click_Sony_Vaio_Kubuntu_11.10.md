---
title: "Disabling tap-click Sony Vaio Kubuntu 11.10"
date: 2012-03-18
forum: Hardware
---

### Post by fallenstar on 2012-03-18
Hi,

Looking through, this has been approached before, but the older workarounds [http://ubuntuforums.org/showthread.php?t=875016](http://ubuntuforums.org/showthread.php?t=875016) just don't apply, as HAL doesn't appear to exist, at least in my /etc/ folder.

Running Kubuntu 11.10 32 bit on a new Sony Vaio E Series.

I have disabled tapclick in the gui, everything involved in the touchpad doing anything but moving the cursor, I have dechecked, and yet it continues to work...

Is there a script I can adjust and make it go away forever? I still need the touchpad itself though...

Sorry for being a pain, this is my 5th OS attempting to get the backlight turned down, now it's dimmed (finally!) and I can't type as the curser buggers off...

---

### Post by Zorael on 2012-03-20
With **xinput**!

Note that your device name will probably be different from the "**Alps PS/2 ALPS DualPoint TouchPad**" that's used here -- likely something like "**SynPS/2 Synaptics TouchPad**". Your available options will probably vary too, both depending on your pad and on your version of **xserver-xorg-input-synaptics**.

```
zorael@laughlyn:~$ **xinput list**
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=12   [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=13   [slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                           id=15   [slave  pointer  (2)]
&#9116;   &#8627; **_AlpsPS/2 ALPS DualPoint TouchPad_          id=16**   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
[...]

zorael@laughlyn:~$ **xinput list-props "_AlpsPS/2 ALPS DualPoint TouchPad_"**
[i]# or by id 16, but id may change if you have more pointer devices attached when starting X
# so especially if in a script, better to refer to the device by name[/i]

Device 'AlpsPS/2 ALPS DualPoint TouchPad':
        Device Enabled (126):   1
        Coordinate Transformation Matrix (128): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (256):     1
        Device Accel Constant Deceleration (257):       2.500000
        Device Accel Adaptive Deceleration (258):       1.000000
        Device Accel Velocity Scaling (259):    12.500000
        Synaptics Edges (280):  300, 1700, 210, 1190
        Synaptics Finger (281): 90, 90, 999
        Synaptics Tap Time (282):       80
        Synaptics Tap Move (283):       120
        Synaptics Tap Durations (284):  20, 80, 80
        Synaptics Tap FastTap (285):    0
        Synaptics Middle Button Timeout (286):  75
        Synaptics Two-Finger Pressure (287):    141
        Synaptics Two-Finger Width (288):       7
        Synaptics Scrolling Distance (289):     40, 40
        Synaptics Edge Scrolling (290): 1, 1, 0
        Synaptics Two-Finger Scrolling (291):   0, 0
        Synaptics Move Speed (292):     0.300000, 1.650000, 0.050000, 0.000000
        Synaptics Edge Motion Pressure (293):   15, 80
        Synaptics Edge Motion Speed (294):      1, 195
        Synaptics Edge Motion Always (295):     0
        Synaptics Off (296):    0
        Synaptics Locked Drags (297):   0
        Synaptics Locked Drags Timeout (298):   5000
        **Synaptics Tap Action (299):     1, 1, 1, 1, 1, 2**
        Synaptics Click Action (300):   1, 1, 1
        Synaptics Circular Scrolling (301):     0
        Synaptics Circular Scrolling Distance (302):    0.100000
        Synaptics Circular Scrolling Trigger (303):     0
        Synaptics Circular Pad (304):   0
        Synaptics Palm Detection (305): 0
        Synaptics Palm Dimensions (306):        10, 100
        Synaptics Coasting Speed (307): 15.000000, 15.000000
        Synaptics Pressure Motion (308):                ... of unknown type CARDINAL
        Synaptics Pressure Motion Factor (309): 1.000000, 1.000000
        Synaptics Grab Event Device (310):      1
        Synaptics Gestures (311):       1
        Synaptics Capabilities (312):   1, 1, 1, 1, 1, 1, 0
        Synaptics Pad Resolution (313): 1, 1
        Synaptics Area (314):   0, 0, 0, 0
        Synaptics Noise Cancellation (315):     2, 2
        Device Product ID (245):        2, 8
        Device Node (246):      "/dev/input/event16"
```
From the man page of **synaptics**;
```
**Synaptics Tap Action**
       8 bit, up to MAX_TAP values (see synaptics.h), 0 disables an element. order: **[COLOR="DarkRed"]RT[/COLOR], [COLOR="DarkOrange"]RB[/COLOR], [COLOR="YellowGreen"]LT[/COLOR], [COLOR="Green"]LB[/COLOR], [COLOR="MediumTurquoise"]F1[/COLOR], [COLOR="RoyalBlue"]F2[/COLOR], [COLOR="Purple"]F3[/COLOR]**.
```
**[COLOR="DarkRed"]RT[/COLOR]** is right top corner, **[COLOR="DarkOrange"]RB[/COLOR]** right bottom corner, **[COLOR="YellowGreen"]LT[/COLOR]** left top corner, **[COLOR="Green"]LB[/COLOR]** left bottom corner, **[COLOR="MediumTurquoise"]F1[/COLOR]** non-corner one finger tap, **[COLOR="RoyalBlue"]F2[/COLOR]** non-corner two finger tap, **[COLOR="Purple"]F3[/COLOR]** non-corner three finger tap.

So to disable all taps everywhere with any number of fingers;
```
$ xinput set-prop "AlpsPS/2 ALPS DualPoint TouchPad" "Synaptics Tap Action" **[COLOR="DarkRed"]0[/COLOR] [COLOR="DarkOrange"]0[/COLOR] [COLOR="YellowGreen"]0[/COLOR] [COLOR="SeaGreen"]0[/COLOR] [COLOR="MediumTurquoise"]0[/COLOR] [COLOR="RoyalBlue"]0[/COLOR] [COLOR="Purple"]0[/COLOR]**
```

An example of an easy-to-maintain script with which you can set properties;
```
[I]#!/bin/bash
# this script sets some touchpad settings
# see 'man synaptics' for information about properties[/i]

DEVICE=**"AlpsPS/2 ALPS DualPoint TouchPad"**  *# change to match your device name*
DELAY=0.1


**[COLOR="Teal"]setprop()[/COLOR]** {
    [I]# sets a property.
    # arg $1: property name, rest ($@) are property values[/I]

    local property="$1"
    *# we've saved $1 in $property, so shift it away so only the values remain*
    shift

    *# print what we're doing*
    [B]echo "-- ${property}: "$@""
    xinput set-prop "$DEVICE" "$property" "$@"[/B]
    errlvl=$?

    *# check if the xinput command output errors and if so, call err() to exit*
    [ $errlvl -gt 0 ] && **[COLOR="darkred"]err[/COLOR]** $? "$property" "$@"

    [I]# pausing a bit to let the driver do its thing
    # some time ago doing this too fast could muck stuff up royally[/I]
    sleep $DELAY
}


**[COLOR="darkred"]err()[/COLOR]** {
    [I]# spouts an error and exits.
    # arg $1: errorlevel, arg $2: property name, rest ($@) are property values[/I]

    local errlvl=$1
    local property="$2"
    *# shift away $1 and $2 so only the values remain*
    shift 2

    echo *# padding*
    echo "ERROR: xinput threw errorlevel $errlvl when trying to set property \"$property\" with values: "$@""
    exit $errlvl   *# end script*
}


# ------ execution start

echo "Pad settings for ${DEVICE}:"
*# list available properties with 'xinput list-props "$DEVICE"'*

[COLOR="Teal"]**setprop[/COLOR] "Synaptics Tap Action"  [COLOR="DarkRed"]0[/COLOR]  [COLOR="DarkOrange"]0[/COLOR]  [COLOR="YellowGreen"]0[/COLOR]  [COLOR="SeaGreen"]0[/COLOR]  [COLOR="MediumTurquoise"]0[/COLOR]  [COLOR="RoyalBlue"]0[/COLOR]  [COLOR="Purple"]0[/COLOR]**
*# 0 disables an element. order: **[COLOR="DarkRed"]RT[/COLOR] [COLOR="DarkOrange"]RB[/COLOR] [COLOR="YellowGreen"]LT[/COLOR] [COLOR="SeaGreen"]LB[/COLOR] [COLOR="MediumTurquoise"]F1[/COLOR] [COLOR="RoyalBlue"]F2[/COLOR] [COLOR="Purple"]F3[/COLOR]**.*

[COLOR="Teal"]**setprop[/COLOR] "Synaptics Edge Scrolling" [COLOR="Navy"]1[/COLOR] [COLOR="Magenta"]1[/COLOR] [COLOR="DarkSlateBlue"]0[/COLOR]**
*# 3 values, **[COLOR="Navy"]vertical[/COLOR], [COLOR="Magenta"]horizontal[/COLOR], [COLOR="DarkSlateBlue"]corner[/COLOR]**.*

[COLOR="Teal"]**setprop[/COLOR] "Synaptics Coasting Speed" [COLOR="Lime"]15[/COLOR] [COLOR="Sienna"]15[/COLOR]**
*# FLOAT, 2 values, **[COLOR="Lime"]speed[/COLOR], [COLOR="Sienna"]friction[/COLOR]***

#setprop "Synaptics PROPERTYNAME" value1 value2 value3 ...
```
This is more or less what I use, but I set some additional values (Move Speed, Noise Cancellation, etc) -- and I certainly don't disable taps. D:

Save it as executable in **~/.config/autostart/**, or in **~/.kde/Autostart/**, or wherever as long as it ends up being run upon X start.

---

