---
title: "fglrx driver &amp; 9.04, 64 bit?"
date: 2009-05-16
forum: Hardware
---

### Post by akos.maroy on 2009-05-16
I'm wondering what happened to the fglrx driver support to unbuntu with 9.04? in 8.10, it was simply listed in System -> Administration -> Hardware drivers

now when I open this window - nothing is shown.

I can do apt-cache search fglrx, and then I can install the driver manually with

sudo apt-get install xorg-driver-fglrx

but why the change?

---

### Post by akos.maroy on 2009-05-16
and, actually installing xorg-driver-fglrx ruins my laptop unusable. as soon as I just logged out, X was broken. upon reboot, X comes up, but hangs before the login screen (just scattered patterns visible). I see 3 times a forced restart of X, and then the machine hangs totally.

rebooting in recovery mode and running xfix doesn't fix the issue either

the only remedy was to reboot in recovery console, and remove the xorg-driver-fglrx package.

what gives? this used to work fine with 8.10. now I can't run fast OpenGL programs anymore :(

---

