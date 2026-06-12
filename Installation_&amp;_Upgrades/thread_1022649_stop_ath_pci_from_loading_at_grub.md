---
title: "stop ath_pci from loading at grub"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by rakannan on 2008-12-27
Hi,

I got hold of an alternate CD and installed Ubuntu 8.10 onto my laptop (Compaq CQ50-106AU). I had to use the alternate CD because of the problem with ath_pci and ath_hal modules dumping core. With the alternate CD the installation was fine. However, after reboot, the same problem with ath_pci and ath_hal persists. Is there a way I can remove these two modules from the kernel load?

Here are the things that I have tried.
1. brokenmodules=ath_pci,ath_hal doesnt work
2. If I turn off pci=off, then it gets me into the initramsh which I have no idea how to utilize.

There are many options to people who are able to boot their way into the box. But when you only have grub shell, there isnt much that you can do. Or is there?


By the way, I do have Windows XP running and it is ok.

Thanks...

---

### Post by lemming465 on 2008-12-28
One version of this goal is to add the offending modules to /etc/modprobe.d/blacklist.  There may be other ways, but that's the one I'm familiar with.  The problem is to get command line access to /etc without having the modules loaded.  The easiest way to do that is probably to follow the directions in [section 8.2]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html#gainrootinstallcd") to boot with "rw init=/bin/bash" instead of "ro" by editing your grub kernel line arguments before booting.

Assuming that gets you a working shell prompt with your root filesystem mounted read-write, then you can do:```
cd /etc/modules.d
echo -e "blacklist ath_pci\nblacklist ath_hal" >> blacklist
```

---

