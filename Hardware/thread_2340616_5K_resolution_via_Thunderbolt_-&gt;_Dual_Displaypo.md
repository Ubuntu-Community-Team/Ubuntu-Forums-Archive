---
title: "5K resolution via Thunderbolt -&gt; Dual Displayport"
date: 2016-10-20
forum: Hardware
---

### Post by xyrochron on 2016-10-20
I'm running Ubuntu 16.10 with kernel 4.8.1 on a Precision 5510 with nvidia drivers, and bumblebee installed. I've got a Plugable Thunderbolt 3 to Dual Displayport adapter, with DP cables going to the monitor. The monitor provides 5K resolution when connected via both DP cables (on Windows). On Linux, I get 4K on the external monitor. xrandr finds TWO external monitors - one 4K and one smaller. I'm no expert with xrandr, xorg, etc. , and was wondering if there's some way of telling Linux that there's actually one external monitor, and that's a 5K one. The nvidia driver version is 367.57 for the Quadro M1000M graphics card in the laptop. xrandr gives me the following:

```


Screen 0: minimum 320 x 200, current 7680 x 2160, maximum 8192 x 8192
eDP-1 connected primary 3840x2160+3840+0 (normal left inverted right x axis y axis) 346mm x 194mm
   3840x2160     60.00*+
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   1920x1200     59.95  
   1920x1080     59.93  
   1600x1200     60.00  
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
DP-1 connected (normal left inverted right x axis y axis)
   848x480       59.74 +
   2560x2880     59.98    29.99  
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected 3840x2160+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   3840x2160     60.00*+  60.00  
   2560x1440     59.95 +
   2560x2880     59.98    29.99  
   1920x1200     59.88  
   1920x1080     60.00  
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     60.02  
   1280x800      59.81  
   1024x768      60.00  
   800x600       60.32  
   640x480       60.00    59.94  
HDMI-2 disconnected (normal left inverted right x axis y axis)



```

Any help is appreciated. Thanks.

---

### Post by xyrochron on 2016-10-26
Erm...bump? (sorry...)

---

### Post by aweiler on 2016-11-21
Same issue here!

---

