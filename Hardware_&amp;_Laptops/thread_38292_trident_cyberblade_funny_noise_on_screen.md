---
title: "trident cyberblade funny noise on screen"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by HadroLepton on 2005-05-30
i have ubuntu 5.04 installed on a via kle133 board with onboard graphic trident cyberblade. the monitor is a samsung syncmaster lcd. resolution used is 1280x1024, refresh 60 hz.

i noticed that the image on screen has a funny noise, which seems to be related to processor usage. because everytime processor goes up the noise appears, and if there is no processor activity there is also no noise.

the noise is some sort of colored lines moving up and down from the edges of high contrast (windows borders for example).

i have tried to run dpkg-reconfigure xserver-xorg (info from other threads) but i don't know what to change from default answers

if i change the resolution to 800x600 the noise is gone. change back to 1280x1024 noise back again.

this behaviour did not occur under windows (win2k)

any ideas?

---

### Post by HadroLepton on 2005-06-01
*bump*
anyone?

---

### Post by Smerp! on 2005-07-14
[Linux Kernel Bug 4312 - tridentfb: flicker when disk I/O is happening](http://bugzilla.kernel.org/show_bug.cgi?id=4312). 

It looks to be a known problem with the tridentfb driver in recent 2.6 kernels.

---

