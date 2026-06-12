---
title: "Using USB external Hard Drives"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by visitek on 2007-05-01
I am trying to backup data from a laptop to an external hard drive using ubuntu.
When I try to copy files to the USB drive, ubuntu will not copy the file giving a message that the drive is read only.  When I boot into windows I can copy and read files however in ubuntu I can only read (not write to the drive).

Can anyone tell me some script to write to the USB drive (making the drive read and write)

Thanks

Ian

---

### Post by Gannin on 2007-05-01
What file system is the drive using?

---

### Post by richardjennings on 2007-05-01
yes it sounds like the drive has to be either NTFS or FAT32

I am guessing it is NTFS if it is big enough to be used for storage.

If it is NTFS synaptic ntfs-config. 
Once installed  Applications > System Tools > NTFS Configuration Tool

if that doesnt work check out the thread below. 

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+support](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+support)

---

### Post by Gannin on 2007-05-01
I'm also guessing it's NTFS.  If it was FAT32, it should mount just fine.

---

