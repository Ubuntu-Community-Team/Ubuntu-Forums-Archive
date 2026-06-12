---
title: "Cannot add mode with xrandr"
date: 2013-07-02
forum: Hardware
---

### Post by motobeats on 2013-07-02
I have defined a modeline for a resolution I would like to use using xrandr. However, when I try to add the settings to a device I get "cannot find mode".

Definitley not an issue with the X in my resolution name since I have modelines named with both (x and X) and neither gets picked up.

```
xrandr --addmode HDMI1 1370X768

cannot find mode "1370X768"
```


If I run xrandr I can see the modelines I am adding at the bottom. How do I add this mode to my display?

---

### Post by dino99 on 2013-07-02
you need to follow the exact expressions  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by motobeats on 2013-07-03
I have read the info at the link a number of times and feel like I am following the instructions verbatim.

What am I missing?

> andrew@Ubuntu-TV:~$ sudo xrandr --newmode "1360x768_60.00" 85.5 1360 1424 1536 1792 768 771 777 795 +HSync +VSync
[sudo] password for andrew: 
andrew@Ubuntu-TV:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      60.0*+   24.0     30.0  
   1280x1024      60.0  
   1280x720       60.0  
   1024x768       60.0  
   1440x480       30.0  
   1440x480i      30.0  
   800x600        60.3  
   720x480        59.9  
   640x480        60.0     59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
  1360x768_60.00 (0xff)   85.5MHz
        h: width  1360 start 1424 end 1536 total 1792 skew    0 clock   47.7KHz
        v: height  768 start  771 end  777 total  795           clock   60.0Hz
andrew@Ubuntu-TV:~$ sudo xrandr --addmode HDMI1 1370x768_60.00
xrandr: cannot find mode "1370x768_60.00"

---

### Post by motobeats on 2013-07-03
The reason for using xrandr is to try and restore resolution options lost when I updated Ubuntu.

Old Xorg.log
> [    22.080] (II) intel(0): Printing probed modes for output HDMI1
[    22.080] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    22.080] (II) intel(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    22.080] (II) intel(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    22.080] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    22.080] (II) intel(0): Modeline "1680x945"x60.0  131.48  1680 1784 1960 2240  945 946 949 978 -hsync +vsync (58.7 kHz)
[    22.081] (II) intel(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[    22.081] (II) intel(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    22.081] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.081] (II) intel(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    22.081] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    22.081] (II) intel(0): Modeline "1366x768"x60.0   85.89  1366 1439 1583 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
[    22.081] (II) intel(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    22.081] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    22.081] (II) intel(0): Modeline "1280x768"x60.0   68.25  1280 1328 1360 1440  768 771 778 790 +hsync -vsync (47.4 kHz e)
[    22.081] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    22.081] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.081] (II) intel(0): Modeline "1440x480"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    22.081] (II) intel(0): Modeline "1440x480i"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    22.081] (II) intel(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[    22.081] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.081] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    22.081] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    22.081] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.081] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)


Current Xorg.log
> [     4.622] (II) intel(0): Printing probed modes for output HDMI1
[     4.622] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     4.622] (II) intel(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     4.622] (II) intel(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)








[     4.622] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)












[     4.622] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     4.622] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     4.622] (II) intel(0): Modeline "1440x480"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     4.622] (II) intel(0): Modeline "1440x480i"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)


[     4.622] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)


[     4.622] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     4.622] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     4.622] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)


---

