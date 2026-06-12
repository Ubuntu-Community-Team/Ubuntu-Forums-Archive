---
title: "DVI to HDMI on 17.10 gives a blank screen"
date: 2018-04-20
forum: Hardware
---

### Post by dehydratedpaani on 2018-04-20
Hi,
New to Ubuntu here. Trying to get my DVI to HDMI link working on Ubuntu 17.10. Works on Windows 7.
VGA link to monitor works fine. DVI to HDMI adapter showing blank screen on TV even after making it primary display.

I have Intel Integrated Graphics Card
```
 lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)


```

xrandr 
```
xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA-1 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024     60.02*+  75.02  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
HDMI-1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1280x720      50.00 +  60.00    59.94  
   1920x1080     60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     60.02* 
   1366x768      59.79  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  
DP-1 disconnected (normal left inverted right x axis y axis)

```

Display too shows/detects my TV. Attaching screen-shot below.

Please help 

[IMG]https://i.imgur.com/Gqqy8kz.png[/IMG]

---

### Post by kerry_s on 2018-04-20
have you tried unplugging & plugging back in?

some times it can be finicky, i think mines worn a bit, it can take 2 to 3 tries for me.

---

### Post by Autodave on 2018-04-20
Another trick I have found is to make sure all displays are turned on  efore powering up the PC.

---

