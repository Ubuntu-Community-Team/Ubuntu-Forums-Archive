---
title: "Getting rid of Windows Vista and installing Ubuntu"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by ilangocal on 2009-03-04
Hi
Presently I have a Windows Vista Home Premium installation (with Service Pack1) and Ubuntu Feisty Fawn running on VMWARE on the same machine. I would like to get rid of Windows Vista altogether and install the latest Ubuntu on this machine. What is the best approach?
This is an Acer Aspire Machine with Intel Core Duo T2350 1.87 GHz, 2 GB RAM, 32-bit operating system.


thanks in advance
ilango

---

### Post by lykwydchykyn on 2009-03-04
First thing's first: download the CD and boot it up, and make sure all your hardware is functioning properly.  Pay close attention to networking and video performance, especially if you're using wireless ethernet.

If all that works, make sure all your important data is backed up and run the installer.  You might want to consider doing a dual-boot if you aren't 100% sold on going all-ubuntu.

Questions?

---

### Post by ilangocal on 2009-03-04
> **lykwydchykyn said:**
> First thing's first: download the CD and boot it up, and make sure all your hardware is functioning properly.  Pay close attention to networking and video performance, especially if you're using wireless ethernet.

If all that works, make sure all your important data is backed up and run the installer.  You might want to consider doing a dual-boot if you aren't 100% sold on going all-ubuntu.

Questions?

So I back up my data, erase Windows Vista, partition the drive (with Ubuntu utilities?) and then install Ubuntu in that partition?
Later I simply install Windows Vista in the other partition and do a dual boot?

---

### Post by 67GTA on 2009-03-04
If you want to do a dual boot, just shrink the Vista partition, then install Ubuntu in the free space. There is no need to erase Vista and then reinstall it. Vista will overwrite your master boot record, and won't let you boot into Ubuntu.

---

### Post by ilangocal on 2009-03-04
> **67GTA said:**
> If you want to do a dual boot, just shrink the Vista partition, then install Ubuntu in the free space. There is no need to erase Vista and then reinstall it. Vista will overwrite your master boot record, and won't let you boot into Ubuntu.

Ah, I see. So I will shrink Vista instead. Thanks again.

---

### Post by avtolle on 2009-03-04
Be sure to defrag the drive before shrinking, and use the Vista tool for shrinking the partition.

---

### Post by ilangocal on 2009-03-12
How do you recommend I uninstall VMWARE (Ubuntu runs on VMWARE) from my Windows Vista partition? Should I first uninstall Ubuntu running on VMWARE first?

I would like to shrink my Vista partition after uninstalling VMWARE and the Ubuntu running inside this machine
Thanks for all your previous replies.

---

