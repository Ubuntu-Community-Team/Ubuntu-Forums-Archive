---
title: "Compiling USB drivers"
date: 2008-07-24
forum: Hardware
---

### Post by lionfish on 2008-07-24
I bought a USB scope (DSO-2100 USB) a while ago. I've not been able to find any usb drivers for linux for it, so thought I'd look into writing my own (if anyone knows of any, that I've not found, please say!)

I've fallen at the first hurdle though: I thought I could modify one of the drivers already bundled, but I don't seem to even be able to compile them.

I tried using the Makefile in the usb source directory, ie:
/usr/src/linux-source-2.6.22/drivers/usb/misc
where I ran "make usbled". This came up with a bunch of compile errors, starting with:

```
usbled.c:14:24: error: linux/init.h: No such file or directory
usbled.c:15:24: error: linux/slab.h: No such file or directory
usbled.c:16:26: error: linux/module.h: No such file or directory
usbled.c:17:23: error: linux/usb.h: No such file or directory
...
```


I then tried compiling a copy of it manually, by running:

```
sudo gcc usbled.c -I /usr/src/linux-source-2.6.22/include -D__KERNEL__ -DMODULE -DCONFIG_M586 -DCONFIG_X86_L1_CACHE_SHIFT=7 -DCONFIG_HZ=250 -I /usr/src/linux-source-2.6.22/include/asm/mach-default -DKBUILD_MODNAME=\'usbled\'
```

(I made up these parameters by looking in the kernel .config file or something, can't remember now)

This had loads of errors too, starting with:

```
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
/tmp/cc9zXMPh.o: In function `change_color':
usbled.c:(.text+0x27): undefined reference to `__kmalloc'
```

I get compile errors either way. What's the correct way to compile these drivers? 

Thanks!

---

