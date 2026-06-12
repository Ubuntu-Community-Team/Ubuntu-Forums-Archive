---
title: "Uninstalling/re-installing help"
date: 2008-08-31
forum: General Help
---

### Post by Miyavix3 on 2008-08-31
First I want to give some background info:
When I installed Ubuntu on my PC I did an manual install. So I allocated space for everything. I gave ubuntu 100GB and left my Windows with 400GB (500total). Whenever I boot to Windows it says my HDD is only 400GB, when I know it's not. Is that normal? 

Anywho, I want to uninstall Ubuntu from that partition to re-install it with Windows. If you boot into Windows and pop the Live CD in, it'll give you the option to install it along-side windows.
That seems easier IMO. Is it? And how would I go about uninstalling Ubuntu in the first place, and getting my 100GB back?

---

### Post by WRDN on 2008-08-31
Regarding the first question, Windows is displaying the size of a partition, not the entire drive, so the figure is correct. On a typical installation, Windows cannot recognise the filesystems Linux is installed on by default (ext3), so you cannot access those partitions. In order to do so, install FS-Driver. 

As for the second question, you can remove Ubuntu by booting from the LiveCD, opening GParted (System > Administration > GParted) and deleting the partition Ubuntu is installed on. Now, resize Windows' partition and give it the unallocated space.

---

### Post by Miyavix3 on 2008-08-31
> **WRDN said:**
> Regarding the first question, Windows is displaying the size of a partition, not the entire drive, so the figure is correct. On a typical installation, Windows cannot recognise the filesystems Linux is installed on by default (ext3), so you cannot access those partitions. In order to do so, install FS-Driver. 

As for the second question, you can remove Ubuntu by booting from the LiveCD, opening GParted (System > Administration > GParted) and deleting the partition Ubuntu is installed on. Now, resize Windows' partition and give it the unallocated space.

And installing it alongside windows is fine? Will it pose any problems?

edit: Problem fixed

---

### Post by falcon61102 on 2008-08-31
When you say you wish to install alongside windows, do you mean as a dual-boot setup like you have now or using wubi?

---

### Post by Miyavix3 on 2008-09-01
> **falcon61102 said:**
> When you say you wish to install alongside windows, do you mean as a dual-boot setup like you have now or using wubi?

When you put the Live CD into a windows session, it's the second option.

---

