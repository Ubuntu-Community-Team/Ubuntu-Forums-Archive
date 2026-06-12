---
title: "Legacy nvidia driver issue"
date: 2010-02-17
forum: Hardware
---

### Post by mvandemar on 2010-02-17
I recently installed Mint 8 on a friend's machine and am having an issue with the video driver. I posted on the Mint forums as well, but since the error starts out identifying itself as an Ubuntu error, and since Mint is based in large part on Ubuntu, hopefully someone here might have some experience with this issue.

The machine is an older emachines t4160, with an nvidia TNT2 64 video card. I installed the legacy drivers located here:

[http://www.nvidia.com/object/linux_display_ia32_71.86.13.html](http://www.nvidia.com/object/linux_display_ia32_71.86.13.html)

The Hardware Drivers applet does not show any proprietary drivers found, however, and the "Nvidia X Server Settings" applet tells me "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server". Doing that has no effect even though it does appear to work (ie. a backup conf file is created, no errors, etc).

When I boot up from scratch, I always have to choose safe graphics mode after getting the following error msg (this is the one that says Ubuntu in it, just ftr):

```
Ubuntu is running in low graphics mode. The following error was encountered:
(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available
```

Searching on this error results in very little information out there being returned, but I *think* it has to do with the current version of X server not supporting the legacy driver. If that is the case, is there a way to simply install an older version of xorg?

Thanks. :)

-Michael

---

