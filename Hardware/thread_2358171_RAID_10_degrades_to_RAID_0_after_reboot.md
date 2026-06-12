---
title: "RAID 10 degrades to RAID 0 after reboot?"
date: 2017-04-10
forum: Hardware
---

### Post by vitamin-pizza on 2017-04-10
Hi guys, I'm running Ubuntu 16.04, and I'm having a problem with a new RAID 10 array. The array consists of four 5 TB drives, all the same exact model. Two of the drives were used by me previously, and two are new. I made sure that they synced cleanly and wiped out old data and partitions. The array forms properly afterwards, with a capacity of 9.1 TB. However, after I reboot, the array degrades to a RAID 0 with a capacity of 13 TB. I've verified that I've got the correct UUID in /etc/mdadm/mdadm.conf, but the array always boots up one disk short. It's always the same device as well: /dev/sdd1 I'm able to force the array to start with this command: sudo mdadm --create /dev/md0 -v --assume-clean --level=raid10 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 The array acts normally and can be mounted after I make a filesystem with fdisk. It just degrades to RAID 0 again after I reboot. What am I doing wrong here? It seems like one disk is failing to be found at boot, and thus is missing from the array. Do the disks require something which I'm missing for this one disk? Should each disk in the array be specified in my fstab file, or should they be excluded from it? Any insight would be greatly appreciated.

---

