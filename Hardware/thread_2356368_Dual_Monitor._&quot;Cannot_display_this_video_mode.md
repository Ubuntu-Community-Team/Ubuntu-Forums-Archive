---
title: "Dual Monitor. &quot;Cannot display this video mode&quot;"
date: 2017-03-22
forum: Hardware
---

### Post by scayze on 2017-03-22
Howdy!
I just got myself another Monitor. When im clicking "1920x1080 (16:9)" under the display settings, the monitor goes black and oddly, the message "Cannot display this video mode, change computer display input to 1920x1080@60HZ" appears. If i reduce the resolution down to 1680x1050, the monitor works just fine. 
The monitor is connected through an DisplayPort to VGA Adapter, which is connected to my Graphics card. The Adapter supports resolutions up to 1920x1200, so tht shouldnt be the problem. The working monitor is connected through HDMI.

heres the output from "xrandr -q"

```

Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080     60.00*+
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     75.02    70.00    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x800      60.00  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       75.00    60.32    56.25  
   640x480       75.00    72.81    59.94  
   1920x1080_60.00  59.96  
DisplayPort-2 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080     60.00*+
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    66.67    59.94  
   720x400       70.08  
DVI-D-0 disconnected (normal left inverted right x axis y axis)


```

Anoter few specs: 
Affected monitor: Phillips 220e1
OS: Ubuntu 16.04
GPU: RX480 4GB

Im also running the newest AMDGPU-PRO driver.

Any help is appreciated!

---

### Post by efflandt on 2017-03-24
Is there some reason that you are not simply using DVI. Then your graphics card would know the capabilities of your monitor and should automatically be the proper resolution. VGA is analog, so it does not have that information.

---

