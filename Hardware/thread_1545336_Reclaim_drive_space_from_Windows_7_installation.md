---
title: "Reclaim drive space from Windows 7 installation"
date: 2010-08-03
forum: Hardware
---

### Post by astembridge on 2010-08-03
Hi all, 

I have a dual boot system with half the drive set aside for Ubuntu and the other half Windows 7.   I never use Windows, and could use the extra storage space. 

How can I reclaim this disk space without wrecking my existing Ubuntu installation?   Or can I?

---

### Post by astembridge on 2010-08-03
Figured this out on my own.
 
Removed the entry from grub for Windows.

Then opened gparted, 
deleted the Windows NTFS partition,
created new ext3 partition, 
applied in gparted, exited gparted.

Then vi'ed /etc/fstab and added
/dev/sda2 /mymountpoint defaults 0 1
Saved, and executed sudo mount -a

presto - I have new drive space.

---

