---
title: "Wifi problem with kernel version 2.6.32-29"
date: 2011-03-07
forum: Hardware
---

### Post by thanasis57 on 2011-03-07
Running Ubuntu 10.04 on a Toshiba Satellite L505-141 laptop.

With kernel version 2.6.32-28, the wifi works just fine (with Network Manager but not with wicd).
When I updated the kernel to 2.6.32-29, it stopped recognizing the wifi and could not scan any of the existing networks.
The problem goes away when I boot with the previous kernel version (hold down shift during boot to bring up grub).

This is perfectly reproducible on more than one (encrypted) networks. I didn't try any non-encrypted ones.

I will be working with version 2.6.32-28, so this post is just to suggest this as a workaround to anyone sharing this problem.

---

### Post by duuso on 2011-03-16
edit: false information

---

### Post by thanasis57 on 2011-03-21
Correction:

The information _was not false_ at the moment this comment was posted. The behavior was *real* and *reproducible*.

However, after some additional updates (if I remember correctly some lib files), the problem has gone  away. Kernel 32-29 worked just fine and now kernel 32-30 also works.

I suppose it was a metter of missing dependencies that were unavailable right after the kernel update?

Anyway, for a period of time the behavior was there.

---

### Post by thanasis57 on 2011-04-23
Similar behaviour after update to kernel 2.6.32-31. Unsecured wifi hotspot detected but could not log in with Network Manager.

After I rebooted with kernel version 32-30, I could log in just fine. I will now try to see whether any new updates allow me to log in with latest kernel version.

---

### Post by KegHead on 2011-04-23
Hi!

You can find an updated kernel here.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

KegHead

---

