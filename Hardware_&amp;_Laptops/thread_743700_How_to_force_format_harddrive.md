---
title: "How to force format harddrive"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by Blacklife08 on 2008-04-02
I have a harddrive that is reported to be running ntfs-3g, and i am trying to format it to fat or fat32, however for some reson in Gparted, even though i can see the disk, i can not make any changes to the partitions.  I do have the ntfs configuration program installed

any help please?  im desparate!

---

### Post by jespdj on 2008-04-03
Maybe it is mounted as read-only? Make sure it is mounted as read-write. Is this an external harddisk, connected via USB or Firewire, or an internal harddisk, connected via IDE or SATA?

---

### Post by Blacklife08 on 2008-04-03
It is a external via USB
for some reason though instead of a normal name like sdb1 or something, it is ######
and yes when i looked at the permissions it seemed to be read only, but i dont know how to change that

---

### Post by njparton on 2008-04-03
Windows may not have released it properly last tim you used it?
 
Boot into windows and try releasing it via safely remove hardware or maybe even use the disk partitioner in windows to first delete all the partitions on the hard drive?
 
The latter will give you an empty hard drive to play with.
 
Anotehr way would be to use "Super F disk" to remove everything from the hard drive and partition it.  Super F disk is a bootable CD rom download.  Google it.

---

### Post by vanadium on 2008-04-03
A drive CAN'T BE MOUNTED when you want to format it. Right click the partition in gparted, select "unmount" and then you will be able to format it.

---

### Post by Blacklife08 on 2008-04-03
Thanks guys
i will try those and get back to you!

---

