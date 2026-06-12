---
title: "Question regarding dual booting with Windows Xp Pro and Ubuntu and the filesystems!"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2009-05-03
Hi.
I just have a question regarding dual booting with Windows Xp Pro and Ubuntu. I know that Windows Xp Pro needs to be installed first and then Ubuntu installed after it creates a partition. During the Ubuntu install, is the new partition; whether it be ext3 or ext4 exactly the same as if the Ubuntu OS was installed on a full HDD to its own?
Sorry if the question is a bit long.

---

### Post by Mark Phelps on 2009-05-03
Don't know how "exact" you want in an answer, but if you choose the same partitioning scheme, the Ubuntu you end up with in its own partition(s) is the same Ubuntu you would end up with on its own separate drive.

A very minor difference is the flexibility in MBR installation.  With only one drive, you have only one MBR. So, if you choose to install GRUB in the MBR, instead of the first Ubuntu partition, you will overwrite the MBR written by XP.  With two drives, you can install GRUB to the MBR of the Ubuntu drive and not touch the MBR of the XP drive.

But again, with respect to Ubuntu, the results are the same.

---

