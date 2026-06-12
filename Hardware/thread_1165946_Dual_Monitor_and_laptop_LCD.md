---
title: "Dual Monitor and laptop LCD"
date: 2009-05-21
forum: Hardware
---

### Post by skitch20 on 2009-05-21
Hi everyone

I have a HP elitebook 8530p (HD Radeon 3650) with ubuntu 9.04 and xorg-driver-fglrx (2:8.612-0ubuntu1). I have a docking station where I connect 2 external monitors, one in DVI and the other on VGA. Everything works great when I only use the external monitors but when I try to activate the laptop LCD one of the other stops working.

Is it possible to have all 3 monitors activated at the same time?

Thanks

---

### Post by thebird on 2009-05-26
You can always try:

patrik@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 2240 x 900
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       65.0*+
   800x600        72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
patrik@ubuntu:~$ 

My laptop computer's built in screen is LVDS and the external is VGA. If all of yours are listed you can try xrandr.

For my 22" external screen I use:

xrandr --output  VGA --fb 1440x900 --output LVDS --fb 1440x900 --off

---

