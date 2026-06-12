---
title: "Should I uninstall xserver-xorg-video-intel on Sky Lake?"
date: 2016-06-09
forum: Hardware
---

### Post by frogotronic on 2016-06-09
I was looking through synaptic and found a comment under the xserver-xorg-video-intel package (which I assume is the Intel video driver).

It says:

[I]This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
and i965 series chips.

This package also provides XvMC (XVideo Motion Compensation) drivers
for i810/i815 and i9xx and newer chipsets.

This package is built from the X.org xf86-video-intel driver module.

[B]The use of this driver is discouraged if your hw is new enough (ca.
2007 and newer). You can try uninstalling this driver and let the
server use it's builtin modesetting driver instead.[/B][/I]

If I'm using a new laptop (2015, 6th generation Intel) with the Sky Lake video chipset (HD520), should I in fact uninstall this package?

Thanks,

---

### Post by bellera on 2016-11-06
I just uninstalled and I don't see any loss of performance. And my cursor-problem with light-locker is solved.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604/comments/261](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604/comments/261)

                        More... about intel drivers...
 [http://forums.debian.net/viewtopic.php?f=6&t=128643#p617404](http://forums.debian.net/viewtopic.php?f=6&t=128643#p617404)

---

### Post by bellera on 2016-11-06
Ohter people removed it, also:

[http://unix.stackexchange.com/questions/259733/this-driver-is-deprecated-in-favor-of-the-server-builtin-modesetting-driver-t](http://unix.stackexchange.com/questions/259733/this-driver-is-deprecated-in-favor-of-the-server-builtin-modesetting-driver-t)

---

### Post by bellera on 2016-11-20
> **bellera said:**
> I just uninstalled and I don't see any loss of performance. And my cursor-problem with light-locker is solved.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604/comments/261](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604/comments/261)

                        More... about intel drivers...
 [http://forums.debian.net/viewtopic.php?f=6&t=128643#p617404](http://forums.debian.net/viewtopic.php?f=6&t=128643#p617404)

I have problems with Google Chrome if I remove xserver-org-video-all (in my case xserver-xorg-video-all-lts-xenial) packages. Chrome works very slow and many times I'v got error application at startup.

Reinstalling the packages solves the problem with Chrome.

I read at some places that graphics acceleration can cause problems using Chrome, [http://www.pcadvisor.co.uk/how-to/internet/how-turn-off-gpu-hardware-acceleration-in-google-chrome-3605455/](http://www.pcadvisor.co.uk/how-to/internet/how-turn-off-gpu-hardware-acceleration-in-google-chrome-3605455/)

---

### Post by cr0wkn0ws on 2017-01-07
> **bellera said:**
> I just uninstalled and I don't see any loss of performance. And my cursor-problem with light-locker is solved.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604/comments/261](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604/comments/261)

                        More... about intel drivers...
 [http://forums.debian.net/viewtopic.php?f=6&t=128643#p617404](http://forums.debian.net/viewtopic.php?f=6&t=128643#p617404)

This solved the persistent issues I had with tearing / Skylake / i915 / i965. Once I removed xserver-xorg-video-intel, I no longer needed to use the 'TearFree' or CLUTTER_PAINT workarounds.

---

