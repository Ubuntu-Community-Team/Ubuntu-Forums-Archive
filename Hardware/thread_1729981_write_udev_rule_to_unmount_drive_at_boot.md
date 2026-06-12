---
title: "write udev rule to unmount drive at boot"
date: 2011-04-15
forum: Hardware
---

### Post by Z.K. on 2011-04-15
I have a Windows Ready Boost drive attached to my dual boot system and I really would rather it was not mounted when I boot into Ubuntu.  I tried writing a udev rule that unmounted it, but for some reason it did not work.  I was wondering if someone more knowledgeable on writing udev rules could tell me what I am doing wrong.

udev rule:
```

SUBSYSTEM=="block", KERNELS=="2-5", SUBSYSTEMS=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="5d07", ATTRS{manufacturer}=="HP",ATTRS{product}=="c310w",ATTRS{serial}=="3S0708440038", RUN+="/home/roger/scripts/umount-ReadyBoost.sh" , OPTIONS+="last_rule"

``` 

script:
```

#! /bin/sh
umount /dev/sdd1

```

:?

---

### Post by ajgreeny on 2011-04-15
Try putting the command ```
umount /dev/sdd1
``` in /etc/rc.local. just above the bottom **exit 0** line.  I don't know if it will work, but it is worth a try.

---

### Post by sisco311 on 2011-04-15
I think that if you create an fstab entry for the partition, then it won't be auto-mounted, /etc/fstab:
```
UUID=**UUID-of-sdd1**    /media/sdd1    auto    noauto
```

---

### Post by ajgreeny on 2011-04-15
> **sisco311 said:**
> I think that if you create an fstab entry for the partition, then it won't be auto-mounted, /etc/fstab:
```
UUID=**UUID-of-sdd1**    /media/sdd1    auto    noauto
```
I forgot that;  I think sisco311 has the answer.

---

