---
title: "format disk in fat32"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by kostaben on 2009-06-08
Hi all,

I have a dual boot disk, one partition with Ubuntu and another one with Fedora. I´m gonna sell this computer so i want to install windows. In order for windows installation disk to work the disk has to be in Fat32 format. How can i format the whole disk in fat32 from Ubuntu.
The disk is the only one the computer has.

Thank you in advanced.

---

### Post by ianmillington on 2009-06-08
I think during the install Windows will just assume the disk not to have been formatted and will format the whole thing into either a FAT 32 or ntfs partition.

---

### Post by kostaben on 2009-06-08
ouf, thats my problem, that windows cannot go on with the installation cause the disk is ext3.

---

### Post by _Purple_ on 2009-06-08
Have you tried using Ubuntu Live CD and using gparted to format the harddisk in FAT32?

---

### Post by boof1988 on 2009-06-08
> **kostaben said:**
> ouf, thats my problem, that windows cannot go on with the installation cause the disk is ext3.

Once you have booted the Windows Install CD...

Are there any options (such as f-keys)?  Is there a delete partition (or all partitions) option?

---

### Post by kostaben on 2009-06-08
No i haven´t. Is Gparted able to format in fat32 or ntfs? I´ll try anyways. Thank you for your help.

---

### Post by kostaben on 2009-06-08
No boof1988 has no options at all. In the begining says "the installation programm is checking your hardware configuration"  (more ore less cause the message is in spanish) and freezes there.

---

### Post by _Purple_ on 2009-06-08
> **kostaben said:**
> No i haven´t. Is Gparted able to format in fat32 or ntfs? I´ll try anyways. Thank you for your help.

Yes, you can format as fat32 or ntfs using gparted.

---

### Post by boof1988 on 2009-06-08
> **_Purple_ said:**
> Yes, you can format as fat32 or ntfs using gparted.

Another option might be...

Delete the partition (using *gparted LiveCD* or other) and then let the Windows Installer format a new partition when it installs the Windows operating system.

---

### Post by kostaben on 2009-06-08
Gparted refused to format the disk in Fat32 or Ntfs but i delete all partitions and finally windows got installed.

Thank you guys for helping.

---

