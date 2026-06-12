---
title: "Problems calibrating touchscreen"
date: 2015-08-24
forum: Hardware
---

### Post by famousignoramus on 2015-08-24
I've spent some time trying to calibrate my touchscreen, but without any luck.

I started by using xinput to set it using the output from xinput_colibrator, but it says it can't find the device name as there are multiple instances.

Bit more Googling, switched to putting the settings into evdev, specifically /usr/share/X11/xorg.conf.d/10-evdev.conf :

```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "Calibration" "32 1656 1652 2568 2552"
EndSection
```

Seems to be better, but the axes are definitely flipped, so I try:

```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "InvertX" "true"
        Option "InvertY" "true"

        Option "Calibration" "32 1656 1652 2568 2552"
EndSection
```

...no joy. More Googling says this is the way to do it:


```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "SwapAxes" "1"
        Option "Calibration" "32 1656 1652 2568 2552"
EndSection
```

But still nothing. What can I try next?

---

### Post by famousignoramus on 2015-08-26
No responses... is there a better place for this post maybe?

---

