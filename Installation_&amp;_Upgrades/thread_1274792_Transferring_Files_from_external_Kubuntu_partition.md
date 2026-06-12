---
title: "Transferring Files from external Kubuntu partition to Windows Xp"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by earendill on 2009-09-24
Hi, 
New to this forum.

My computer which had a Kubuntu Feisty Fawn on it crashed. Along with Kubuntu 7.1 it also had a partition of Windows XP and a partition of Fedora Core 3(generally used as a dumping partition and maybe for sentimental reasons  :cry:). 

However, the problem is that my motherboard short circuited. As a result, I have to get a new motherboard (along with a new processor). Unfortunately, this means that I have to reinstall everything.  But my fedora core 3 partition has some important valuable data(close to about 10GB)

I have another computer with Windows XP installed in it. It is working fine. This windows has two NTFS partitions and one FAT32 partition. Can anybody suggest a method to transfer the files from Fedora Core 3 partition to Windows XP? Does the open source community have any tools for this purpose? Can you suggest how I transfer the data from the ext3 partition to an NTFS/FAT32 partitions?  :-k

The hard disk of the crashed PC can be connected as a slave to the hard disk of my working PC. Both Hard disks are IDE devices(not SATA). Is there any way for the windows to recognize the Fedora 3 partition.

Can this work?
In my working PC, I install Ubuntu. Will it recognize the external Fedora 3 and Kubuntu 7.1 partitions? 

Thanking You
earendil

---

### Post by mikewhatever on 2009-09-25
Just connect the disk and boot and use a live cd to copy files. Alternatively, install fs-driver to make Windows read ext3.

---

