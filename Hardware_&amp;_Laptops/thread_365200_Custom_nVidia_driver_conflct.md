---
title: "Custom nVidia driver conflct"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by Jefferson Heard on 2007-02-19
I am running the newest from nVidia version of my video driver, which is needed to support my dell port replicator (the driver available from non-free in Edgy will only use VGA, while the new driver will use DVI).  I also have linux-restricted-modules installed to support my Intel ipw3945-based wireless card.  

Now here's the problem.  Whenever I boot up, the nvidia kernel module that gets installed is NOT the version that I installed, but the version that linux-restricted-modules comes with, meaning that the Xorg driver won't load and GDM crashes at boot, which is a real pain.  The crazy thing is that if I do 

$ sudo rmmod nvidia
$ insmod /lib/modules/2.6.17-10-generic/kernel/drivers/video/nvidia.ko

then the correct driver is installed and I can restart GDM.

So where is the nvidia kernel module getting loaded from?

---

