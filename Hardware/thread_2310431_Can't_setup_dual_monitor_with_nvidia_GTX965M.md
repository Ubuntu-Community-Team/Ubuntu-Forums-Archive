---
title: "Can't setup dual monitor with nvidia GTX965M"
date: 2016-01-19
forum: Hardware
---

### Post by Alexis.M on 2016-01-19
Hello,

I'm trying to setup a dual monitor on a laptop with Ubuntu 15.10 and a nvidia GTX965M graphic card with the latest nvidia driver (nvidia-361). Could not make X work with drivers less than 352.

When I use ubuntu's display settings, the display is stretch (not extended) on the two monitors. When i try to use **nvidia-settings, the built-in monitor is not detected** while xrandr propoerly detects it:

```

$ xrandr
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
eDP-1-0 connected primary 1920x1080+0+0 344mm x 194mm
   1920x1080     60.02*+  59.93    47.99  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
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
  1680x1050 (0x47) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1280x1024 (0x4b) 108.000MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1440x900 (0x4c) 106.500MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1280x960 (0x4d) 108.000MHz
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock  60.00KHz
        v: height  960 start  961 end  964 total 1000           clock  60.00Hz
  1024x768 (0x52) 65.000MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x59) 40.000MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x5a) 36.000MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x62) 25.175MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```

```

$ nvidia-xconfig --query-gpu-info
Number of GPUs: 1

GPU #0:
  Name      : GeForce GTX 965M
  UUID      : GPU-cf7b1682-bb9a-e758-021d-9c6b2ae243e6
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 1

  Display Device 0 (TV-4):
      EDID Name             : AOC 2470W
      Minimum HorizSync     : 30.000 kHz
      Maximum HorizSync     : 83.000 kHz
      Minimum VertRefresh   : 50 Hz
      Maximum VertRefresh   : 76 Hz
      Maximum PixelClock    : 170.000 MHz
      Maximum Width         : 1920 pixels
      Maximum Height        : 1080 pixels
      Preferred Width       : 1920 pixels
      Preferred Height      : 1080 pixels
      Preferred VertRefresh : 60 Hz
      Physical Width        : 520 mm
      Physical Height       : 290 mm


```

Any suggestions ?

Thanks by advance

Alexis

---

