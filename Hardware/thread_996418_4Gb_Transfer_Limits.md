---
title: "4Gb Transfer Limits"
date: 2008-11-28
forum: Hardware
---

### Post by vancedus on 2008-11-28
Hi,

I've been using Ubuntu for only about 6 months now and I recently wanted to start a backup system.  I decided to use Simple Backup Suite and I would back it up to a Western Digital External hard drive. I found that it stopped transferring data after 4Gb.  I read this was due to the type of file system but I don't know how to change that,  Please help me out.  Thank you.

---

### Post by taurus on 2008-11-28
Is your WD external drive a fat32/vfat filesystem?

---

### Post by vancedus on 2008-11-29
Yes, the hard drive a fat32/vfat file system.  Thanks for the help.

---

### Post by taurus on 2008-11-29
If you have a file larger than 4GB, fat32/vfat is not going to work because that filesystem will not allow you to write to it if a file is larger than 4GB.  So, either format it to ntfs or ext3.

---

### Post by vancedus on 2008-11-29
How do I change the format to either ntfs or ext3?

---

### Post by taurus on 2008-11-29
Is there any data on that drive?  You have to reformat the drive so everything on it will be gone.  

You can use gparted in System -> Administration (install it if you don't have it) to reformat it to either ntfs or ext3.  Is Ubuntu the only OS that external harddrive connected to?

---

### Post by vancedus on 2008-11-29
Yes the drive is empty and I may, at some point, use it in Windows.  Thanks you for the imformation.

---

