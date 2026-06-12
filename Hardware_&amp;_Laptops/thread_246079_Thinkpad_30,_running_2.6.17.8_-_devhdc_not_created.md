---
title: "Thinkpad 30, running 2.6.17.8 - /dev/hdc not created??"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by kaens on 2006-08-28
Alright, so I'm running Dapper on a Thinkpad T30 with the 2.6.17.8 kernel.

For some reason, /dev/hdc is not created on boot...

dmesg | grep CD produces:
```
hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4240N, ATAPI CD/DVD-ROM drive
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache

```

So it is detected on boot. I have a feeling this might have to do with udev rules? I really have no idea. 

I tried booting with irqpoll, and pci=routeirq (the first suggestion I found in another forum, the second I found as a suggestion in dmesg if PCI devices didn't work), which did nothing.

Anyone with more knowledge about this than I, your help would be greatly appreciated. If you need any more info, just let me know.

---

