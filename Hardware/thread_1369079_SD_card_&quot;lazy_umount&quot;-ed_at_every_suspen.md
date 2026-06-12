---
title: "SD card &quot;lazy umount&quot;-ed at every suspend, cannot mount again without restart"
date: 2009-12-31
forum: Hardware
---

### Post by sarthorks on 2009-12-31
Hello

When I mount my SD card, and then suspend my system, when i finally resume it, the SD card has been umounted by my system, automatically. And I cannot mount it again unless i restart, at least  thats my current understanding.

When I suspend my system, this is my /var/log/syslog:
```

Dec 31 22:14:15 sarthorks kernel: [   32.998627]  mmcblk0: p1
Dec 31 22:14:56 sarthorks hald: mounted /dev/mmcblk0p1 on behalf of uid 1000
Dec 31 22:18:20 sarthorks kernel: [  135.508840] mmc0: card 8fe4 removed
Dec 31 22:18:20 sarthorks hald[5300]: forcibly attempting to lazy unmount /dev/mmcblk0p1 as enclosing drive was disconnected
Dec 31 22:18:20 sarthorks hald: unmounted /dev/mmcblk0p1 from '/media/disk-1' on behalf of uid 0
Dec 31 22:18:20 sarthorks NetworkManager: <debug> [1262278100.383535] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_card_rca36836'). 

```
Here I suspended my system at 22:18.
How can I stop this automatic umounting? Help will be appreciated.

---

### Post by sarthorks on 2010-01-03
bump.

---

### Post by sarthorks on 2010-02-02
c'mon guys. cant anyone suggest anything?

---

