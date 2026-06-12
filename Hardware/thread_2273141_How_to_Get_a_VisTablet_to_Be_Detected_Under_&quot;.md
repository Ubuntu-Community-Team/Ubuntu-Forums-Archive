---
title: "How to Get a VisTablet to Be Detected Under &quot;Wacom Tablets&quot;?"
date: 2015-04-10
forum: Hardware
---

### Post by tehtotalpwnage on 2015-04-10
Hi there!

So I recently received a VisTablet VT Realm as a gift and I want to use it under Ubuntu 14.10. So far, the controls are working fine, but I can't configure the two buttons on the pen and the macros on the tablet because it isn't detected under Wacom Tablets. I don't like having useless buttons on my tablet and I really don't want to have to go out and buy an actual Wacom tablet to work under Ubuntu, so is there any way that I can configure the VisTablet to be detected under Wacom Tablets?

Based on what I read in other threads, this might be useful:

Output of /var/log/Xorg.0.log:
```
[    21.393] (II) config/udev: Adding input device WALTOP International Corp. Graphics Tablet (/dev/input/event3)
[    21.393] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "evdev pointer catchall"
[    21.393] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "evdev keyboard catchall"
[    21.393] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "evdev tablet catchall"
[    21.393] (**) WALTOP International Corp. Graphics Tablet: Applying InputClass "Waltop class"
[    21.393] (II) LoadModule: "wacom"
[    21.393] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    21.409] (II) Module wacom: vendor="X.Org Foundation"
[    21.409]     compiled for 1.16.0, module version = 0.25.0
[    21.409]     Module class: X.Org XInput Driver
[    21.409]     ABI class: X.Org XInput driver, version 21.0
[    21.409] (II) wacom: Driver for Wacom graphics tablets: PenPartner, Graphire,
    Graphire2 4x5, Graphire2 5x7, Graphire3 4x5, Graphire3 6x8,
    Graphire4 4x5, Graphire4 6x8, BambooFun 4x5, BambooFun 6x8,
    Bamboo1 Medium, Graphire4 6x8 BlueTooth, CTL-460, CTH-461, CTL-660,
    CTL-461/S, Bamboo Touch, CTH-460/K, CTH-461/S, CTH-661/S1, CTH-461/L,
    CTH-661/L, Intuos 4x5, Intuos 6x8, Intuos 9x12, Intuos 12x12,
    Intuos 12x18, PTU600, PL400, PL500, PL600, PL600SX, PL550, PL800,
    PL700, PL510, PL710, DTI520, DTF720, DTF720a, DTF521, DTU1931,
    DTU2231, DTU1631, Intuos2 4x5, Intuos2 6x8, Intuos2 9x12,
    Intuos2 12x12, Intuos2 12x18, Intuos2 6x8 , Volito, PenStation,
    Volito2 4x5, Volito2 2x3, PenPartner2, Bamboo, Bamboo1, Bamboo1 4x6,
    Bamboo1 5x8, Intuos3 4x5, Intuos3 6x8, Intuos3 9x12, Intuos3 12x12,
    Intuos3 12x19, Intuos3 6x11, Intuos3 4x6, Intuos4 4x6, Intuos4 6x9,
    Intuos4 8x13, Intuos4 12x19, Intuos4 WL USB Endpoint,
    Intuos4 WL Bluetooth Endpoint, Intuos5 touch S, Intuos5 touch M,
    Intuos5 touch L, Intuos5 S, Intuos5 M, Intuos Pro S, Intuos Pro M,
    Intuos Pro L, Cintiq 21UX, Cintiq 20WSX, Cintiq 12WX, Cintiq 21UX2,
    Cintiq 24HD, Cintiq 22HD, Cintiq 24HD touch (EMR digitizer),
    Cintiq 13HD, DTK2241, DTH2242, Cintiq 22HDT, TabletPC 0x90,
    TabletPC 0x93, TabletPC 0x97, TabletPC 0x9A, CapPlus  0x9F,
    TabletPC 0xE2, TabletPC 0xE3, TabletPC 0xE5, TabletPC 0xE6,
    TabletPC 0xEC, TabletPC 0xED, TabletPC 0xEF, TabletPC 0x100,
    TabletPC 0x101, TabletPC 0x10D, TabletPC 0x116, TabletPC 0x4001,
    TabletPC 0x4004, TabletPC 0x5000, TabletPC 0x5002, usb:172f:0024,
    usb:172f:0025, usb:172f:0026, usb:172f:0027, usb:172f:0028,
    usb:172f:0030, usb:172f:0031, usb:172f:0032, usb:172f:0033,
    usb:172f:0034, usb:172f:0035, usb:172f:0036, usb:172f:0037,
    usb:172f:0038, usb:172f:0039, usb:172f:0051, usb:172f:0052,
    usb:172f:0053, usb:172f:0054, usb:172f:0055, usb:172f:0056,
    usb:172f:0057, usb:172f:0058, usb:172f:0500, usb:172f:0501,
    usb:172f:0502, usb:172f:0503, usb:1b96:0001, usb:17ef:6004
[    21.409] (II) Using input driver 'wacom' for 'WALTOP International Corp. Graphics Tablet'
[    21.409] (**) WALTOP International Corp. Graphics Tablet: always reports core events
[    21.409] (**) Option "Device" "/dev/input/event3"
[    21.409] (II) WALTOP International Corp. Graphics Tablet: type not specified, assuming 'stylus'.
[    21.409] (II) WALTOP International Corp. Graphics Tablet: other types will be automatically added.
[    21.409] (--) WALTOP International Corp. Graphics Tablet stylus: using pressure threshold of 27 for button 1
[    21.409] (--) WALTOP International Corp. Graphics Tablet stylus: maxX=20000 maxY=12500 maxZ=2047 resX=1016 resY=1016  tilt=enabled
[    21.409] (II) WALTOP International Corp. Graphics Tablet stylus: hotplugging dependent devices.
[    21.409] (EE) WALTOP International Corp. Graphics Tablet stylus: Invalid type 'cursor' for this device.
[    21.409] (EE) WALTOP International Corp. Graphics Tablet stylus: Invalid type 'touch' for this device.
[    21.409] (II) WALTOP International Corp. Graphics Tablet stylus: hotplugging completed.
[    21.416] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:172F:0047.0001/input/input5/event3"
[    21.416] (II) XINPUT: Adding extended input device "WALTOP International Corp. Graphics Tablet stylus" (type: STYLUS, id 9)
[    21.416] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) keeping acceleration scheme 1
[    21.416] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) acceleration profile 0
[    21.416] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) acceleration factor: 2.000
[    21.416] (**) WALTOP International Corp. Graphics Tablet stylus: (accel) acceleration threshold: 4
[    21.416] (II) config/udev: Adding input device WALTOP International Corp. Graphics Tablet (/dev/input/mouse0)
[    21.416] (II) No input driver specified, ignoring this device.
[    21.416] (II) This device may have been added with another device file.

```

