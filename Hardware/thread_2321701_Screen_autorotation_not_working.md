---
title: "Screen autorotation not working"
date: 2016-04-23
forum: Hardware
---

### Post by christianbrooker on 2016-04-23
Hello. I've just installed Ubuntu Gnome 16.04 fresh and have upgraded to  Gnome 3.20 immediately. My PC is an HP Spectre 360 which is a hybrid  with a swivel screen to turn it into a tablet.
My bug is when i rotate the screen nothing happens. From googling I've discovered that screen rotation should work. In addition, when i return the screen back to normal orientation airplane mode becomes enabled.
I need some help to troubleshoot and find out why my screen rotation is not working and why my sensors think that me rotating the screen to normal orientation is actually me pressing the airplane mode button. I have no idea where to start. Thanks.

---

### Post by chris2132 on 2016-04-24
I am having the same issue. But what is very odd is after a fresh install..  at some point the rotation populated with more than normal. The screen did have the rotation on my external monitor. but after a restart at some point, it has now since disappeared.

***Addition***
So, I at least on my system, I have narrowed down to why the rotation doesn't work. The Nvidia Driver looks like is the issue. if I go into X server and switch the PRIME profile to using Intel(Power Saving Mode) the rotation option is populated again. But Using that option is obviously less than ideal and Also.. more importantly.. when trying to shutdown down, just sticks. No message... just a single white cursor. My system is an MSI-GS60 (skylake). Other than this issue...everything seems to be working fine.

---

### Post by christianbrooker on 2016-04-24
> **chris2132 said:**
> I am having the same issue. But what is very odd is after a fresh install..  at some point the rotation populated with more than normal. The screen did have the rotation on my external monitor. but after a restart at some point, it has now since disappeared.

***Addition***
So, I at least on my system, I have narrowed down to why the rotation doesn't work. The Nvidia Driver looks like is the issue. if I go into X server and switch the PRIME profile to using Intel(Power Saving Mode) the rotation option is populated again. But Using that option is obviously less than ideal and Also.. more importantly.. when trying to shutdown down, just sticks. No message... just a single white cursor. My system is an MSI-GS60 (skylake). Other than this issue...everything seems to be working fine.


The HP Spectre 360 only has integrated intel graphics so it's not an NVIDIA issue for me. I have still got no idea why rotating the screen turns airplane mode on.

As a workaround I've got some keyboard shortcuts to manually rotate the screen:
xrandr --output eDP1 --rotate left (bound to Super+F4)
xrandr --output eDP1 --rotate normal (bound to Super+Alt+F4)

Hope this helps until there's a proper fix.

---

### Post by chris2132 on 2016-04-24
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
eDP-1 connected primary 1920x1080+0+0 344mm x 194mm
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
DP-1 disconnected
HDMI-1 disconnected
HDMI-2 connected 1920x1080+1920+0 509mm x 286mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.08    70.07    60.00  
   1440x480      60.00    59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    66.67    60.00    59.94  
   720x400       70.08  


I've appended Option "RandRRotation" "True" to xorg.conf

but I can't rotate using xrandr 

i get "*xrandr: output HDMI-2 cannot use rotation "left" reflection "none""*

---

### Post by virgosun on 2016-04-25
> **christianbrooker said:**
> Hello. I've just installed Ubuntu Gnome 16.04 fresh and have upgraded to  Gnome 3.20 immediately. My PC is an HP Spectre 360 which is a hybrid  with a swivel screen to turn it into a tablet.
My bug is when i rotate the screen nothing happens. From googling I've discovered that screen rotation should work. In addition, when i return the screen back to normal orientation airplane mode becomes enabled.
I need some help to troubleshoot and find out why my screen rotation is not working and why my sensors think that me rotating the screen to normal orientation is actually me pressing the airplane mode button. I have no idea where to start. Thanks.

I am familiar with Gnome 3.18 since 15.10. Some day ago I upgrade to 16.04 and rotation work fine for me, I also discover there is new touch screen on/off switch in top panel.
However I have not tested new desktop much. I found this one for touch screen today, anyone try and give an idea [http://touch-base.com/](http://touch-base.com/)
My laptop is Lenovo Yoga 500

---

