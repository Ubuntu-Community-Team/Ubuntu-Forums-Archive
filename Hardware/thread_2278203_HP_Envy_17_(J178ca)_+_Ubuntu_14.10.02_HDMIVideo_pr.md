---
title: "HP Envy 17 (J178ca) + Ubuntu 14.10.02 HDMI/Video problem"
date: 2015-05-14
forum: Hardware
---

### Post by dcbasso on 2015-05-14
Hello All, I have the HP Envy J178ca (17' FULL HD, i7 4700mq, 16gb), hybrid video card (HD4600 and Nvidia GT740m), and one video output, HDMI.
So install all property drivers from nvidias and set to use only the HD4600 (low power consumption, and good for work), and I have one External Monitor (LG 23' Flatron M237WA).
Well, the video quality on the notebook display is VERYYYY good (FULL HD), but my monitor LG, the webpages, images and fonts appers to be "squared"... on the LG I don't have a readlly rounded borders, but on the Laptop is everything GOOD!

So, I really don't know how to solve it... 
I not very expert linux user, but I try xrandr and xdpi info... and nothing change...

I check, that appears (not sure) that xdpyinfo only shows one DISPLAY, and seems to be a very high resolution... below a litle part of "xdpyinfo" command:

xdpyinfo:
```

screen #0:
  dimensions:    3840x1120 pixels (1016x296 millimeters)
  resolution:    96x96 dots per inch

```

xrandr:
```

Screen 0: minimum 8 x 8, current 3840 x 1120, maximum 32767 x 32767
eDP1 connected primary 1920x1080+1920+40 (normal left inverted right x axis y axis) 381mm x 214mm
   1920x1080      60.0*+   59.9     40.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      59.9*+   60.0     50.0     59.9     30.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       75.0  
   1152x864       60.0  
   1280x720       60.0     60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     70.1     60.0  
   1440x480i      60.1     60.1  
   832x624        74.6  
   800x600        75.0     60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     60.0     59.9  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

I really not sure how to fix the Video quality on LG/HDMI monitor...
On my old laptop with kubuntu, the same monitor in VGA cable has a better video quality!!!

---

