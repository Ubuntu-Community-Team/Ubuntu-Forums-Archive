---
title: "Hosed partitions installing fedora"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by walter_j on 2009-08-19
I tried to install fedora 11 on my pc running ubuntu 9.04, and selected wrong installation procedure. The installation tried to install using the whole disk instead of updating fedora 11. The install quit with an error immediately after starting the partition process. Fedora and ubuntu live cd don't see any valid partitions now, although my main data partition may be still there - but is marked as unallocated when view using the partition manager with ubuntu live cd. I don't care about the os partitions, but i'm hoping the data partition is still recoverable. Is the data partition recoverable, or am i out of luck?


Walter

---

### Post by zvacet on 2009-08-19
If it is marked as unallocated I´m afraid that means you delete it.Maybe somebody else knows if it is possible to recover data and how.

---

### Post by louieb on 2009-08-19
Your best open source solution is **testdisk and photorec.** Testdisk finds and can restore delete partitions. photorec finds deleted files. testdisk is the Ubuntu repositories.  [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk") 

When Ive used it I run it from a  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") or a [SystemRescueCd]("http://www.sysresccd.org/Main_Page")
If nothing has been written to the disk then there is a great chance testdisk will give you a 100% recovery.

For example I had a drive with Crunchbag Linux install (3 partitions: / (root), /home and swap). Decided to format the the drive to one NTFS partition. Later decided did not need the partition for data. Used testdisk just to see if it could really rescue  the original partiton structure. It did. 
Had to restore GRUB to the MBR and the drive boots to Linux just like it did before.

---

