---
title: "ext3 recovery"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by arzafen on 2007-06-11
Hi, 
I cannot access to my external harddrive which is formatted in ext3 filesystem with 500Gb capacity. When I plug it to the computer, it shows /dev/sdb but no /dev/sdb1. Running fsck on /dev/sdb gives 

fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

```
sudo fdisk /dev/sdb
```

Unable to read /dev/sdb

```
mount /dev/sdb 
```
gives

mount: /dev/sdb: can't read superblock



Do you have any idea about the problem and possible solutions?
Any help is greatly appreaciated.
Thanks in advance

---

### Post by taurus on 2007-06-11
Why don't you install gparted and use it to create a partition, /dev/sdb1, and format it to ext3.

```
sudo aptitude update
sudo aptitude install gparted
gksudo gparted
```

---

### Post by arzafen on 2007-06-12
I installed gparted.One weird thing is that it shows negative capacity for the external drive. In addition, I have some data in it. Won't this data be lost if I format it to ext3?

---

