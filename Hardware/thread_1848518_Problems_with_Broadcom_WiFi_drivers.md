---
title: "Problems with Broadcom WiFi drivers"
date: 2011-09-22
forum: Hardware
---

### Post by B_Nut on 2011-09-22
I'm still having problems installing WiFi drivers after following [these instruction]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").  I'm installing 11.04 on a Dell Latitude laptop, I'm positive the hardware is compatible because I've used it before (had a hard drive failure and am reinstalling).  The network controller is a BCM4306.  I am using an ethernet cable and the first set of instructions, even after reinstalling via Synaptic the driver doesn't show up under system>drivers.  No idea what to do next.

---

### Post by aura7 on 2011-09-22
Install these drivers from the undergiven link. Do read the readme given on the site.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by B_Nut on 2011-09-23
Thank you VERY much, I'll give that a shot.

---

### Post by B_Nut on 2011-10-10
OK

I followed the directions in the readme.  When I use "make", I get the following:

error: implicit declaration of function 'init_MUTEX'

And it fails.  What am I doing wrong?

---

