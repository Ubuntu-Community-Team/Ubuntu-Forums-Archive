---
title: "Can't set monitor resolution"
date: 2011-10-13
forum: Hardware
---

### Post by Gurth12345 on 2011-10-13
I've recently installed Ubuntu 11.4 on a rather elderly computer I'm forced to use, and can't get the resolution of the monitor to the one I want. Right now it's using the default 1024x768 but I would like it to be 1280x1024 in order to have some more screen real estate -- however, the screen setup doesn't detect the monitor so it only offers a bunch of default resolutions, all of them smaller than what I want.

So far I've tried setting stuff up using xrandr, which gives the warning "xrandr: Failed to get size of gamma for output default" when I try to add a 1280x1024 modeline (as determined using cvt), then says it doesn't know a mode "1280x1024" if I try the --addmode option. I also attempted specifying data in xorg.conf, but this has so far only resulted in a blank screen that required me to remove my additions and restart the X server in order to get a picture again.

The monitor is a [Dell P793](http://support.dell.com/support/edocs/monitors/p793/En/specs.htm) and the video card an [ASUS V9520 Magic/T](http://www.asus.com/999/html/events/vga/v9520m/overview.htm) (NVIDIA GeForce FX 5200).

Any help would be appreciated :)

---

