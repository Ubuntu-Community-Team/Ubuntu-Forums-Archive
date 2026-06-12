---
title: "how to use qemu to load kernel image?thanks"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by newbeeonlinux on 2009-03-02
I am having trouble loading the kernal bzImage using qemu under ubuntu. I am trying to load the kernal bzImage under ubuntu using qemu.

I first make menuconfig and then make bzImage.
Then i use: qemu-img create qemu.img 4G
and: qemu -s -S -kernel arch/i386/boot/bzImage qemu.img

Then the following error occurs:
(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15) (*) Direct/Memcpy: Using Generic 64bit memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
  --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
  --> Initialization error!
Could not initialize SDL - exiting

Any suggestion? thanks.

---

