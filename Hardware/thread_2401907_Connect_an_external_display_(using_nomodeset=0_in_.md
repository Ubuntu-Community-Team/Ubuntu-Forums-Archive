---
title: "Connect an external display (using nomodeset=0 in grub)"
date: 2018-09-24
forum: Hardware
---

### Post by daredevildas on 2018-09-24
Steps followed after dual booting ubuntu with windows-

  [https://www.reddit.com/r/linux_gaming/comments/8oy876/failed_installing_ubuntu_1604_on_my_new_msi_gs65/e3amuif](https://www.reddit.com/r/linux_gaming/comments/8oy876/failed_installing_ubuntu_1604_on_my_new_msi_gs65/e3amuif) - Necessary to set nomodeset=0 to boot into Ubuntu
  [https://www.reddit.com/r/linuxhardware/comments/93769g/all_purpose_laptop/e3f5xia](https://www.reddit.com/r/linuxhardware/comments/93769g/all_purpose_laptop/e3f5xia) - Not sure how relevant but decided to link anyway in case any of the steps had side effects


  Output of xrandr (with external monitor connected) - 

```
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080    144.03*+  60.08    60.01    59.97    59.96    59.93  
   1680x1050     84.94    74.89    69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     85.00    74.76    70.00    59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     85.02    75.02    60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      85.00    60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864     100.00    85.06    85.00    75.00    75.00    70.00    60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      85.00    75.05    60.04    85.00    75.03    70.07    60.00  
   1024x768i     86.96  
   960x720       85.00    75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   832x624       74.55  
   960x540       59.96    59.99    59.63    59.82  
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00    60.32    56.25  
   840x525       85.02    74.96    69.88    60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       85.08    74.76    70.06    59.98  
   800x450       59.95    59.82  
   640x512       85.02    75.02    60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       85.09    60.00    85.01    72.81    75.00    59.94  
   720x405       59.51    58.99  
   720x400       85.04  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98    85.08  
   576x432      100.11    85.15    85.09    75.00    75.00    70.00    60.06  
   640x360       59.86    59.83    59.84    59.32  
   640x350       85.08  
   512x384       85.00    75.03    70.07    60.00  
   512x384i      87.06  
   512x288       60.00    59.92  
   416x312       74.66  
   480x270       59.63    59.82  
   400x300       85.27    72.19    75.12    60.32    56.34  
   432x243       59.92    59.57  
   320x240       85.18    72.81    75.00    60.05  
   360x202       59.51    59.13  
   360x200       85.04  
   320x200       85.27  
   320x180       59.84    59.32  
   320x175       85.27  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1400x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-1-2 disconnected (normal left inverted right x axis y axis)
  1680x1050 (0x4c) 119.000MHz +HSync -VSync
        h: width  1680 start 1728 end 1760 total 1840 skew    0 clock  64.67KHz
        v: height 1050 start 1053 end 1059 total 1080           clock  59.88Hz
  1280x1024 (0x4f) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1280x1024 (0x50) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x800 (0x52) 71.000MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock  49.31KHz
        v: height  800 start  803 end  809 total  823           clock  59.91Hz
  1152x864 (0x53) 108.000MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
        v: height  864 start  865 end  868 total  900           clock  75.00Hz
  1024x768 (0x57) 78.750MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
        v: height  768 start  769 end  772 total  800           clock  75.03Hz
  1024x768 (0x58) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x59) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x5a) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  640x480 (0x5e) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x60) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz


```

---

