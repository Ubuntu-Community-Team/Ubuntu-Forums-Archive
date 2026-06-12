---
title: "SATA hard drives disappear from running system"
date: 2008-09-22
forum: Hardware
---

### Post by z3ro-kam on 2008-09-22
I have two SATA drives in my computer when the computer starts up they show up in the BIOS they also show up with fdisk -l I mount one to /mnt/video the other to /mnt/mythtv I can access the data on them. then after a short time any where from 10 min to a few hours I can still see the data on the drives but they dont show up when I do fdisk -l and I cant write any data to the drives I check dmesg and I get I/O errors on sdc1 but sdc1 no longer shows up on the computer. The drives dont come back if I reboot but if I turn it off for a few min the drives show back up the drives are Seagate Barracuda 7200.8 250 Gbytes. I also started the computer up with a live cd ran smartctl test and the drives pass I am currently testing them for bad blocks.

---

