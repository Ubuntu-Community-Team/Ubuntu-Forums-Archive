---
title: "Partitioning question"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by crova on 2009-10-30
Hi all!
I want to install Ubuntu on my laptop ( Acer Aspire 7720G ), dual-booting with another OS
I have 2 Hard Disks:
- the first is used by another OS ( yet installed, Win 7 )
- the second is used for files

This one ( the 2nd ) is yet partitioned in this way:
- 10GB System Recovery Image ( cannot be deleted )
- 70GB Data ( used for data storage..files documents and so on.. )  -  NTFS
- 20GB Projects ( used for my C++/C and so on, projects )  -  NTFS
- 50GB Unallocated 

Now my question is, there is a way to install Ubuntu in this 50GB unallocated space?
Thank you in advance for the answers : )

---

### Post by lindsay7 on 2009-10-30
Use the ubuntu live install disk and then use gparted found under system/administration.  You can set up a partition for the unallocated space and format it ext3 or ext4 then use the custom install feature to install ubuntu on that partition.

---

### Post by crova on 2009-10-30
I tried but gparted sees the disk like 1 big block of 150GB
I need to find only the 50 unallocated : (

---

### Post by theWrkncacnter on 2009-10-30
Did you try changing the device? Maybe it's looking at the first hard disk, which is one big windows 7 partition.

---

### Post by crova on 2009-10-30
Yes yes I checked both :/

---

