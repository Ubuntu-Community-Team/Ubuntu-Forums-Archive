---
title: "New HDMI-DVI Cable Works On Desktop, Not Laptop"
date: 2015-01-08
forum: Hardware
---

### Post by llanitedave on 2015-01-08
I have two systems running ubuntu 14.04, a homebuilt desktop with a GeForce GTX 750 add-on card and an Acer laptop with a GeForce GTX 760M stock graphics.  I have an older model Acer 22" LED screen with VGA and DVI inputs, but no HDMI.  My desktop card has VGA, DVI, and HDMI outputs, but the laptop only has VGA and HDMI.  
Until today, I only had a VGA cable, which gave a poor and distorted result when hooked up to the add-on card on the desktop, but worked fine with the stock motherboard output on the desktop as well as the VGA output on the laptop to show the monitor as a second screen.  Today I bought an HDMI -> DVI cable to give me a real digital display and make my desktop graphics card useful.  Hooking it up to the HDMI output on the desktop, it works great, but when attached to the laptop, it's not detected at all.

The desktop graphics driver is the open-source Gallium 0.4, while the laptop driver is the proprietary Nvidia 331.113.  To test this, I switched the laptop to the open-source x-org driver and rebooted.  Made no difference.

I ran xrandr, and here is the relevant output:

:~$ xrandr 
Screen 0: minimum 8x 8, current 1920 x 1080, maximum 16384 x 16384 
eDP1 connected1920x1080+0+0 (normal left inverted right x axis y axis) 382mm x215mm 
   1920x1080     60.0*+   59.9  
   1680x1050     60.0     59.9  
   1600x1024     60.2  
   1400x1050     60.0  
   1280x1024     60.0  
   1440x900      59.9  
   1280x960      60.0  
   1360x768      59.8     60.0  
   1152x864      60.0  
   1024x768      60.0  
   800x600       60.3     56.2  
   640x480       59.9  
VGA1 disconnected(normal left inverted right x axis y axis) 
**HDMI1 disconnected(normal left inverted right x axis y axis) **
VIRTUAL1disconnected (normal left inverted right x axis y axis)  

(Bolded the HDMI1 line).

Checking the internet, this seems to be a rather common problem, and I haven't stumbled across a solution.  Is there any way to get the second screen working without going back to VGA?

---

### Post by llanitedave on 2015-01-09
Well, I stumbled on *a* solution, no genius here.  If I attached the VGA and the HDMI cables to the laptop at the same time, and then removed JUST the VGA cable, the HDMI connected and remained working.  It's holding it's own now, so with no more insight than I had before, I'll just call this one "solved".

---

