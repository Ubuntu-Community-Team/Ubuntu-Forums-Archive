---
title: "Problem multi-booting with an external hdd (Windows XP, Ubuntu 9.04, Fedora 11)"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by mhofer on 2009-08-31
Hello everyone.  I'm sorry if this has been answered already, I've done some looking around and I've seen some similar questions but I'm not quite linux-savvy enough to adapt the solutions and fix my own problem.

So here is the situation:  I have a Dell Notebook (XPS M1710) with Windows XP installed on the hard drive, and I recently bought an external hard drive (Iomega Prestige 1.0TB USB).  The hard drives are partitioned as follows:

Internal:
/dev/sda1 - 50MB FAT16 Primary Partition. 'DellUtility'
/dev/sda2 - 70GB NTFS Primary Partition with Windows XP installed.  (Flagged as the 'boot' partition in gparted)
/dev/sda3 - 3GB FAT32 Primary Partition. 'DellRestore'
*I have not touched the partitions on this drive

External:
/dev/sdb1 - 25GB NTFS Primary Partition, empty (I am contemplating a Vista or Windows 7 install).
/dev/sdb2 - 25GB Ext3 Primary Partition with Ubuntu 9.04 installed.
/dev/sdb3 - 25GB Ext4 Primary Partition with Fedora 11 installed.
/dev/sdb4 - [Remainder of disk is an Extended Partiton]
/dev/sdb5 - 5GB linux-swap Partition.
/dev/sdb6 - 100GB NTFS Partition. 'Programs'
/dev/sdb7 - 600GB NTFS Partition. 'Data Files'
/dev/sdb8 - 100GB FAT32 Partition. 'Back-Up'
/dev/sdb9 - 70GB NTFS Partition. 'Downloads/Drivers'
*I partitioned this hard drive myself using the gparted 0.4.6-1 bootable CD.

**This is what I would like to be able to do: **
1) Boot Windows XP normally when my external hdd is not attached (or atleast have my boot loader bring me to a menu and let me choose XP), because this is a notebook computer and I will not always have the external hdd with me.  
2) Choose between booting Windows XP, Ubuntu 9.04, and Fedora 11 when my external hdd is attached.

**And this is my problem:**
I installed Ubuntu 9.04 on the /dev/sdb2 partition using the Live CD.  I chose the mount point '/'.  At this point I could boot Ubuntu with no problems.  I then installed Fedora 11 on the /dev/sdb3 partition using Fedora's Live CD.  Unfortunately I get an error message stating that "Bootable partitions cannot be on an ext4 filesystem," so at this point I changed the mount point for the Ubuntu partition to '/boot' and the mount point for the Fedora partition to '/' and I was able to proceed with the installation.  At this point I could only boot Fedora.  If I chose Ubuntu from Grub's boot list (which, unfortunately did not include Windows XP as an option), I would instead boot into Windows XP.  So, naturally I thought I could trick my system (great idea, right?) and I decided to run the Ubuntu install again and reset the mount point to '/'.  I then installed WinGrub .0206 because I figured this would recognize my Windows OS since Fedora's version of Grub did not.  Now when I boot up I can choose to boot either Ubuntu 9.04 or Windows XP, but Fedora does not show up.  Furthermore, if my external hdd is not present when I boot, I get a Grub error (error 17, I believe) and I am unable to boot Windows at all.

Phew, I'm sorry to be so long-winded, but I figure it's better to give too much information than too little.  I guess my big questions are, how should I mount my linux partitions so that I am able to boot either one (Ubuntu or Fedora), and how can I fix the problem of Grub requiring my external hdd be present for me to boot correctly?

Thanks so much for any wisdom you can impart!

---

