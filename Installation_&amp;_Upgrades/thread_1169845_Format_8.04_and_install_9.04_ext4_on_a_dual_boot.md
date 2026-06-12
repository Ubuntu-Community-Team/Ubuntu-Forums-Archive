---
title: "Format 8.04 and install 9.04 ext4 on a dual boot"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by lovethepirk on 2009-05-25
I run Ubuntu 8.10 and it is dual booted with XP pro.

I would like to format 8.10 and install Ubuntu 9.04 using Ext 4 format.

What steps should I take to 
1) Format my ubuntu 8.10 
2) Install 9.04 using Ext 4

I have formatted linux before on a duel boot and I couldn't boot up until I fixed the mbr somehow.


Thanks for help

---

### Post by merlinus on 2009-05-25
You can install 9.04 into the partition that contains 8.04.  The install partitioner will allow you to do this, and offer a choice of ext4.  Choose the manual method.

Make sure, however, that you back up your data, and do not format the XP partition.

---

### Post by presence1960 on 2009-05-25
use the manual option at the partitioner as mentioned by merlinus. when you get to the attached screen click the Advanced button and install GRUB to the MBR by selecting your hard disk (such as sda or sdb as appropriate for your machine). This will avoid your GRUB MBR problems you mentioned. Choosing the other options  (sda1, sda2, sdb1, sdb2, etc) will install GRUB to that particular disk & partition.

---

