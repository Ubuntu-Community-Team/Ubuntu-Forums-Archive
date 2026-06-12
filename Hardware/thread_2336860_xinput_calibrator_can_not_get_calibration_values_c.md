---
title: "xinput_calibrator can not get calibration values correctly"
date: 2016-09-12
forum: Hardware
---

### Post by shao-chi on 2016-09-12
Hi everybody,
     I use xinput_calibrator tool to calibrate touch screen that can working properly on ubuntu 12.04, but not on ubuntu 14.04.

Here are output with debug mode:

Ubuntu 12.04 

```
~$ xinput_calibrator -v --device "SAMDE THEOE"
DEBUG: XInputExtension version is 2.3
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Selected device: SAMDE THEOE
DEBUG: Not usbtouchscreen calibrator: Not a usbtouchscreen device
DEBUG: Evdev Axis Calibration not set, setting to axis valuators to be sure.
DEBUG: Successfully applied axis calibration.
DEBUG: Read axes swap value of 0.
Calibrating EVDEV driver for "SAMDE THEOE" id=10
    current calibration values (from XInput): min_x=0, max_x=32767 and min_y=0, max_y=32767
DEBUG: Adding click 0 (X=135, Y=1677)
DEBUG: Adding click 1 (X=141, Y=237)
DEBUG: Adding click 2 (X=935, Y=1688)
DEBUG: Mis-click detected, click 3 (X=942, Y=259) not aligned with click 1 (X=141, Y=237) or click 2 (X=935, Y=1688) (threshold=15)
DEBUG: Adding click 0 (X=134, Y=1688)
DEBUG: Adding click 1 (X=135, Y=253)
DEBUG: Adding click 2 (X=945, Y=1677)
DEBUG: Adding click 3 (X=942, Y=248)


Doing dynamic recalibration:
    Swapping X and Y axis...
DEBUG: Successfully swapped X and Y axis.
    Setting new calibration data: 202, 32786, 32715, -10
DEBUG: Successfully applied axis calibration.




--> Making the calibration permanent <--
DEBUG: Found that 'SAMDE THEOE' is a sysfs name.
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
    Identifier  "calibration"
    MatchProduct    "SAMDE THEOE"
    Option  "Calibration"   "202 32786 32715 -10"
    Option  "SwapAxes"  "1"
EndSection

```

Ubuntu 14.04

```
~$ xinput_calibrator -v --device "SAMDE THEOE"
DEBUG: XInputExtension version is 2.3
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Selected device: SAMDE THEOE
DEBUG: Not usbtouchscreen calibrator: Not a usbtouchscreen device
DEBUG: Read axes swap value of 1.
DEBUG: Read InvertX=0, InvertY=0.
Calibrating EVDEV driver for "SAMDE THEOE" id=9
        current calibration values (from XInput): min_x=29013, max_x=28993 and min_y=23487, max_y=23566
DEBUG: Found that 'SAMDE THEOE' is a sysfs name.
DEBUG: Adding click 0 (X=1079, Y=0)
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Adding click 1 (X=1079, Y=1919)
DEBUG: Not adding click 2 (X=1079, Y=1919): within 7 pixels of previous click
DEBUG: Not adding click 2 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 2 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Adding click 2 (X=0, Y=0)
DEBUG: Not adding click 3 (X=1079, Y=1919): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=1919): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=0, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=0, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=0, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=0, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=0, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=1919): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Not adding click 3 (X=1079, Y=0): within 7 pixels of previous click
DEBUG: Mis-click detected, click 3 (X=701, Y=0) not aligned with click 1 (X=1079, Y=1919) or click 2 (X=0, Y=0) (threshold=15)



```

I noticed that the calibration values are different on unbuntu 12.04 and 14.04. 
The value of min_x large then max_x on 14.04, I thought that are not correct calibration values.
Any one can help me to correct it? 
Any suggestions are welcome.

---

### Post by shao-chi on 2016-09-12
I add parameter (precalib) to xinput_calibrator, and test again.

Here is first output:

```
~$ xinput_calibrator -v --precalib 0 32767 0 32767 --device "SAMDE THEOE"
DEBUG: XInputExtension version is 2.3
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Selected device: SAMDE THEOE
DEBUG: Setting precalibration: 0, 32767, 0, 32767
DEBUG: Not usbtouchscreen calibrator: Not a usbtouchscreen device
DEBUG: Evdev Axis Calibration not set, setting to axis valuators to be sure.
        Setting calibration data: 0, 32767, 0, 32767
DEBUG: Successfully applied axis calibration.
DEBUG: Read axes swap value of 0.
DEBUG: Read InvertX=0, InvertY=0.
Calibrating EVDEV driver for "SAMDE THEOE" id=10
        current calibration values (from XInput): min_x=0, max_x=32767 and min_y=0, max_y=32767
DEBUG: Found that 'SAMDE THEOE' is a sysfs name.
DEBUG: Adding click 0 (X=139, Y=1655)
DEBUG: Adding click 1 (X=137, Y=248)
DEBUG: Adding click 2 (X=942, Y=1666)
DEBUG: Adding click 3 (X=931, Y=253)


Doing dynamic recalibration:
        Swapping X and Y axis...
DEBUG: Successfully set swapped X and Y axes = 1.
        Setting calibration data: 28828, 29152, 9243, 9095
DEBUG: Successfully applied axis calibration.
        --> Making the calibration permanent <--
DEBUG: Found that 'SAMDE THEOE' is a sysfs name.
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf' (/usr/share/X11/xorg.conf.d/ in some distro's)
Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "SAMDE THEOE"
        Option  "Calibration"   "28828 29152 9243 9095"
        Option  "SwapAxes"      "1"
EndSection

```
The calibration values are correct at first time, but not working when do second calibration.

```
~$ xinput_calibrator -v --precalib 0 32767 0 32767 --device "SAMDE THEOE"
DEBUG: XInputExtension version is 2.3
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Selected device: SAMDE THEOE
DEBUG: Setting precalibration: 0, 32767, 0, 32767
DEBUG: Not usbtouchscreen calibrator: Not a usbtouchscreen device
DEBUG: Read axes swap value of 1.
DEBUG: Read InvertX=0, InvertY=0.
Calibrating EVDEV driver for "SAMDE THEOE" id=10
        current calibration values (from XInput): min_x=28828, max_x=29152 and min_y=9243, max_y=9095
DEBUG: Found that 'SAMDE THEOE' is a sysfs name.
DEBUG: Adding click 0 (X=573, Y=1919)
DEBUG: Adding click 1 (X=0, Y=1919)
DEBUG: Mis-click detected, click 2 (X=259, Y=0) not aligned with click 0 (X=573, Y=1919) or click 1 (X=0, Y=1919) (threshold=15)
DEBUG: Adding click 0 (X=0, Y=1919)
DEBUG: Not adding click 1 (X=0, Y=1919): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=0, Y=1919): within 7 pixels of previous click
DEBUG: Not adding click 1 (X=0, Y=1919): within 7 pixels of previous click

```
It just working at first boot.

---

### Post by ajgreeny on 2016-09-12
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**
Also please use standard fonts when posting; colours as you used can be difficult to read for users who are colour-blind.

---

### Post by shao-chi on 2016-09-12
OK, thanks for your suggestion.

---

### Post by shao-chi on 2016-09-13
I've found an article, and this solve my problem.
[https://forums.gentoo.org/viewtopic-t-945284-start-0.html](https://forums.gentoo.org/viewtopic-t-945284-start-0.html)

It's very simple, just map your touch screen device to a monitor and make sure do this after X started .

```


~$ xinput --map-to-output 11 HDMI1



```

---

