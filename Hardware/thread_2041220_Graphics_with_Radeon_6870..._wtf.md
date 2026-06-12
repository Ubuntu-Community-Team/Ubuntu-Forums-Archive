---
title: "Graphics with Radeon 6870... wtf?"
date: 2012-08-12
forum: Hardware
---

### Post by Toupee on 2012-08-12
So, it's been a while since I mucked about with ubuntu, but I'm loving the new install on my SSD with i5.

Problem is, I tried to install the proprietary drivers for my 6870 and things went awry.  Now my second monitor isn't working at it's native resolution of 1650x1080.  I keep getting the message:

The selected configuration for displays could not be applied
required virtual size does not fit available size: requested=(2960, 1050), minimum=(320, 200), maximum=(1680, 1680)

Failed to apply configuration: %s
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: required virtual size does not fit available size: requested=(2960, 1050), minimum=(320, 200), maximum=(1680, 1680)

For what it's worth, when I installed Desura my monitor flickered like six times and things locked up and I had to restart.  But it wasn't until I tried to install the 'additional drivers' that my resolution went all wonky.  And it's not even activated!

Thoughts?

---

### Post by Toupee on 2012-08-12
Problem appears to be resolved as a result of changing xorg.conf as per these instructions. [http://smotko.si/the-amd-linux-drivers/](http://smotko.si/the-amd-linux-drivers/)

I also installed the AMD Catalyst drivers, but that did not fix the problem in and of itself.

---

