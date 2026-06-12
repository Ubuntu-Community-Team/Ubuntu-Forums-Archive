---
title: "Nvidia problems (kind of)"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by orion413 on 2007-04-11
Hi everyone,

I'm running Feisty on a brand new HP Pavilion laptop with an Nvidia graphics card. The nvidia driver provided in the repository didn't work, so I had to use the nvidia installer instead. It works great, except that every time I reboot my computer, X11 doesn't load. To get it to run, I have to boot into runlevel 1, reinstall the nvidia driver, and then init 5. I'm pretty sure this means that the driver isn't loading.

I did an lsmod to make sure that the 'nvidia' driver was there and I made sure to blacklist the 'nv' driver. Thanks in advance your help:)

---

### Post by zekica on 2007-04-11
I don't know how Feisty handles restricted drivers, but I think the problem is that you have two compiled nvidia kernel modules (one from linux-restricted-drivers package, and the other from official nvidia drivers).

In edgy, I had to edit: **/etc/default/linux-restricted-modules-common**
and change this line:
DISABLED_MODULES=""
to something like:
DISABLED_MODULES="nvidia nvidia_legacy"

After reboot, everything worked like it should.

---

### Post by orion413 on 2007-04-11
Thank you for responding! I'll give it a try and get back to you:D

---

### Post by orion413 on 2007-04-12
It worked! Thank you!

---

