---
title: "Setting WQHD resolution"
date: 2018-08-13
forum: Hardware
---

### Post by swirii67 on 2018-08-13
HI, I have a problem while setting my display into WQHD (2560 x 1440) resolution.
My display and VGA supports WQHD and I used the monitor as WQHD on my mac and windows with the same cable.

Result of "sudo get-edid | parse-edid" is as following.
```

This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
1 potential busses found: 5
256-byte EDID successfully retrieved from i2c bus 5
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
    Identifier "SMS27A850"
    ModelName "SMS27A850"
    VendorName "SAM"
    # Monitor Manufactured week 11 of 2013
    # EDID version 1.3
    # Digital Display
    DisplaySize 520 320
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 30-90
    VertRefresh 56-75
    # Maximum pixel clock is 320MHz
    #Not giving standard mode: 1152x864, 75Hz
    #Not giving standard mode: 1280x800, 60Hz
    #Not giving standard mode: 1280x960, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1440x900, 60Hz
    #Not giving standard mode: 1600x1200, 60Hz
    #Not giving standard mode: 1680x1050, 60Hz
    #Not giving standard mode: 1920x1200, 60Hz


    #Extension block found. Parsing...
    Modeline     "Mode 0" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync 
    Modeline     "Mode 1" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 2" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 3" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync 
    Modeline     "Mode 4" 74.25 1280 1720 1760 1980 720 725 730 750 +hsync +vsync 
EndSection

```

lspci -vk | grep VGA
```
09:00.0 VGA compatible controller: NVIDIA Corporation GP108 (rev a1) (prog-if 00 [VGA controller])
```

I tried to add xrandr mode using cvt and following is the current status.
```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1080     60.00*+  50.00  
   1680x1050     59.95  
   1600x1200     60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x800      59.81  
   1280x720      60.00    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
  2560x1440_60.00 (0x271) 312.250MHz -HSync +VSync
        h: width  2560 start 2752 end 3024 total 3488 skew    0 clock  89.52KHz
        v: height 1440 start 1443 end 1448 total 1493           clock  59.96Hz

```

When I try to add the new mode to the display, it fails.
xrandr --addmode HDMI-0 2560x1440_60.00
```

X Error of failed request:  BadMatch (invalid parameter attributes)  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

Help me on this issue please.
Thanks.

---

### Post by Autodave on 2018-08-13
That card is also called a GT1030 and should be using the 390 driver.  If you haven't installed a driver for that yet, go to Additional Drivers and let it search. Either of the 390 drivers should work fine. Install one of them and then you will have the Nvidia setup icon available to use to change your resolution.

---

### Post by swirii67 on 2018-08-13
> **Autodave said:**
> That card is also called a GT1030 and should be using the 390 driver.  If you haven't installed a driver for that yet, go to Additional Drivers and let it search. Either of the 390 drivers should work fine. Install one of them and then you will have the Nvidia setup icon available to use to change your resolution.
Well, actually I am using 390.77 version of the drivers already.

---

