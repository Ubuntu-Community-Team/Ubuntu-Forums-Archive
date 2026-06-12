---
title: "Partition creation disturbing recovery partition access"
date: 2014-03-06
forum: Hardware
---

### Post by yayou on 2014-03-06
Hi there,

I've realised that once we create a partition on a newly installed computer, the shortcut for accessing the recovery partition stops working. I can still access to mine because I've installed kubuntu and grub see this partition. So when I wanted to reinstall my laptop, I've just chosen it from the grub menu, but that is embarrasing when we need to do a factory restore on a windows computer in which we've previously created new partitions. So how could we create new partition(s) on a disk without losing the recovery partition access shortcut? 

thanx for having read.

---

### Post by Mark Phelps on 2014-03-06
> So how could we create new partition(s) on a disk without losing the recovery partition access shortcut? 

Sorry, but that might simply NOT be possible.  If the laptop recovery app expects the partition to be a certain number on the drive, at a certain offset on the drive, and a certain size on the drive, then you are stuck.

A better solution for restoring a PC, in my experience, is to make an full image backup to an external drive (using a Windows tool like Macrium Reflect), and creating the Linux Boot CD that is needed for loading a restore.  That way, you can return the disk to what it was when you made the backup and you don't need to keep the Recovery partition around.

---

### Post by yayou on 2014-03-10
Ok, thanx Mark Phelps. I thought that the problem occurs only when we create primary partition and could be solved by creating logical ones. I wanted to be sure of that. But if there's no way, do I need a precise Linux live cd ? Could you advice me one ?

---

