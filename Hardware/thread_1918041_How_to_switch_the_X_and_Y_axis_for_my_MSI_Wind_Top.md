---
title: "How to switch the X and Y axis for my MSI Wind Top AE-1900"
date: 2012-01-31
forum: Hardware
---

### Post by w1z4rd on 2012-01-31
Hey folks,

Not sure if anyone here will be able to assist me, but let me give it a shot as I do not have many other options.

I was recently given a MSI Wind Top AE-1900. Its a fairly old piece of hardware but good enough to run Ubuntu. 

Everything seems to install okay, except the touchscreen. It works... but *** about face. IE, the X and Y axis are swapped around.

At first I thought it was a calibration issue so I installed xinput-calibrator. I basically followed the instructions as per here:

[http://www.thefanclub.co.za/how-to/how-ubuntu-1104-touchscreen-calibration](http://www.thefanclub.co.za/how-to/how-ubuntu-1104-touchscreen-calibration)

Well... they dont work for my situation.

Basically the instructions tell me to edit:

```
/usr/share/X11/xorg.conf.d/10-evdev.conf
```

Ive tried too add:

```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "Calibration" "59421 6041 57342 9557"
EndSection
```

&
```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "Calibration" "59421 6041 57342 9557"
        Option  "swapY" "1"
EndSection
```

&
```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option          "minX"          "59421"
        Option          "minY"          "6041"
        Option          "maxX"          "57342"
        Option          "maxY"          "9557"
        Option          "InvertY"         "true"
        Option          "InvertX"         "true"
EndSection

```
&
```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option          "minX"          "59421"
        Option          "minY"          "6041"
        Option          "maxX"          "57342"
        Option          "maxY"          "9557"
        Option  "swapY" "1"
EndSection
```

I am totally unable to swap the axiz no matter what settings I put there. I dont even know if its loading those settings or what the 100% correct format should be. 

I dont know what else to try... this should be a silly simple thing to get working.... and its not :(

---

