---
title: "Ubuntu 20.04 Cannot use 1920x1080 resolution on a 4k external monitor"
date: 2020-07-14
forum: Hardware
---

### Post by dmocek on 2020-07-14
Hello.  I'm running Ubuntu 20.04 on a Dell XPS 17 laptop with an Nvidia graphics card (see results of xrandr and read-edid below).  My monitor is actually a Seiki SE39UY04, not the Seiki SE50UY04 read-edid shows.  The monitor is capable of 1920x1080 @60Hz and 3840x2160 @30Hz.  When I use the monitor with an HDMI cable, it always comes up in 3840x2160 mode.  When I choose 1920x1080 in any Hz, it resorts back to 3840x2160.  I've tried adding 1920x1080 using xrandr (and lrandr), addmode, newmode, but it still won't display in 1920.  I have another Dell Latitude 7400 with an Intel GPU I have the exact same problem with (although using xrandr I was able to get it to display in 1920x1080 once but it has since reverted back to 3840x2160 and now won't change to anything else).  When I connect my Mac to it via HDMI, it displays in 1920.

Any suggestions to get this to display in 1920 Using Ubuntu?

Thanks
xrandr
-----------------------------------------------------------
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 698mm x 393mm
   3840x2160     30.00*+  25.00    24.00    29.97    23.98  
   1920x1080     60.00    50.00    59.94    24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1440x900      59.89  
   1280x960      60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    60.00    59.94  
   720x400       70.08  
   2560x1440_30.00  29.94
-----------------------------------------------------------
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 3
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
No EDID on bus 8
No EDID on bus 9
3 potential busses found: 0 2 4
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 0 doesn't really have an EDID...
256-byte EDID successfully retrieved from i2c bus 2
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
    Identifier "SE50UY04"
    ModelName "SE50UY04"
    VendorName "SEK"
    # Monitor Manufactured week 35 of 2014
    # EDID version 1.3
    # Digital Display
    DisplaySize 1100 620
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 24-60
    VertRefresh 50-75
    # Maximum pixel clock is 110MHz
    #Not giving standard mode: 1280x960, 60Hz


    #Extension block found. Parsing...
    Modeline     "Mode 17" 27.00 720 732 796 864 576 581 586 625 -hsync -vsync 
    Modeline     "Mode 0" 297.00 3840 4016 4104 4400 2160 2168 2178 2250 +hsync +vsync 
    Modeline     "Mode 1" 106.50 1440 1520 1672 1904 900 903 909 934 -hsync +vsync 
    Modeline     "Mode 2" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
    Modeline     "Mode 3" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
    Modeline     "Mode 4" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 5" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 6" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 7" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 8" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 9" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 10" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
    Modeline     "Mode 11" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 12" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
    Modeline     "Mode 13" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
    Modeline     "Mode 14" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 15" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 16" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 18" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
    Modeline     "Mode 19" 74.25 1920 2448 2492 2640 540 542 547 562 +hsync +vsync interlace
    Modeline     "Mode 20" 74.25 1280 1720 1760 1980 720 725 730 750 +hsync +vsync 
    Option "PreferredMode" "Mode 17"
EndSection

---

