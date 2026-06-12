---
title: "UHD and FHD scaling on GTX950"
date: 2016-09-20
forum: Hardware
---

### Post by dmitry46 on 2016-09-20
Hello. I have DELL P2415Q (UHD 3840x2160 on Display Port) and NEC EA231WMi (FHD 1920x1080 on DVI-D), connected on ASUS STRIX-GTX950-DC2OC-2GD5-GAMING. Driver NVidia.
When i drag window from UDH monitor to FHD monitor, wondow become twice - it not good. I whant have same proportion on both monitor.
I'm try to use xrandr:
```
xrandr --output DVI-D-0 --scale 2x2 --mode 1920x1080 --pos 3840x0 --fb 7680x2160
``` but it not work, NEC do not show, have only small (1 pixel) horisontal line on top of screen.
What else I'm can to try?

P.S. xrand output
```
$ xrandr
Screen 0: minimum 8 x 8, current 5760 x 2160, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DP-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 527mm x 296mm
   3840x2160     60.00*+  29.98  
   2560x1440     59.95  
   2048x1280     59.96  
   1920x1200     59.88  
   1920x1080     60.00    60.00    59.94    50.00    23.97    60.00    50.04  
   1600x1200     60.00  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    59.94    59.93  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 connected 1920x1080+3840+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+  50.00    60.05  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1400x1050     59.98  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x800      59.81  
   1280x720      60.00    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
```

---

### Post by dmitry46 on 2016-09-29
Any ideas?

---

