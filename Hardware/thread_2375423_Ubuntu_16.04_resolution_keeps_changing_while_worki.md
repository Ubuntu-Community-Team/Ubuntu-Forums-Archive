---
title: "Ubuntu 16.04 resolution keeps changing while working"
date: 2017-10-24
forum: Hardware
---

### Post by kuvasney on 2017-10-24
Hi Everyone.
I've got a Dell Inspiron 5110 laptop working with dual monitors. My graphic information from inxi -Fx is:

```
Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: Advanced Micro Devices [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
           bus-ID: 01:00.0
           Display Server: X.Org 1.19.3 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.04hz, 1024x768@75.03hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 17.2.2 - padoka PPA Direct Rendering: Yes

```



My second screen is a LG Flatron W2252TQ connected on VGA-1 port.

my x-randr info, after I mannually change the screen resolution to the expected one (it swtiched back after few seconds)

```

$xrandr
Screen 0: minimum 320 x 200, current 3046 x 1050, maximum 8192 x 8192
LVDS-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768      59.99*+  40.06  
   1360x768      59.80    59.96  
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
VGA-1 connected 1680x1050+1366+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050     59.88*+  59.95  
   1280x1024     75.02    60.02  
   1440x900      74.98    59.89  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32    56.25  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

```

Everytime I'm working something like an auto process run and it just changes my screen resolution. And keeps changing for a long time (sometimes took me the entire day). 
I've made a short vídeo of the problem [https://www.youtube.com/watch?v=lkLl8IbOscM](https://www.youtube.com/watch?v=lkLl8IbOscM)


Does anybody know how to fix this?

---

### Post by kuvasney on 2017-10-28
:confused:... No answers and no views. Am I doing anything wrong?

Could it be that Ubuntu haven't properlly installed my secondary monitor?

---

### Post by fredwntr1 on 2017-10-29
Is this only on Linux because it seems almost as if you cables are loose

---

### Post by kuvasney on 2017-10-30
doesn't seem to be it, on Windows it works pretty fine. I am using a VGA cable

---

### Post by kuvasney on 2017-11-14
just for the record, what I've done already (and without success):

switched monitors (an AOC 19' plugged in a VGA port)

switched cables (VGA - VGA and DVI - HDMI)

set this on startup: 
/bin/bash -c "sleep 10&&xrandr --output LVDS-1 --mode '1360x768' --primary&&xrandr --auto --output VGA-1 --mode '1680x1050' --right-of LVDS-1"

set this on terminal everytime it changes the screen resolution: 
xrandr --output LVDS-1 --mode "1360x768" --primary&&xrandr --auto --output VGA-1 --mode "1680x1050" --right-of LVDS-1

the only thing that worked was install Windows. But I don't want it because Linux is better for web development.

---

