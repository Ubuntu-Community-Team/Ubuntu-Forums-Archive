---
title: "HDMI not working after upgrade from 12.10 to 13.04"
date: 2013-05-15
forum: Hardware
---

### Post by epix_ian on 2013-05-15
Hi,

I upgraded from 12.10 yesterday on my Acer Aspire S3 laptop and lost the HDMI output that had been working fine in 12.10.

The xrandr output shows:

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

In 12.10 it definitely had a HDMI1 [in my history I have lines like xrandr --output LVDS1 --pos 1280x700 --output HDMI1 --left-of LVDS1 from when I was playing with it in November]. I've been running with HDMI as my second monitor and now can't live without it!

Does anyone have any thoughts on where my HDMI has gone to?

Thanks

Ian

---

### Post by epix_ian on 2013-05-15
I've booted with the previous kernel and HDMI still doesn't work, so I don't think it's a kernel issue.

My system settings -> details -> graphics shows:

Driver Intel Sandybridge Mobile
Experience Fallback

---

### Post by epix_ian on 2013-05-16
My laptop crashed today, and when I rebooted the HDMI was working again. I had tried to swap intel_drv.so for the one from 12.04 but that hadn't worked, so swapped it back. But that was a few hours before the crash and rebooted a couple of times in that period. The only sane thing that I can think happened between the last boot and the crash that "fixed" me was that I used usb-creator-gtk to burn a recovery usb stick in case my messing with intel_drv.so ended in disaster. 

I'm not happy that this is an explanation, and I've no idea why HDMI went away, and then came back again. Ah well, there are more things in heaven and earth.

---

