---
title: "eGalaxTouch calibration does not work"
date: 2013-01-22
forum: Hardware
---

### Post by wasu on 2013-01-22
Hello,

I am using a Samsung Touchscreen (LTI220MT02) at Ubuntu 12.04 with drivers from eGalaxTouch. Driver download from [http://home.eeti.com.tw/web20/eg/Touch_Drives.html](http://home.eeti.com.tw/web20/eg/Touch_Drives.html) . As desktop manager I use lightdm.

I want to calibrate the touchscreen, but so far I have no success, the calibration is still not working. I have tried the following:

1) The 4-point-calibration tool 4Pts Cal from the eGTouchU programm (comes with the driver) is always displayed as inactive (cannot be clicked). See image eGTouchU.png attached. I want to execute the 4Pts Cal but this is not possible, I do not know why. I have read in forums that normally this tool should be executable. Does anyone know how to get 4Pts Cal working? Or does anyone know in which file and in which format the tool saves the calibration data?

2) I have tried xinput_calibrator, the following output is shown:
```

Section "InputClass"
Identifier "calibration"
MatchProduct "eGalaxTouch Virtual Device for Single"
Option "Calibration" "43 2039 52 1959"
EndSection

```In forums I have read to put this data not as shown by xinput_calibrator in /etc/X11/xorg.conf.d/99-calibration.conf but to put this data into /usr/share/X11/xorg.conf.d/99-calibration.conf . After reboot calibration still does not work. I have also tried to put the line
Option "Calibration" "43 2039 52 1959"
into
/usr/share/X11/xorg.conf.d/10-evdev.conf
no success.

3) I have tried to use xinput directly, xinput --list results in:
```

Virtual core pointer                        id=2    [master pointer  (3)]
Virtual core XTEST pointer                  id=4 [slave  pointer  (2)]
DualPoint Stick                             id=15    [slave  pointer  (2)]
AlpsPS/2 ALPS DualPoint TouchPad            id=16    [slave  pointer  (2)]
eGalaxTouch Virtual Device for Multi        id=11 [slave  pointer  (2)]
eGalaxTouch Virtual Device for Single       id=12    [slave  pointer  (2)]
Virtual core keyboard                       id=3    [master keyboard (2)]
Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
Video Bus                                   id=6    [slave  keyboard (3)]

```After executing the command:
```
xinput set-int-prop 12 "Evdev Axis Calibration" 32 43 2039 52 1959

```still no calibration. For information, id=11 (Multi) is from testing with another monitor, normally I use the Touchscreen as Single Monitor. In a forum I have read to store the xinput-command in /etc/X11/Xsession.d/98x11-common_touchscreen , but still no calibration after reboot.

4) In the file Guide/Linux_eGTouch_Release_Note.txt from the driver download there is a line with:
-The calibration data is now store at /etc/eGTouchX.param
However the file /etc/eGTouchX.param does not exist. I can create it, but I do not know the format of the calibration data to put in.

5) I have found the file
/etc/eGTouchL.ini
I did not found calibration data there.
Does anyone know, is this file needed for calibration?

Please help!
Regards,
wasu

---

### Post by wasu on 2013-01-23
I have now installed Ubuntu 12.10 because I have read this has better touchscreen support than 12.04. At 12.10 no additional driver is needed but the axis are inverted. I could not manage to invert the axis. Here is the new post with the new problem:
[http://ubuntuforums.org/showthread.php?t=2107933](http://ubuntuforums.org/showthread.php?t=2107933)

---

