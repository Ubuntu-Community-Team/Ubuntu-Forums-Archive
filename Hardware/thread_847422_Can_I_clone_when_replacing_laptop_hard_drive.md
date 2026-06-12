---
title: "Can I clone when replacing laptop hard drive?"
date: 2008-07-02
forum: Hardware
---

### Post by mikeescott on 2008-07-02
I am replacing the 30gb ide hard drive in my laptop with a 250gb ide drive. Is there any way to clone the dual boot drive without loosing anything or having to reinstall everything? I am running 8.04 and XP SP3 on a Compaq Presario 1700T.

---

### Post by prshah on 2008-07-02
> **mikeescott said:**
> I am replacing the 30gb ide hard drive in my laptop with a 250gb ide drive. Is there any way to clone the dual boot drive without loosing anything or having to reinstall everything? I am running 8.04 and XP SP3 on a Compaq Presario 1700T.

You can use partimage to clone and restore your partitions, then use gparted to resize the partitions to use up the leftover space. You don't need to save/restore your swap partition, unless it's in an extended partition.

Note: mucking around with partitions, partimage and/or gparted is risky be sure to have a backup.

---

### Post by mikeescott on 2008-07-02
I want to make an exact copy of what is on the drive now, then create a new partition with the remaining 220GBs for media files. Will partimage copy the installation and settings of Ubuntu and XP without affection their performance (zero loss of data and files)?

---

### Post by prshah on 2008-07-03
> **mikeescott said:**
> I want to make an exact copy of what is on the drive now, then create a new partition with the remaining 220GBs for media files. Will partimage copy the installation and settings of Ubuntu and XP without affection their performance (zero loss of data and files)?

partimage will clone the entire _partition_ including the files and data. It will not affect performance and will not affect data/files in anyway.

---

