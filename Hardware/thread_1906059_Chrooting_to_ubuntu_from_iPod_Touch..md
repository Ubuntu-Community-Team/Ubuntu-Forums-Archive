---
title: "Chrooting to ubuntu from iPod Touch."
date: 2012-01-08
forum: Hardware
---

### Post by Meizirkki on 2012-01-08
Hello.

I got a random idea to slam Ubuntu rootfs on my iPod Touch 3g. But when I try to chroot into it, I get an "Exec format error".

This apparently means that my ubuntu rootfs, created with the rootstock is of incompatible architecture? This is weird. iPod Touch 3g has a Cortex-A8 CPU which according to the rootstock script is exactly what the image was built for.

I decided to try a debian lenny rootfs, since the Debian ARM Eabi port seems to compatible with just about anything... but no. I get the same "Exec format error" when attempting chroot.

I also tried to run the chroot from the debian rootfs, and got a similar error.

Is this Apple playing tricks on me? Does anyone know whether Ubuntu and Debian ARM ports are _really_ incompatible with the CPU of iPod Touch 3g?

---

