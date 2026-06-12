---
title: "Upgrading 2.6.29 kernel in Jaunty"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by doesntcount on 2009-07-05
After months of problems with my bluetooth usb dongle, I've learned that my problems might be fixed by a new kernel:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502)

I've googled around, and there doesn't seem to be a reasonable howto on upgrading to an unreleased kernel. I tried adding karmic sources, but that didn't help. Am I to go directly to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.6/) and downloaded the package myself? If I do that, seems like I'll have to recompile my kernel modules, especially my nvidia module.

I'd like to know if I'm going about this all wrong. Seems like there should be an easier way to do this.

Thanks for the help.

---

### Post by doesntcount on 2009-07-05
This seems to be the way to do it:

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

And apparently there's this thing called DKMS which will take care of making sure your nvidia driver is compatible with your kernel, so that's good.

Hopefully this works!

---

### Post by NewbieNik on 2009-07-05
hey doesntcount,

Can you post on success or failure on this? Would be interested in your experience and views on it's worthiness as a fix or whether to wait for the official Ubuntu update/

---

### Post by doesntcount on 2009-07-05
Worked great. Surprised there wasn't a howto for this.

But even greater news is that the upgrade to 2.6.29 solved my bluetooth problems that I've ever since upgrading from 2.6.24! Which means I can now run xbmc and use my wiiremote to navigate.

---

