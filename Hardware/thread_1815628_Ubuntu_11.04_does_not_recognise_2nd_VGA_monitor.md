---
title: "Ubuntu 11.04 does not recognise 2nd VGA monitor"
date: 2011-07-31
forum: Hardware
---

### Post by desss. on 2011-07-31
hi everyone,
I would like to solve my problem with dual monitors. So far I have been using my extern video-card (nVidia). Now i have bought a new monitor and would like to make Ubuntu work in the dual-monitor mode. My internal video card (intel) has got 1 VGA output (same as nVidia). The problem is that when I plug in both monitors, only 1 appears to work. Also a weird thing is happening: when I logout/login (restart X server aswell I am guessing) - it makes the 2nd monitor blink - and even a Ubuntu boot screen appears - but that is all it does, the boot screen stays there till I turn the PC off.

Here is what I found out about my video cards so far:

```
lspci -nn | grep VGA:
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
05:04.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15)
```

I would appreciate any help - how to config something or run tests even - thank you for your help

---

### Post by desss. on 2011-07-31
Any help?

---

### Post by desss. on 2011-08-01
```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1
```

---

### Post by realzippy on 2011-08-01
Problem is that you run an
Optimus laptop.
One monitor port is dedicated to the intel graphics,the other to nvidia.
Do not think that you will find a solution.
More about optimus:

[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)

---

### Post by LapsedCatholic2010 on 2011-08-02
I am having a similar problem upon which removing the second monitor I am asked if I want to restore backup video configuration upon a reboot. 

Here's my problem when I boot up the laptop the second monitor works a little past the GRUB splash screen and before the user/owner login. 

The main computer is a Dell Inspiron 1150. The second monitor is a Dell 14" although System Monitor Preferences reports that it's a 17" monitor.

When I run some checks I figure that the second monitor is registering
i.e when I run xrandr

-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
 

Other information
The  VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

