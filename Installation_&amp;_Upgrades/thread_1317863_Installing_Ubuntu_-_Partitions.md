---
title: "Installing Ubuntu - Partitions"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Parkito on 2009-11-07
Hello

I'm new at trying to installing Ubuntu.

I have 2 hard drives: 

(1) 250GB with Windows 7 on it.
(2) 160GB partitioned into 3 NTFS drives. 1 of 3 partitions is a 30 GB partition which i want to use for the Ubuntu installation.

So I boot from the Install CD until i get to the partitions screen. I choose Guided Partitioning and then manual. The problem is that i don't see my 3 different partitions on my 160 GB drive - it shows me the whole drive. 

How do i select only the 30 GB partition created on the 160 GB? :mad:

Thanks

---

### Post by Rambar on 2009-11-07
Greetings. Boot from the LiveCD and execute Gparted. Delete the partition you want to use to install Karmic and then proceed to installation. When asked, select your second drive and the option "Use the biggest free space avaible". It should automaticly select your 30gb slot.

---

