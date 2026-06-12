---
title: "LG 32UK50T-W monitor EDID information showing 27&quot; vs 32&quot; monitor"
date: 2020-01-09
forum: Hardware
---

### Post by gerleman on 2020-01-09
Hi,

I'm running Ubuntu 18.04 with a LG 32UK50T-W monitor, but it's reporting as a 27" monitor instead of it's actual 32".  Not sure if it matters, but I have a MSI RX580 graphics card.  Any idea how I can get the monitor to be recognized as 32"?

```

lspci -nn | grep -E 'VGA|Display'
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X] [1002:67df] (rev e7)

```

```

sudo lshw -c display
  *-display                 
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:133 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:dfe00000-dfe3ffff memory:c0000-dffff

```

```

xrandr
Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 600mm x 340mm
   3840x2160     60.00*+  50.00    59.94    30.00    30.00    25.00    24.00    29.97    23.98  
   2560x1440     59.95  
   1920x1200     60.00  
   1920x1080     60.00    60.00    59.94    30.00    24.00    29.97    23.98  
   1600x1200     60.00  
   1680x1050     60.00  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      60.00  
   1280x800      59.91  
   1152x864      59.97  
   1280x720      60.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
HDMI-A-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)

```

```

sudo get-edid|parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 2
No EDID on bus 5
No EDID on bus 6
3 potential busses found: 1 3 4
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 1 doesn't really have an EDID...
Bus 3 doesn't really have an EDID...
256-byte EDID successfully retrieved from i2c bus 4
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
    Identifier "LG Ultra HD"
    ModelName "LG Ultra HD"
    VendorName "GSM"
    # Monitor Manufactured week 9 of 2018
    # EDID version 1.3
    # Digital Display
    DisplaySize 600 340
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 30-135
    VertRefresh 56-61
    # Maximum pixel clock is 600MHz
    #Not giving standard mode: 1152x864, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1280x720, 60Hz
    #Not giving standard mode: 1600x900, 60Hz
    #Not giving standard mode: 1920x1080, 60Hz
    #Not giving standard mode: 1280x800, 60Hz

    #Extension block found. Parsing...
#WARNING: I may have missed a mode (CEA mode 97)
#WARNING: I may have missed a mode (CEA mode 96)
#WARNING: I may have missed a mode (CEA mode 93)
#WARNING: I may have missed a mode (CEA mode 94)
#WARNING: I may have missed a mode (CEA mode 95)
    Modeline     "Mode 10" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync -vsync 
    Modeline     "Mode 0" 594.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync 
    Modeline     "Mode 1" 297.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync -vsync 
    Modeline     "Mode 2" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 3" 74.250 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 4" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 5" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
    Modeline     "Mode 6" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 7" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 8" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 9" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
    Modeline     "Mode 11" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync 
    Option "PreferredMode" "Mode 10"
EndSection

```

---

### Post by CelticWarrior on 2020-01-09
As long as the correct native resolution is detected, size doesn't matter.

---

### Post by gerleman on 2020-01-09
It is recognizing the resolution as 3840x2160 @ 60Hz which I believe is correct since it's a 4k monitor with HDMI.  Are you saying that the Display size is ignored?  It's showing 600mm x 340mm, but the monitor is closer to 698mm x 393mm.  Thanks

---

### Post by CatKiller on 2020-01-09
> **gerleman said:**
> Are you saying that the Display size is ignored?

It's used to calculate how many dots-per-inch your display has, which is used to work out the layout of the subpixels for subpixel anti-aliasing with text rendering. The DPI calculated from the EDID information is only one source for that, and every text tool to configure that that I've seen has an override option included.

---

### Post by gerleman on 2020-01-10
Thanks, I appreciate it.  I'll just ignore the fact the monitor is listed as 27".

---

