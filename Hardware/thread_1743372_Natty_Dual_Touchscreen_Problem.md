---
title: "Natty Dual Touchscreen Problem"
date: 2011-04-29
forum: Hardware
---

### Post by LinceptDJ on 2011-04-29
Hi,
anyone tried using 2 touchscreens on Natty?
It was quite a hassle on 10.10, but community help for older versions helped to success.

Using a single touchscreen (Acer T230H) works fine, but as soon as the 2nd one is added, calibration is messed up - from each touchscreen the mouse pointer would move through the whole virtual desktop size of 3840px over both displays - like the mouse. On 10.10, with the calibration set up in xorg.conf, each touchscreen would control only its own display (1920px wide), not both ...

10.10 has xorg 1.9.0, 11.04 comes with 1.10.1. I did a clean new install from the 64-bit ISO. In Natty touch-behaviour, there is no difference between the free radeon driver and the ATI prop driver for my Radeon 4600 install. 

On 10.10, my xorg.conf would have the following entries:

```

Section "ServerLayout"
        Identifier     "1Screen Layout"
        Screen      0  "screen0" 0 0
        InputDevice    "touch0"
        InputDevice    "touch1"
EndSection

Section "InputDevice"
        Identifier  "touch0"
        Driver      "evdev"
        Option      "Device" "/dev/input/event5"
        Option      "Calibration" "0 3840 0 1080"
EndSection

Section "InputDevice"
        Identifier  "touch1"
        Driver      "evdev"
        Option      "Device" "/dev/input/event6"
        Option      "Calibration" "-1920 1920 0 1080"
EndSection

```

On Natty, the Xorg-log would show in the evdev/touchscreen-section the following warning:
```

[    12.849] (WW) Touch X valuator does not match pointer X valuator, pointer em
ulation may be incorrect
[    12.849] (WW) Touch Y valuator does not match pointer Y valuator, pointer em
ulation may be incorrect

```

Comparing the 10.10-Xorg-log, I could not find any other new/unusual messages ...

Anyone any idea why this is not working anymore?

---

### Post by LinceptDJ on 2011-04-30
Never mind why calibration option has no effect anymore - found a solution in changig the "Coordinate Transformation Matrix", thks to [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation):

```

xinput set-prop 'touch0' 'Coordinate Transformation Matrix' 0.5 0 0 0 1 0 0 0 1
xinput set-prop 'touch1' 'Coordinate Transformation Matrix' 0.5 0 0.5 0 1 0  0 0 1

```

---

### Post by dkzeb on 2011-05-01
do you have multitouch support for the Acer t230h? or is it just single?

---

### Post by rongrimes on 2011-06-20
A related question for an Acer T230H touchscreen. It's working (connects  and produces screen actions) on Natty with the standard drivers.  However I run a dual desktop from a laptop and I can't get the  Touchscreen to accurately show where the touch location is. The laptop  is 1366 wide and the T230H is 1920 (total 3286 wide) with the T230H to  the RIGHT of the laptop. If I touch on the left side  of the T230H, the  cursor appears on the left of the LAPTOP screen, if I touch the middle  of the T230H the cursor appears half way across the double screen width -  I touch at 960 (centre of the touchscreen), and the cursor appears at  (1366+1920)/2 = 1643 from the left of the laptop.

There is no xorg.conf files as such, but there is the directory  /usr/share/X11/xorg.conf.d, and I've put a file in there: 60-t230h.conf  with the following:

> 
Section "InputDevice"
# I added this for touchscreen T230H
 Identifier      "Acer T230H"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
#Option          "Device"                "/dev/usb/quanta_touch"
 Option          "Device"                "/dev/usb/hiddev0"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
#Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftX"        "1366"
 Option          "CornerTopLeftY"        "0"
#Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightX"       "3286" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
#Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftX"     "1366"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
#Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightX"    "3286" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

Section "ServerLayout"
# I added this for touchscreen T230H
        Identifier "Touchscreen"
        InputDevice "Acer T230H" "SendCoreEvents"
