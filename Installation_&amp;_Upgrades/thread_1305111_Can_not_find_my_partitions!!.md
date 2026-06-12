---
title: "Can not find my partitions!!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by bhishan on 2009-10-29
I have a 160 GB hard drive. I have four partitions: 2 NTFS, 1 ext4 and 1 swap. I am trying to install Karmic. When I go to the advanced partition manager mode during installation, i can only see the 160 GB single partition, which ubuntu says is unallocated. It also says no other operating system detected. But I have Jaunty in the ext4 and vista in one of the NTFS drives.Even Gparted shows just one 160 GB unallocated drive. What is the problem. Please help. BTW, when I checked the disk before installation it said 1 file may have error. Anyone with similar problem? I am trying to install 64 bit version.

---

### Post by collinp on 2009-10-29
I don't know about it not detecting Jaunty, but the NTFS partitions are not going to show up as the method for reading & writing to them is not a part of the default Ubuntu install (you have to install a special package to read/write to them).

---

### Post by mikewhatever on 2009-10-29
I can both read and write to ntfs from Ubuntu live cds, and the installer should definitely detect ntfs partitions.

---

### Post by bhishan on 2009-10-29
> **Hellow said:**
> I don't know about it not detecting Jaunty, but the NTFS partitions are not going to show up as the method for reading & writing to them is not a part of the default Ubuntu install (you have to install a special package to read/write to them).

So what should I do to install Karmic without deleting Vista?

---

### Post by bhishan on 2009-10-30
I can not see my partitions from within Jaunty using Partition Editor too.

---

### Post by dhavalbbhatt on 2009-10-30
What CD are you using to install? It seems that people are getting around similar issues using the alternate CD as against the Desktop CD.

---

### Post by bhishan on 2009-10-30
> **dhavalbbhatt said:**
> What CD are you using to install? It seems that people are getting around similar issues using the alternate CD as against the Desktop CD.

No, I was using the regular one. I went to Vista, installed a partition manager and deleted the linux partitions. And then I rebooted using ubuntu cd and it worked. I have no idea what the initial problem. I am posting this from Karmic and I m loving it!!!

---

