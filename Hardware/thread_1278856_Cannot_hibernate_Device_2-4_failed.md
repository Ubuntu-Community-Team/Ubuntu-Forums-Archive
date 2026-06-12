---
title: "Cannot hibernate Device 2-4 failed"
date: 2009-09-30
forum: Hardware
---

### Post by map7 on 2009-09-30
I'm running Ubuntu 904 64bit on a Lenovo T400s notebook and I've setup a swap partition as a primary partition which is 2.5 times the size of my memory in the machine.  The machine seems mostly intel based, ie: graphics cards, wifi, chipset (ICH9), are all intel.

When I try and hibernate I get the following error:
```
ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
ata1: irq_stat 0x00400040, connection status changed
ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
ata2: irq_stat 0x40000001
pm_op(): usb_dev_poweroff+0x0/0x10 returns -32
PM: Device 2-4 failed to hibernate: error -32
```

I'm on kernel 2.6.28-15.

I don't have a /etc/initramfs-tools/conf.d/resume file should I?

I've checked my blkid readout and it's correct and includes my swap partition

Suspend works.

---

