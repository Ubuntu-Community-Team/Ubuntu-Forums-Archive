---
title: "Screen mode unsupported by the monitor after a recommended AMD driver update"
date: 2014-02-08
forum: Hardware
---

### Post by tryphon2 on 2014-02-08
Hello,

I use Ubuntu 12.04 LTS.
I recently intalled some weekly recommended updates. I remember they included a new AMD Catalyst driver. Let's go, I am on a LTS build and I install the advised updates as usual.

After a reboot: black screen with my monitor claiming : unsupported graphic mode !!

With my Ubuntu CD, trying to see what's happening on my system in /etc/X11.

Awful : no Xorg.cong at all... and worse : no Xorg.bak at all !!! Nothing :confused:, everything is gone!

If some programmers read here : please, do not place problematical drivers in the recommended updates that users usually install on their LTS system.

I am not good enough to manually rebuild a new Xorg.conf that could light up my system.

I need your help and I apologise for my dramatic thread.

Configuration: Asus P7P55D EVO, quadcore i7 2,8 GHz, Gainward Radeon HD4870, Samsung T240HD on DisplayPort, Plasma Samsung TV on HDMI, NAS QNAP TS-559

---

### Post by egeezer on 2014-02-08
Check this from the Ubuntu wiki;
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)

I suspect your graphics chip is no longer supported by the fglrx drivers, as it is the same series as mine.  There is a fix down lower on the linked page (under Problem: need to purge -fglrx) which worked for me.

---

### Post by tryphon2 on 2014-02-09
Thank you. Back to the previous version.

Unfortunatly, it is partially solved. When I try to activate my plasma TV in the system parameters, I have this error message:

GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3

I never had this error before. Any idea?

---

### Post by egeezer on 2014-02-09
Sorry, I guess that's a couple of steps beyond my experience.  You might want to start another thread for it.

---

