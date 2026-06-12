---
title: "HDD Problems at startup. ThinkPad Edge"
date: 2011-03-14
forum: Hardware
---

### Post by Hammserg on 2011-03-14
Hi!
I'm novice in Ububtu. And already have problems.. I've installed 10.10 on my laptop alongside Windows 7. When I was installing it, i've deleted some partition /dev/sda3 which size was 0MB. 
Now Ubuntu runs correctly. Even GRUB supports Windows 7 startup, which leads to blue screen.
Windows installer didn't see any partition because of HDD driver failure. I've install it manually "Intel(R) SATA controller AHCI driver", but there is no effect.. 
Also: Ubuntu didn't see Windows (E:) partition, it is marked as not allocated space.. 
Is it possible to repair Windows startup from Ubuntu?

df -h:
/dev/sda5              65G  2,5G   59G   5% /
none                  1,9G  288K  1,9G   1% /dev
none                  1,9G  1,3M  1,9G   1% /dev/shm
none                  1,9G   88K  1,9G   1% /var/run
none                  1,9G     0  1,9G   0% /var/lock
/dev/sda4             107G   19G   88G  18% /media/System
/dev/sda2            1000M  325M  676M  33% /media/SYSTEM_DRV

Config: Lenovo ThinkPad Edge 14, ATA Fujitsu MJA2500BH G2

Thank you for advices!

---

