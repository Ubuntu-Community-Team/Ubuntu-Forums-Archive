---
title: "Missing 23.5GB on new drive."
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by steelblue77 on 2007-08-01
I got a new Seagate 500GB IDE drive today.  I installed it, got the BIOS correct and Linux sees it.  I created one partition on it using the whole drive (ext3).  However, when I go to properties for the drive in my storage media folder it says 6% of it is already used.  What the hell is going on?

Why am I missing 23.5GB?  It is a fresh drive.  I only have kubuntu running on my 200GB master.  The 500GB is for storage so I need every GB I can get.  Any ideas?  It does have that pesky lost+found folder in it.  I think it maybe the ext3 journal that is eating up space.

Thanks.

---

### Post by D4mn on 2007-08-02
Hi! 
I know this is the case indeed. I always assumed this was the journal that EXT3 maintains, but trying to find the % of space used by the journal I found this: [http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips]("http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips"), look for the "Reclaim Reserved Filesystem Space" part.

I have an USB disk myself and decided to make this NTFS. NTFS-3G works well in Feisty and I am able to use the disc from both OS's.

Good luck!

Danny :KS

---

### Post by steelblue77 on 2007-08-02
Thanks for the info.  I'll try resizing the space in needs.

---

