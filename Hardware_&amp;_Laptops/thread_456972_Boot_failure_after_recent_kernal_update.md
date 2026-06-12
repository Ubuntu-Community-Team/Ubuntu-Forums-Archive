---
title: "Boot failure after recent kernal update"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by cas118 on 2007-05-28
Hi there,

I've updated Feistry with the recent kernal, and now the system completely fails to boot.

I've had this problem coming I suppose, but here is the main issue:

On booting, I get the following error messages appear:

```

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules is /dev
ALERT! /dev/sdb1/ does not exist. Dropping to a shell!

...

/bin/sh: can't access tty; job control turned off

```

By default, any kernal upgrades have always put the incorrect dev path in the menu (/dev/sda1 or in Feisty the UUID equivalent). I had to manually change this and also in Feisty add IRQPOLL to the boot options to get Ubuntu to start correctly.

When booting with the new kernel, I also get some perculair error messages:

```

hde: cache flushes supported
hde:<3>irq 16:nobody cared (try booting with the "irqpoll" option")

...

Disabling IRQ #16
hde: dma_timer_expiry: dma status == 0x24
hde: DA interrupt recovery
hde: lost interrupt

```

It then repeats similar stuff for hdg, finally, I get the big error at the top. And then it starts again!

Any help would really, *really* be appreciated.

---

