---
title: "External monitor not working on Lenovo Ideapad 5i 15IAL7"
date: 2022-12-17
forum: Hardware
---

### Post by wesintonderchef on 2022-12-17
I have a brand new Lenovo Ideapad 5i 15AL7 with Ubuntu 22.04.1 LTS. 
I also have an HP Curved Display monitor (HDMI) which works with other laptops, but for some reason not with this one.
The laptop detects the monitor, as shown in the output of get-edid below, but nothing is displayed, the monitor goes to sleep. 
I have not seen any relevant entries in journalctl.

```

Section "Monitor"
    Identifier "HP 27 Curved"
    ModelName "HP 27 Curved"
    VendorName "HPN"
    # Monitor Manufactured week 29 of 2017
    # EDID version 1.3
    # Digital Display
    DisplaySize 600 340
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 30-85
    VertRefresh 48-75
    # Maximum pixel clock is 180MHz
    #Not giving standard mode: 1920x1080, 60Hz
    #Not giving standard mode: 1280x720, 60Hz
    #Not giving standard mode: 1600x900, 60Hz
    #Not giving standard mode: 1440x900, 60Hz
    #Not giving standard mode: 1680x1050, 60Hz
    #Not giving standard mode: 1280x800, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz

    #Extension block found. Parsing...
    Modeline     "Mode 10" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 2" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 3" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 4" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
    Modeline     "Mode 5" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 6" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 7" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 8" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 9" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
    Modeline     "Mode 11" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync 
    Modeline     "Mode 12" 174.50 1920 1968 2000 2080 1080 1083 1088 1119 +hsync -vsync 
    Option "PreferredMode" "Mode 10"
EndSection
256-byte EDID successfully retrieved from i2c bus 9
Looks like i2c was successful. Have a good day.

```

The relevant part of lspci:

```

00:02.0 VGA compatible controller: Intel Corporation Device 46a8 (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3af2
    Flags: bus master, fast devsel, latency 0, IRQ 152
    Memory at 6000000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 4000000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable+ 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] Process Address Space ID (PASID)
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] Page Request Interface (PRI)
    Capabilities: [320] Single Root I/O Virtualization (SR-IOV)
    Kernel driver in use: i915
    Kernel modules: i915

```

uname -a:

```

Linux aries 5.15.0-56-generic #62-Ubuntu SMP Tue Nov 22 19:54:14 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

any help would be most appreciated.

---

