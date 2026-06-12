---
title: "Help me to get touchscreen work properly again."
date: 2016-05-06
forum: Hardware
---

### Post by fvnhwpf on 2016-05-06
Last Saturday I got bunch of updates to my tablet. After that x- and y-axes has been inverted. I found from log that xserver-xorg-input-libinput package was installed. 
I made [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-libinput/+bug/1577387") from it, even I'm not 100% sure that's causing problem.

Normally I could fix them by using xinput_calibrator tool, but now if I run that tool it won't affect touchscreen settings. 

Distribution is fresh Xenial server install, but there is Elementary-Desktop installed to it. I know this is still buggy desktop environment, but it should not affect to touchscreen.

```

$ uname -r
4.4.0-21-generic

```

```

$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0911 Intel Corp. 
Bus 001 Device 004: ID 046a:0008 Cherry GmbH Wireless Keyboard and Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0f)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0f)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0f)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0f)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0f)

```

```

$ xinput
&#9121; Virtual core pointer id=2    [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4    [slave pointer (2)]
&#9116; &#8627; Goodix Capacitive TouchScreen id=7    [slave pointer (2)]
&#9116; &#8627; Cherry GmbH Cherry Slim Line Trackball Keyboard    id=11[slave pointer (2)]
&#9123; Virtual core keyboard id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5    [slave keyboard (3)]
    &#8627; Video Bus id=6    [slave keyboard (3)]
    &#8627; axp20x-pek id=8    [slave keyboard (3)]
    &#8627; gpio-keys id=9    [slave keyboard (3)]
    &#8627; Cherry GmbH Cherry Slim Line Trackball Keyboard    id=10[slave keyboard (3)]

```

```

$ xinput list-props 9
Device 'Goodix Capacitive TouchScreen':
 Device Enabled (139):    1
 Coordinate Transformation Matrix (141):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
 libinput Calibration Matrix (292):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
 libinput Calibration Matrix Default (293):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
 libinput Send Events Modes Available (257):    1, 0
 libinput Send Events Mode Enabled (258):    0, 0
 libinput Send Events Mode Enabled Default (259):    0, 0
 Device Node (260):    "/dev/input/event3"
 Device Product ID (261):    1046, 911
 libinput Horizonal Scroll Enabled (262):    0

```

---

