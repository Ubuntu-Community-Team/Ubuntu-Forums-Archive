---
title: "Samsung 24&quot; monitor displaying in 800x600 but no other modes/resolutions"
date: 2019-10-23
forum: Hardware
---

### Post by jrcook416 on 2019-10-23
Good morning/evening/afternoon.

I have an installation of Studio 18.04 that has three monitors attached: a Visio, an HP, and a Samsung.  The Visio and HP are attached using native VGA and DVI inputs and the Samsung is connected using a DisplayLink VGA adapter.  The Visio and HP work successfully and the Samsung 24" will display in 800x800 only.  I have ran xrandr and arandr with no success, only to get the Samsung monitor to display in 800x600.  The top resolution in this monitor is somewhat larger, but I have been unable to get it to work successfully above 800x600.  

Following is my xrandr output.

```
Screen 0: minimum 320 x 200, current 4320 x 1080, maximum 8192 x 8192
DP-3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     59.93*+
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
DP-4 connected 1600x900+1920+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900      60.00*+
   1280x1024     60.02  
   1440x900      59.90  
   1280x720      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
   720x400       70.08  
DVI-I-2-1 connected 800x600+3520+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1080     60.00  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      60.00  
   800x600       60.32*   56.25  
   640x480       59.94  
DP-1-1 disconnected (normal left inverted right x axis y axis)
DP-1-2 disconnected (normal left inverted right x axis y axis)
  1600x900 (0x68) 108.000MHz +HSync +VSync
        h: width  1600 start 1624 end 1704 total 1800 skew    0 clock  60.00KHz
        v: height  900 start  901 end  904 total 1000           clock  60.00Hz
  1280x1024 (0x69) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x720 (0x6c) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1024x768 (0x6d) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x6e) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  640x480 (0x70) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```

Trying to push this monitor into the largest mode, 1920x1080 returns configure crtc 2 failed.

Any suggestions anyone may have would be helpful.   If further outputs from the OS are required, please let me know and I will post them forthwith.

Regards,

Jeremiah

---

