---
title: "&quot;Clocksource tsc unstable&quot; after upgrade from 8.10 to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by hanzgroove on 2009-04-24
After upgrading from 8.10 to 9.04 (Server Edition), I get the following messages in my logs:

```

System Events
=-=-=-=-=-=-=
Apr 24 10:34:58 xxx kernel: Clocksource tsc unstable (delta = -234443907 ns)
Apr 24 10:38:15 xxx ntpd[3607]: kernel time sync status change 0001

```

Is there something I can do/run to fix this? I'd appreciate any help.

---

### Post by hanzgroove on 2009-04-24
I've been researching this a bit via google. Specifically this workaround : [http://patanachai.blogspot.com/2009/02/slow-boot-with-clocksource-message-in.html](http://patanachai.blogspot.com/2009/02/slow-boot-with-clocksource-message-in.html)

The odd thing is that if I check /boot/grub/menu.lst, all the references still point to 8.10? Is that supposed to change to 9.04?

```

title           Ubuntu 8.10, kernel 2.6.27.15-20090209a Default
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/md1 ro quiet splash
quiet

title           Ubuntu 8.10, kernel 2.6.27.15-20090209a Default (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/md1 ro single

title           Ubuntu 8.10, kernel 2.6.26.8-20081113a Previous
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/md1 ro quiet splash
quiet

title           Ubuntu 8.10, kernel 2.6.26.8-20081113a Previous (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/md1 ro single

title           Ubuntu 8.10, kernel 2.6.27.15-20090209a
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27.15-20090209a root=/dev/md1 ro quiet splash
quiet

title           Ubuntu 8.10, kernel 2.6.27.15-20090209a (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27.15-20090209a root=/dev/md1 ro single

title           Ubuntu 8.10, kernel 2.6.26.8-20081113a
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.26.8-20081113a root=/dev/md1 ro quiet splash
quiet

title           Ubuntu 8.10, kernel 2.6.26.8-20081113a (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.26.8-20081113a root=/dev/md1 ro single

title           Ubuntu 8.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```

---

