---
title: "What type of Hard Drive Do I need to Cross XP and Edgy"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by ZeusMoose15 on 2007-03-20
So here's the deal.  I've got a computer with the xp/edgy dual boot set up on the main drive.  I am looking to buy a new external hard drive (actually I had one, but it failed and I'm getting a data transfer to a new external HD, but don't worry about that part).  The external drive would not contain necessary operating files, only media and documents.  I  am looking to be able to boot either xp or edgy, and have write access to these files on the new hard drive.  I understand that not all hard drives work for all operating systems.  What type of drive do I need in order to have write access to files on an external hard drive that is not seperately partitioned for each operating systems.  So when I choose to boot an operating system from start up, I choose the operating system, but the files on the external hard drive will be write accessable on either OS.

Whew

---

### Post by flyingbrass on 2007-03-20
Any hard drive will work.  Your question is about which file system to use on it so you can have read/write access with both Linux and Windows.  You have several choices:
[list]
[*] Use FAT32.  It's compatible with both but isn't a very good file system.  It requires periodic defragmenting, and file size limit is 4 GB.

[*] Use ext3 (Ubuntu's default) and install [fs-driver](http://www.fs-driver.org/) in Windows.  Windows will mount it as ext2 (same as ext3 minus the journaling).

[*] Use NTFS and install ntfs-3g in Edgy.  ntfs-3g recently went "stable," so if you go this route be sure to install the newest version.
[/list]

---

### Post by GreenHawkIA on 2007-03-20
You can use FAT formatting - which is fully supported by both systems, or you can use NTFS - the Windows filesystem which can be supported by the installation of ntfs-3g.  While ntfs-3g is beta, it is very stable and easy to use.  Instructions are here:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g)

---

### Post by GreenHawkIA on 2007-03-20
FlyingBrass beat me to it, but he's right about the 3rd option, you can do that too.  I forgot, glad he was around

---