Both lsusb | grep Wacom and lsmod | grep Wacom come up empty.

Output of xinput list:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Natural® Ergonomic Keyboard 4000    id=11    [slave  pointer  (2)]
&#9116;   &#8627; USB OPTICAL MOUSE                           id=13    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Graphics Tablet stylus    id=9    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Graphics Tablet eraser    id=14    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Graphics Tablet pad    id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Microsoft Natural® Ergonomic Keyboard 4000    id=10    [slave  keyboard (3)]
    &#8627; C-Media USB Headphone Set                   id=12    [slave  keyboard (3)]

```

---

### Post by tehtotalpwnage on 2015-04-12
*bump*
Really? No one?

---

### Post by dino99 on 2015-04-13
this might help you to dig a bit more  [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

---

### Post by tehtotalpwnage on 2015-04-13
> **9d9 said:**
> this might help you to dig a bit more  [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)
Thanks, but that article has to do with laptop touchpads as far as I know.

---

### Post by tehtotalpwnage on 2015-04-17
Bump. Anyone?

---

### Post by tehtotalpwnage on 2015-04-17
Alright, apparently this is somewhat of an issue probably in Ubuntu 14.10 Utopic, because when I (accidentally) updated to 15.04 development branch for Vivid, the drawing tablet is picked up.

Thread closed.

---

