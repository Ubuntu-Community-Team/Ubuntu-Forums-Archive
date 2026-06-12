---
title: "Blocks, Sectors and partition size"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by bluedalmatian on 2007-11-04
I apologise if this is covered elsewhere but can't see it.

I've got a RAID mirror with 2 disks, one of which has failed and I'm replacing it, which involves partitioning it to match the existing drive.

Im having a problem getting each partition set to the minimum needed block size.  I dont understand how blocks relate to sectors, cylinders and the amount of useful space resulting on each partition? 

One book I've got says a block in Linux is 1024 bytes, another book (both O'Reilly) say block size can be altered with the mkfs command which is confusing.

How can I make each partition a set number of blocks? fdisk asks for a starting and ending cylinder or a starting cylinder and a size in bytes/KB/MB, but doesnt allow you to specify blocks? If I specify the size in MB it doesnt seem to guarantee there will be at least the same no of blocks as the other drive.

---

### Post by bingoUV on 2007-11-04
> **bluedalmatian said:**
> I apologise if this is covered elsewhere but can't see it.

I've got a RAID mirror with 2 disks, one of which has failed and I'm replacing it, which involves partitioning it to match the existing drive.

Im having a problem getting each partition set to the minimum needed block size.  I dont understand how blocks relate to sectors, cylinders and the amount of useful space resulting on each partition? 

One book I've got says a block in Linux is 1024 bytes, another book (both O'Reilly) say block size can be altered with the mkfs command which is confusing.

How can I make each partition a set number of blocks? fdisk asks for a starting and ending cylinder or a starting cylinder and a size in bytes/KB/MB, but doesnt allow you to specify blocks? If I specify the size in MB it doesnt seem to guarantee there will be at least the same no of blocks as the other drive.

fdisk just partitions a disk into "subdisks". It has nothing to do with the filesystem on it. You may not even choose to create a partition, fdisk will not mind. 

Blocksize is a concept of a filesystem. Which is why you can alter it with an mkfs (make a filesystem) command. Making a filesystem is the step that comes after the (optional) step of partitioning a disk. It is here that you specify a block size.

I do not have much experience with raid, but I think mirrored partitions need to be of same size (number of cylinders) . They should also be formatted with the same filesystem, with the same block size.

---

### Post by bluedalmatian on 2007-11-04
How can you check for an existing filesystem, what its block size is?

---

