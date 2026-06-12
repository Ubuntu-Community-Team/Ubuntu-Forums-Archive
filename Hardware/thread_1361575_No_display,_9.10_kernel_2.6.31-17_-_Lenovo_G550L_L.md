---
title: "No display, 9.10 kernel 2.6.31-17 - Lenovo G550L Laptop"
date: 2009-12-22
forum: Hardware
---

### Post by raikou on 2009-12-22
As title says...
I did a apt-get do-release-upgrade from 9.04 to 9.10
I defaulted all the configs it asked me to default during upgrade.

Now I can't get a display when I boot up, unless I boot up in 2.6.28-17... which seems to be extremely slow compared to in jaunty

the annoying thing is... nomodeset just reboots me and I can't even use the newer kernel with a command line.
i want to use this newer kernel so i can use certain wifi drivers with kismet.

---

### Post by raikou on 2009-12-22
fixed by adding:
i915.mode=0
onto the end of the kernel line in grub for kernel 2.6.31-17

---

