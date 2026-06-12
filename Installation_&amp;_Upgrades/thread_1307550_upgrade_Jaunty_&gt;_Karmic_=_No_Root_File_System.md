---
title: "upgrade Jaunty &gt; Karmic = No Root File System"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by maxol on 2009-10-31
I just upgraded 64 bit Ubuntu 9.04 to 9.10. The upgrade went smoothly with no problems.

When the system rebooted I was dropped back to BusyBox with the error message

"ALERT! /dev/disk/by-uuid/xxxxxxxxxxxxxxxxxblahxxxxxxx does not exist. Dropping to a shell!

So I tried booting the older 2.6.28-16 kernel I had been using with Jaunty only to get the same error.

I have tried a couple of grub boot arguments "rootdelay=90" and "acpi=off" but they make no difference.

I have two SATA hard disks run as RAID 1 on a MSI K9A Platinum motherboard. Partitioned like this

sda1 /windows
sda2 /root
sda3 /swap
sda4 /home

This all worked fine with Jaunty

Is anybody else having similar problems? Can anyone suggest a workaround?

Any help much appreciated.

---

### Post by aheckler on 2009-10-31
Try running this in your shell:
```
sudo /etc/init.d/udev restart
```

---

### Post by maxol on 2009-10-31
I get> /bin/sh: sudo: not foundI'm entering this in the BusyBox shell

---

### Post by maxol on 2009-10-31
I'm having a look at my disks with gparted on the Karmic live CD

It recognises the RAID setup as /dev/mapper/pdc_iaedgi but seems to be having trouble correctly recognising the partitions.

> /dev/mapper/pdc_iaedgi1 fat 32 ( this is correct )
/dev/mapper/pdc_iaedgi2 ext3 ( this is actually an ext4 partition )
/dev/mapper/pdc_iaedgi3 linux-swap ( this is correct )
/dev/mapper/pdc_iaedgi4 Unknown ( this is actually an ext4 partition )

If i get gparted to look at /dev/sda it shows what i would expect.

> /dev/sda1 fat32
/dev/sda2 ext4
/dev/sda3 linux-swap
/dev/sda4 ext4

But when gparted looks at /dev/sdb I see this.

> /dev/sdb1 fat32
/dev/sdb2 ext3
/dev/sdb3 linux-swap
/dev/sdb4 Unknown
unallocated unallocated

Anybody have any ideas?

---

### Post by maxol on 2009-10-31
OK I have managed to get it to boot by using the grub boot argument "nodmraid"

---

### Post by AMSlider on 2009-11-01
Hey Maxol,

I had the same issue on the Jaunty-Karmic upgrade.  My mobo has a RAID controller but I'm not using it and don't have RAID turned on at all...  The nodmraid solved it for me!  Many Thanks!

---

