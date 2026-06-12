---
title: "Hard Disk does not spin down"
date: 2009-11-12
forum: Hardware
---

### Post by RichardCL on 2009-11-12
Dear Forum,

Ubuntu Karmic doesn't seem to be spinning-down SATA hard disks that are not being accessed for a long period (including non-mounted).

Shouldn't the operating system spin-down and hibernate the drive to save power and wear&tear on the hardware?

By the way, I'd like to change my server to a small solid state or internal USB for the OS and spin-down the drive to save power/noise/wear. I had that setup on my NAS system up to now.


Richard



#Follows the wordy intro about which system and exactly what I did.


I'm running Karmic on Intel core4quad and NVIDA motherboard. The board has 4 SATA slots. When I installed Karmic I had a HDD and DVD, which where correctly recognised and used for the install.

Last week I attached a second HDD from an old RAID NAS. The drive was formerly one of a mirrored pair. The HDD had data I needed and was already partitioned.
/dev/sdb1=boot
/dev/sdb2=Linux RAID
/dev/sdb3=swap

I mounted the drive from terminal with
```
sudo mount -t ext2 /dev/sdb2 /home/me/mydata
CHOWN me /home/me/mydata
```

Then I copied my data to the hard disk and fine. On reboot mydata was not linked and showed empty. The disk manager showed not mounted.

So I used the machine for a few hours and then opened the case to remove the drive again. The drive was hot as hell so I guess it had been running. I'd expected that the drive had been power-saving and shut-down since it wasn't mounted.

---

