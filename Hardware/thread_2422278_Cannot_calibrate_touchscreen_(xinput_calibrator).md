---
title: "Cannot calibrate touchscreen (xinput_calibrator)"
date: 2019-07-04
forum: Hardware
---

### Post by gingear on 2019-07-04
I've been trying for the last two hours or so, but when running through xinput_calirator, it seems like everything it does makes absolutely no change. Even making the config file it stated and rebooting didn't help. This is a Fujitsu lifebook p1630, running lubuntu 19.04
```
gingear@miniGear-pc:~$ sudo xinput_calibrator -v
DEBUG: XInputExtension version is 2.3
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Skipping device 'Virtual core XTEST pointer' id=4, does not report Absolute events.
DEBUG: Skipping device 'PS/2 Generic Mouse' id=14, does not report Absolute events.
DEBUG: Selected device: Fujitsu Component USB Touch Panel
DEBUG: Not usbtouchscreen calibrator: Not a usbtouchscreen device
DEBUG: Not evdev calibrator: Evdev: invalid "Evdev Axis Calibration" property format
Calibrating standard Xorg driver "Fujitsu Component USB Touch Panel"
        current calibration values: min_x=0, max_x=65535 and min_y=0, max_y=65535
        If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).
DEBUG: Found that 'Fujitsu Component USB Touch Panel' is a sysfs name.
DEBUG: Adding click 0 (X=174, Y=147)
DEBUG: Adding click 1 (X=1069, Y=148)
DEBUG: Adding click 2 (X=174, Y=663)
DEBUG: Adding click 3 (X=1069, Y=667)
        --> Making the calibration permanent <--
DEBUG: Found that 'Fujitsu Component USB Touch Panel' is a sysfs name.
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf' (/usr/share/X11/xorg.conf.d/ in some distro's)
Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "Fujitsu Component USB Touch Panel"
        Option  "MinX"  "1271"
        Option  "MaxX"  "62369"
        Option  "MinY"  "5227"
        Option  "MaxY"  "64106"
        Option  "SwapXY"        "0" # unless it was already set to 1
        Option  "InvertX"       "0"  # unless it was already set
        Option  "InvertY"       "0"  # unless it was already set
EndSection 
```

---

