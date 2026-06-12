---
title: "Intermittent freezes on laptop"
date: 2008-08-11
forum: General Help
---

### Post by mexp on 2008-08-11
I installed Hardy on Acer Aspire 1450 (AMD Athlon 1800 with 512 MB RAM), and system works fine except for intermittent freezes when using the computer. For example, when viewing a normal web page with no frills, the system freezes for a second or three, and it's very annoying. It doesn't seem to relate to the content of a web page. On other programs the freeze is not so obvious, but it does happen.

The system monitor shows that the CPU is not at 100% at the time of the freeze, so I can't really figure out what could cause the problem.

How should I troubleshoot this issue?

---

### Post by cmnorton on 2008-08-11
Look through your logs (/var/log) for something interesting.

I had a Travel Mate 630 do the same thing. If you're using the nvidia driver, try another. (I'm going with it might be a graphics problem.)

You can boot into recovery mode, run dpkg-reconfigure xserver-xorg, take the default answers but choose the vesa driver. This will be a lot of work and testing, but it might fix your problem.

---

### Post by mexp on 2008-08-15
Thanks for reply. There's an ATI Radeon Mobility 9200 card in this machine, how do I know if the *ati* or *radeon* driver has been loaded? Should that show on the xorg.conf?

On the Xorg.0.log the card is recognised ok, and there's a line (II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so. Does that mean that this driver is in use?

Also the System > Administration > Drivers shows that there are no restricted drivers in use.

---

### Post by mexp on 2008-08-15
Further, Synaptics shows that xserver-xorg-video-ati driver is installed.

---

### Post by mexp on 2008-09-18
Back to this problem... I ran the dpgk-reconfigure, but I didn't get any option to choose the vesa driver. Is there another way I could use that driver, or to change to another ATI driver?

---