EndSection
(I'm quite green in the finer points of xorg.conf... )

Also, I get the following from xinput:
> 
 xinput list "Acer T230H"
Acer T230H                                  id=14    [slave  pointer  (2)]
    Reporting 6 classes:
        Class originated from: 14
        Buttons supported: 5
        Button labels: Button Unknown Button Unknown Button Unknown Button Wheel Up Button Wheel Down
        Button state:
        Class originated from: 14
        Detail for Valuator 0:
          Label: Abs X
          Range: 0.000000 - 1920.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 1643.000000
        Class originated from: 14
        Detail for Valuator 1:
          Label: Abs Y
          Range: 0.000000 - 1080.000000
          Resolution: 10000 units/m
          Mode: absolute
          Current value: 540.000000
        Class originated from: 14
        Multitouch capable (max 20 touches):
          Mode: Direct Touch
        Class originated from: 14
        Detail for Touch Valuator 0:
          Label: Abs MT Position X
          Range: 0.000000 - 1920.000000
          Resolution: 0 units/m
        Class originated from: 14
        Detail for Touch Valuator 1:
          Label: Abs MT Position Y
          Range: 0.000000 - 1080.000000
          Resolution: 0 units/m
Does anyone have any insights on configuring this setup?

Thanks for any help offered.

---

### Post by rongrimes on 2011-06-24
OK, got it! I re-read [LinceptDJ]("http://ubuntuforums.org/member.php?u=1290240") above (April 30, 2011), and started working with *xinput*. A play around with the numbers gave me exactly what I need, and I'll now add an *xinput* line to my .*bashrc* (see next post).

To recap:

[LIST=1]
[*]Playing with **xorg** did nothing for me! The touchscreen worked "out of the box" with Natty, so that part was easy.
[*]I followed the instructions at: [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation): and this led me to the solution.
[/LIST]
**Environment:**
Laptop on left, screen width 1366, T230H on right width 1920.

I ran *xinput* with the new values, and it currently shows:

> 
xinput list-props "Acer T230H" | grep "Coordinate"

Coordinate Transformation Matrix (127):    0.584300, 0.000000, 0.415700, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
0.5843 = 1920 / (1366 + 1920)

0.4157 = 1366 / (1366 + 1920)
(= offset of Touchscreen from left margin of laptop)

Hope this is of use to someone!

Thanks [LinceptDJ]("http://ubuntuforums.org/member.php?u=1290240") for the inspiration!

---

### Post by rongrimes on 2011-06-27
My .bashrc code to configure the Acer T230H (see notes in previous post):

> 
# Touchscreen Matrix calculations
# Laptop on left, screen width 1366, T230H on right width 1920.
# See: [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation)
#
# 0.5843 = 1920 / (1366 + 1920)
# 0.4157 = 1366 / (1366 + 1920) (= offset from Touchscreen from left margin of laptop)

echo

if xinput -list-props "Acer T230H" 2>&1 | grep "Device Enabled" | grep "1$" > /dev/null
then[INDENT]     xinput set-prop "Acer T230H" "Coordinate Transformation Matrix" 0.5843 0 0.4157 0 1 0 0 0 1
[/INDENT][INDENT]     echo Touch Screen configured
[/INDENT]else[INDENT]     echo Touch Screen not connected
[/INDENT]fi

echo


---

### Post by LSenf on 2011-07-21
Thanks, this works perfectly!

However, there is one problem. Despite the mouse position being detected correctly, utouch (which I use through touchegg -> [https://code.google.com/p/touchegg/issues/detail?id=82](https://code.google.com/p/touchegg/issues/detail?id=82)) seems to remain unaffected by the xinput transformation change.

So, a touchegg action is actually performed where the mouse would have been without the transformation adjustment.

Do you have any idea how to make this adjustment work for utouch?

---

### Post by godsbane on 2011-11-02
I have this same monitor - next to an older similarly sized monitor with a different aspect ratio.

The one to the left is a 24 inch Samsung that is 1920 x 1200

the one on the right is the Acer t230h which is 1920 x 1080

xinput set-prop 'Acer T230H' 'Coordinate Transformation Matrix' 0.5 0 0.5 0 1 0 0 0 1

works for me horizontally, however when i get to the bottom of the screen it actually goes beyond, to the 1200'th pixel which doesn't exist. I assume i need to tweak the matrix, but for the life of me i couldn't figure out the values for the y axis.

1080/1200 = .9 as a multiplier?

---

