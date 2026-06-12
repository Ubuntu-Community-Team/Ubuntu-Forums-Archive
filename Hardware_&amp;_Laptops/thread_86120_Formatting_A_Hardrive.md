---
title: "Formatting A Hardrive"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by short4lif2 on 2005-11-04
Hi, I am running a dual boot system with Breezy and windows.  I just shortened my windows partition to make more room for linux, because i am just about ready to completely switch to Ubuntu (i love it)

I used NTFS resize to make the NTFS partition smaller, but then i realized there is a problem, how do I extend the ext3 partition?  Is there a way to do it?  I tried using qtparted on several bootable distros (NTFS resize, knoppix, and DSL)  But none of them can do it.  Of course the QTpart in ubuntu can not do it because the system can not be changed if it is mounted.

How do i extend that partition?

---

### Post by Confused Fishcake on 2005-11-04
Try partition manger, handles all filesystems (At least linux ones.)

EDIT: Try the Ubuntu install cd.

---

### Post by short4lif2 on 2005-11-06
i don't think that can expand partitions, it can delete the current one and replace it with a bigger one.  I would prefer something more solid

---

### Post by short4lif2 on 2005-11-07
anything?

---

### Post by short4lif2 on 2005-11-07
I found out about fdisk but i am not sure if that can do resizing.

---

### Post by psusi on 2005-11-07
fdisk does not muck with the volume, only the partition table.  You will need to use it to update the partition table to reflect the new size of the volume after changing it with either ntfsresize or resize2fs.  

Try gparted for a nice gui way, and if that doesn't work, you can use resize2fs + fdisk.

In the case of expanding a partition, you will need to use fdisk to make the partition larger first, then resize2fs to expand the filesystem to use the new space.  When shrinking, you shrink first, then fdisk.  gparted handles both steps automatically.

---

