---
title: "Multiple Monitor not working with Ubuntu 12.10"
date: 2014-05-16
forum: Hardware
---

### Post by Ajit_Mathew on 2014-05-16
Hi,
I have a DELL Inspiron 15Z with NVIDIA graphic card. I connected a DELL S2240L to my laptop to use it as a seconday screen using HDMI port but the monitor is not being detected. I tried installing latest NVIDIA drivers but after installation, there is no display on reboot.

xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

Please help.

---

### Post by QIII on 2014-05-16
Hello!

Did you just install 12.10?  If so, are you aware that it reaches End of Life today, the repos will be moved and it will no longer receive updates?

Rather than trying to solve a problem with 12.10 on the day of its funeral, you might do well to install 14.04.  13.04 is already out of support and 13.10 will be in July.

Cheers!

---

