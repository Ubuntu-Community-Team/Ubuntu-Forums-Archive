---
title: "Laptop with 2 external monitors"
date: 2021-09-30
forum: Hardware
---

### Post by ldcdc on 2021-09-30
Hello,

I have an HP Probook 6470b with an intel i5-3210M, Intel HD Graphics 4000, and a dock station, otherwise I would not have 3 video outputs.

In Windows I was able to use two external displays and the built-in display simultaneously.

In Kubuntu 20.04 I am only able to use two monitors at the same time, and in order to use the external ones (cause bigger is generally better) I had to resort to using a startup script with several xrandr commands (the built-in display off, then each of the external ones off and then on again). That way I can have the two external monitors on, but the built-in one cannot be made to work.

The error I get when running a command like

```
xrandr --output LVDS-1 --auto

```

...in order to enable the third display, is:

```
xrandr: Configure crtc 2 failed
```

The monitors are detected correctly as far as I can see:


```
xrandr
Screen 0: minimum 320 x 200, current 4480 x 1440, maximum 16384 x 16384
LVDS-1 connected (normal left inverted right x axis y axis)
   1366x768      60.07 +  40.04  
   1360x768      59.80    59.96  
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
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
   1920x1200     59.88  
   1920x1080     60.00    50.00    59.94  
   1920x1080i    60.00    50.00    59.94    50.00  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
HDMI-2 connected 1920x1200+2560+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  

```

I tried a live Ubuntu 21.04, Kubuntu 21.04, Manjaro XFCE, hoping that one of them will be better at detecting my setup. Unfortunately, they all enable two monitors (the built-in one and an external one), and cannot be made to enable the third via their specific GUI.

Can anyone point me in the right direction? Thank you!

---

