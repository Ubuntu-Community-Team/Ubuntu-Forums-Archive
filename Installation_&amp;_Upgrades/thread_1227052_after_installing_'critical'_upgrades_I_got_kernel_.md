---
title: "after installing 'critical' upgrades I got kernel panic"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by jmkpost on 2009-07-30
Yesterday I had the pop-up alert for updates on my 9.04 installation (32 bit) on my AMD Athlon X2 cpu box. I deselected the updates that were not on the critical list and the updates proceeded to install. Upon auto-restart it would not boot due to kernel panic.

Using the GRUB menu I did a recovery and was able to reboot. Then I did apt-get update.

Things looked OK but I went to run my VM using VirtualBox and it will not start.

I have attached the combined vbox-install and make log outputs, but the meat of it is:

In file included from /tmp/vbox.0/r0drv/linux/the-linux-kernel.h:80,
                 from /tmp/vbox.0/r0drv/linux/memobj-r0drv-linux.c:35:
include/linux/mm.h:1174: error: stray ‘\177’ in program
include/linux/mm.h:1174: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cache_async_readahead’
make[2]: *** [/tmp/vbox.0/r0drv/linux/memobj-r0drv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxdrv] Error 2

There seems to be some corrupted kernel file text that is preventing restoration, and I am unsure what the minimum measures are to get this fixed.

---

### Post by dstew on 2009-07-31
One thing you could do is look at the file include/linux/mm.h, line 1174 and see what the fuss is about. It suggests there is a "stray \177" there. Maybe you can edit the line, and try again. The other errors are probably a result of the compilation error. Just a guess.

---

