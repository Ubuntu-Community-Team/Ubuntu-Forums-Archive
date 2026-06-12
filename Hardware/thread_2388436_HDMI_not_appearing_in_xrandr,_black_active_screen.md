---
title: "HDMI not appearing in xrandr, black active screen"
date: 2018-04-02
forum: Hardware
---

### Post by Shadyjames on 2018-04-02
Hello friends, I have a pair of identical monitors (both recognised by nvidia-settings as "LG Electronics LG IPS FULLHD"), both of which are connected to the same video card (which according to lshw is a GF119 [GeForce GT 610]). One is connected via VGA, the other is connected via HDMI, and I am trying to configure a dual monitor setup.

The monitor that is connected via VGA is working perfectly, and the monitor that is connected via HDMI is being a bit strange. It is ACTIVELY showing a completely black screen (with no i3bar, no background) onto which I can drag my mouse, which makes a little X shape. Furthermore when I tried to troubleshoot, HDMI-0 is completely missing from xrandrs output:

```
james@james-desktop:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1440x900       59.9  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1280x800       59.8  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)

```

I am kind of at a loss to what to do about this. I've already updated to the latest proprietary nvidia drivers that were available, meaning I am now on 384.111

---

### Post by Shadyjames on 2018-04-02
So after some troubleshooting that can only be described as occult, i discovered that the issue does not occur if I plug in the hdmi monitor while the computer is both on and logged in - up until now I had one-and-done plugged it in while the computer was off. After i did this it appeared in xrandrs output and I was able to enable/configure it in nvidia-settings

---

