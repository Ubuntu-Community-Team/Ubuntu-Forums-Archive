---
title: "drive disappeared from xp after dapper install"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by gontofe on 2006-10-10
Hello all,

A friend has installed Dapper on his PC (after my advice, oops). His system had 3 partitions on the hd, one with windows, one with documents, and the other blank (for ubuntu). After installing ubuntu, windows no longer recognises the documents drive, which is however accessible in Dapper. I checked the permissions, and changed the drive permissions to 777 to no avail - the drive still remains invisible!

In Disk Management in XP the partion is shown as Healthy (Unknown Partition). What can I do?

---

### Post by Mr Frosti on 2006-10-10
Windows will only recognize the partition if it is FAT* or NTFS. If the Ubuntu installation CD changed the file system on this partition, it will not be able to be read by Windows XP.

This sounds like the order of the partitions might be confusing Windows XP as well. Changing the file permissions inside of Ubuntu will not remedy the Windows mounting issue.

---

### Post by gontofe on 2006-10-10
its a fat drive, i checked that, its listed as in fstab as vfat - remember that this was a partition created in windows, ubuntu has changed nothing on this drive.

not sure how the order would have affected anything - ubuntu was installed on the last partition, the others shouldnt have been 
touched.

---

### Post by gontofe on 2006-10-12
Apparently it's all sorted:

He went here, and downloaded the program:

[http://super-fdisk.ptdd-group.qarchive.org/](http://super-fdisk.ptdd-group.qarchive.org/)

On startup, the partition was automatically detected and repaired...

Not sure how Ubuntu will deal with losing its swap partition!

---

### Post by Mr Frosti on 2006-10-16
It deals with it in an interesting way. Once your memory is filled up, and more is needed it will kill the highest memory-consuming process. For me, this was typically VMWare, and it took me a while to figure out what was going on. You might prefer this, as it keeps the system "lean".

---

### Post by gontofe on 2006-10-17
would it maybe be better to create a new swap? How?

---

