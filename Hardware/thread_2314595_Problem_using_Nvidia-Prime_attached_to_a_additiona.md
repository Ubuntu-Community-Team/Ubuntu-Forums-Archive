---
title: "Problem using Nvidia-Prime attached to a additional monitor via DVI"
date: 2016-02-22
forum: Hardware
---

### Post by S._W. on 2016-02-22
Hi all,

I have problems using the nvidia-prime on my Lenovo T420 in addition with a portreplicator. The os is Ubuntu 15.10.

Normally the T420 hasn't a DVI port, but if you use the portreplicator you can use DVI.


If I use only one of the screens, which means the integrated LCD display or the DVI monitor, everything works well. But if I use both of them they got regonzised as one and a resolution of 3250x XXXz. 

I attached three configs.

Only laptops screen:
```

Screen 0: minimum 8 x 8, current 1600 x 900, maximum 16384 x 16384
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected (normal left inverted right x axis y axis)
   1920x1080     60.00 +
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   640x480       59.94  
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
LVDS-1-0 connected primary 1600x900+0+0 309mm x 174mm
   1600x900      60.01*+  40.00  
   1440x900      59.89  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1-0 disconnected
  1440x900 (0x46) 106.500MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1024x768 (0x4b) 65.000MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x52) 40.000MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x53) 36.000MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x5b) 25.175MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```

Only external screen:
```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   640x480       59.94  
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
LVDS-1-0 connected
   1600x900      60.01 +  40.00  
   1440x900      59.89  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1-0 disconnected
  1440x900 (0x46) 106.500MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1024x768 (0x4b) 65.000MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x52) 40.000MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x53) 36.000MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x5b) 25.175MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```

Both of them:
```

Screen 0: minimum 8 x 8, current 3520 x 1080, maximum 16384 x 16384
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   640x480       59.94  
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
LVDS-1-0 connected primary 1600x900+0+0 309mm x 174mm
   1600x900      60.01*+  40.00  
   1440x900      59.89  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1-0 disconnected
  1440x900 (0x46) 106.500MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1024x768 (0x4b) 65.000MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x52) 40.000MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x53) 36.000MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x5b) 25.175MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```


Does anyone has an idea to hadle this problem?

Thanks a lot!

---

### Post by gordintoronto on 2016-02-22
Does the port replicator convert VGA to DVI? If the monitor (brand and model?) has a VGA port, that might work better.

I have an Nvidia display adapter with the "additional driver" installed in Xubuntu 15.10, but I don't recognize the phrase "nvidia prime". I use Nvidia X Server Settings. What model is the display adapter?

---

