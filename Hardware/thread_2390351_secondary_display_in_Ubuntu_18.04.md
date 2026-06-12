---
title: "secondary display in Ubuntu 18.04"
date: 2018-04-28
forum: Hardware
---

### Post by mihai-4 on 2018-04-28
Hello, I upgraded from 16.04 to 18.04 and I seem to have an issue with my HDMI port (which in 16.04 was working ok). I am trying to connect a Benq W1070 projector and it gets detected for a split second and then nothing. Attached my old monitors.xml (the current one is empty), below the output of xrandr:

[ATTACH]279461[/ATTACH]

[I]Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080     60.02*+  60.01    59.97    59.96    59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
DP-1-2 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 disconnected (normal left inverted right x axis y axis)
[/I]
My laptop is an Acer Aspire V Nitro VN7-592G-709V, using an Nvidia GTX 960M with driver version 390, Ubuntu 18.04 is up to date and I already tried reinstalling and reconfiguring the nvidia drivers.

Anyone has a hint where I could start investigating the issue?

Thanks!

---

### Post by howefield on 2018-04-28
Thread moved to the "*Hardware*" forum.

---

### Post by mihai-4 on 2018-05-29
Found a workaround:


        xrandr --addmode HDMI-1-1 1920x1080
        xrandr --output HDMI-1-1 --mode 1920x1080


This sequence of commands enables clone display. However, I still don't see anywhere in Displays/Monitors the secondary display.


Here is the xrandr output (while projector is on):


        HDMI-1-1 disconnected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
           1920x1080     60.02*

---

