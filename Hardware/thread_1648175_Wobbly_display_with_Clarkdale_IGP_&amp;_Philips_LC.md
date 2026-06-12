---
title: "Wobbly display with Clarkdale IGP &amp; Philips LCD"
date: 2010-12-18
forum: Hardware
---

### Post by magneze on 2010-12-18
I have an i5 with the Intel Clarkdale integrated graphics, connected via VGA port to an Philips 170X6 monitor on Ubuntu 10.10.

Windows 7 works (so this isn't a hardware issue), but in Ubuntu the display shakes really really badly.

I've tried generating an xorg.conf and fiddling with various settings within there but I'm now pretty stuck.

I really want to have Ubuntu as primary OS, but it's unusable at the moment. I'm hoping someone can give me some help in getting this video/monitor combination working!

Thanks in advance. :KS

---

### Post by magneze on 2010-12-20
Bump for Monday. ;)

---

### Post by magneze on 2011-01-11
Tried this with a newer monitor connected via HDMI and it all works fine, so there's some issue with detecting the frequency abilities of the older monitor.

---

### Post by WHiZZi on 2011-01-31
Same problem here with brand new install of 10.10 ..

The DVI-D connector seems fine, the VGA output is unusable. At this moment I'm looking at one perfect screen and one bad one.

---

### Post by Niekk on 2011-01-31
I've tried installing the RC of the latest Kernel, with the newest xserver builds. This was still not working for me.
[http://git.kernel.org/?p=linux/kernel/git/ickle/drm-intel.git;a=commit;h=633f2ea26665d37bb3c8ae30799aa14988622653](http://git.kernel.org/?p=linux/kernel/git/ickle/drm-intel.git;a=commit;h=633f2ea26665d37bb3c8ae30799aa14988622653)

---

