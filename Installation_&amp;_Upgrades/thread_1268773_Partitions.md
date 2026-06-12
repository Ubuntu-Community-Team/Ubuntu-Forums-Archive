---
title: "Partitions"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2009-09-17
I have a dualboot of Windows 7 and Ubuntu. When I work in Ubuntu I can see all my documents, including the ones from Windows. When I am in Windows I can only see the documents of Windows. 
Is there an easy way to change this now without changing partitions or is it easier to install my Data next time on a second Primary partition, like this? 

PP1 Windows NTFS
PP2 Data Ext3
EP Linux
(Now I have: PP1, windows NTFS; EP Linux with Data) 

I would like to know this because a friend of my is partitioning a new harddisk and he would like to be able to see his files also when booting from Windows.

---

### Post by Yvan300 on 2009-09-17
all you have to do is install the driver in windows that allows you to read from ext3. I'm not sure if it is available for windows 7 but i guess in your situation, you should put your home partition on a seperate partition and format it to fat32.

---

### Post by pyroclastic on 2009-09-17
> **Ampi said:**
> I have a dualboot of Windows 7 and Ubuntu. When I work in Ubuntu I can see all my documents, including the ones from Windows. When I am in Windows I can only see the documents of Windows. 
Is there an easy way to change this now without changing partitions or is it easier to install my Data next time on a second Primary partition, like this? 

PP1 Windows NTFS
PP2 Data Ext3
EP Linux
(Now I have: PP1, windows NTFS; EP Linux with Data) 

I would like to know this because a friend of my is partitioning a new harddisk and he would like to be able to see his files also when booting from Windows.


try this     [link]("http://www.diskinternals.com/linux-reader/") i think this is what u need.

---

### Post by Ampi on 2009-09-19
So that software doesn't let you edit any files? Is it just read-only?
That would be good for me, because I already have the harddisk partitioned. But for the new harddisk it is better to format to fat32, right?

---

### Post by Bartender on 2009-09-19
Just my opinion, but I think people are moving away from FAT32 when creating a partition that both OS'es can access.  FAT32 wastes a lot of space, it's not very efficient, etc.  I've got a big external HDD for storage.  It's formatted NTFS.  Ubuntu has not had any problems reading or writing to it.

---

