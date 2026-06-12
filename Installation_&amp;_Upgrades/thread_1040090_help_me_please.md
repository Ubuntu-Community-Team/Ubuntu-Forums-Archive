---
title: "help me please"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by udblfh on 2009-01-15
"there is one update available",but when i tried to install it,an error occurred.
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

---

### Post by avtolle on 2009-01-15
Do you have a separate partition for boot, mounted at /boot? If so, it may be full (or almost full). Run ```
df -h
``` from the terminal. If said partition exists, and has little room, then you should delete old kernels using Synaptic (be careful to not delete the kernel you are presently using) to free up some space, and then try updating again.

---

