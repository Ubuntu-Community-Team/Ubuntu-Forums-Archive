---
title: "Compile module from kernel headers for generic kernel?"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by diehardyouth on 2008-02-16
Hi.

I want to compile a module that's in the kernel source, but I don't want to recompile a new kernel (i'm running the generic kernel and don't feel like recompiling other modules for this)

Is there a way to compile a module that was never included in the kernel, but can be compiled with the kernel?

The module I have in mind is the USB Keyspan module (USB to serial adapter)

Thank you

---

### Post by 444 on 2008-02-16
Install the Linux source using apt-get. Then:

tar xjf /usr/src/linux-source-2.6.22.tar.bz2
cd linux-source-2.6.22
cp /boot/config-`uname -r` .config
#modify the config (not drastically or the module will be incompatible)
make
#let this run for minute (compile build stuff), then stop it with ctrl-c"
make path/to/module.ko

---

