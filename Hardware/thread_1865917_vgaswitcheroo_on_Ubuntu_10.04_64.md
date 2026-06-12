---
title: "vgaswitcheroo on Ubuntu 10.04_64"
date: 2011-10-20
forum: Hardware
---

### Post by Rexhunt on 2011-10-20
Hi I have recent bought a laptop to help with my schoolwork and am in the process of getting Ubuntu working on it in a stable state that will last 12 months until I finish my HSC. The laptop is an Acer Aspire Timeline X 5820TG, with 2.4GHz i5 and Radeon Mobility HD 5650 with 1GB.

I have got Ubuntu booted successfully and am happy with it except the battery ccharge indicator applet does not work-shows on AC and fully charged 100% of the time. However this is less of an issue at the moment. To get the hybrid graphics system working I seem to need vgaswitcheroo ([http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)). To this end I have compiled a 2.6.34 kernel successfully ([http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)) and then have compiled a kernel that has vgaswitcheroo enabled, however the folder /sys/kernel/debug/vgaswitcheroo does not exist even though I have checked the kernel with switcheroo enabled does indeed have it enabled```
cp -vi /boot/config-`uname -r` .config
``` then ```
make menuconfig
``` to check if it is enabled in the running kernel (the one I compiled with switcheroo enabled)

So what I'm asking is should I be able to see /sys/kernel/debug/vgaswitcheroo? or is there another way to get switcheroo working?

---

### Post by Rexhunt on 2011-12-22
got a more recent version of the kernel from kernel.org that worked so I went for the latest stable, 3.1.1 which i'm now running successfully...

---

