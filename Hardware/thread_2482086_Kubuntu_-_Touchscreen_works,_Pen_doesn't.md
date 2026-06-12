---
title: "Kubuntu - Touchscreen works, Pen doesn't"
date: 2022-12-19
forum: Hardware
---

### Post by linucyphre on 2022-12-19
I own a Panasonic Toughpad with a touchscreen. 

In Windows, the touchscreen mode can be chosen by finger-mode, stylus-pen-mode, finger and stylus-pen-mode, glove-mode or water-mode. 
Under Kubuntu only finger-mode is possible. However, I urgently need to use the stylus-pen. The stylus-pen is passive and has a small plastic tip.

```

$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Sharp Corp.   07EA0004                    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; USB FHD Webcam: USB FHD Webcam            id=10   [slave  keyboard (3)]
    &#8627; USB2.0 Camera: USB2.0 Camera              id=11   [slave  keyboard (3)]
    &#8627; Intel Virtual Buttons                     id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; Panasonic Laptop Support                  id=14   [slave  keyboard (3)]

```

This might be the relevant device:
```

$ xinput list-props 9
Device 'Sharp Corp.   07EA0004':
        Device Enabled (157):   1
        Coordinate Transformation Matrix (159): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000,
0.000000, 1.000000
        libinput Calibration Matrix (297):      1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000,
0.000000, 1.000000
        libinput Calibration Matrix Default (298):      1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.
000000, 0.000000, 1.000000
        libinput Send Events Modes Available (280):     1, 0
        libinput Send Events Mode Enabled (281):        0, 0
        libinput Send Events Mode Enabled Default (282):        0, 0
        Device Node (283):      "/dev/input/event8"
        Device Product ID (284):        1245, 38754

```

```

$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 5986:0656 Acer, Inc  
Bus 001 Device 005: ID 13d3:5224 IMC Networks  
Bus 001 Device 004: ID 04dd:9762 Sharp Corp.  
Bus 001 Device 003: ID 0424:2514 Microchip Technology, Inc. (formerly SMSC) USB 2.0 Hub
Bus 001 Device 002: ID 8087:0a2b Intel Corp.  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Xorg log
```

    Informationen    [    10.576] (II) config/udev: Adding input device Sharp Corp.   07EA0004 (/dev/input/event8)
    Informationen    [    10.576] (**) Sharp Corp.   07EA0004: Applying InputClass "libinput touchscreen catchall"
    Informationen    [    10.576] (II) Using input driver 'libinput' for 'Sharp Corp.   07EA0004'
    Informationen    [    10.577] (**) Sharp Corp.   07EA0004: always reports core events
    Informationen    [    10.577] (**) Option "Device" "/dev/input/event8"
    Informationen    [    10.577] (**) Option "_source" "server/udev"
    Informationen    [    10.642] (II) event8  - Sharp Corp.   07EA0004: is tagged by udev as: Touchscreen
    Informationen    [    10.642] (II) event8  - Sharp Corp.   07EA0004: device is a touch device
    Informationen    [    10.643] (II) event8  - Sharp Corp.   07EA0004: device removed
    Informationen    [    10.684] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9.1/1-9.1:1.0/0003:04DD:9762.0003/input/input12/event8"
    Informationen    [    10.684] (II) XINPUT: Adding extended input device "Sharp Corp.   07EA0004" (type: TOUCHSCREEN, id 9)
    Informationen    [    10.685] (**) Option "AccelerationScheme" "none"
    Informationen    [    10.685] (**) Sharp Corp.   07EA0004: (accel) selected scheme none/0
    Informationen    [    10.685] (**) Sharp Corp.   07EA0004: (accel) acceleration factor: 2.000
    Informationen    [    10.685] (**) Sharp Corp.   07EA0004: (accel) acceleration threshold: 4
    Informationen    [    10.751] (II) event8  - Sharp Corp.   07EA0004: is tagged by udev as: Touchscreen
    Informationen    [    10.751] (II) event8  - Sharp Corp.   07EA0004: device is a touch device
    Informationen    [    10.754] (II) config/udev: Adding input device Sharp Corp.   07EA0004 (/dev/input/mouse0)

```

```
Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.8
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.15.0-56-generic
OS Type: 64-bit
Processors: 4 × Intel® Core&#8482; m5-6Y57 CPU @ 1.10GHz
Memory: 7,7 GiB

```

Any hints?

---

### Post by linucyphre on 2023-01-23
What's odd is that the back of the stylus allows an input at a certain angle. Just not the tip of the pen.
Could be a BIOS problem. In the BIOS menu, only touch input is possible.

On this special MK2 toughpad the stylus input seems to be disabled by the bios. For comparison: on the MK1 series, stylus input in KUBUNTU and BIOS is working without any problems.

---

### Post by p-shapley on 2023-11-29
I'm also having this issue and tried many 'xinput' variations but nothing worked for me in Ubuntu 22.04 LTS/Gnome/gdm3. Did you manage to get anywhere with this? There is nothing in the bios aside calibration which won't accept the stylus input. It's strange that the much older wacom based CF-19 works well with stylus hard point, finger and soft rubber tips.

---

