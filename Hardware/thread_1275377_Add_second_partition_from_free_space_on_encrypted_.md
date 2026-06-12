---
title: "Add second partition from free space on encrypted drive"
date: 2009-09-25
forum: Hardware
---

### Post by gofishel on 2009-09-25
When I installed I choose the option for full disk encryption, however I didn't allow the partition to use all the disk space.
Now I want to use the free space and make a second partition, but I don't see it.

GParted shows:
 /dev/Mapper/sda1_crypt  -  111GB
 /dev/mapper/laptop-root  -  71GB
 /dev/mapper/laptop-swap_1  - 3GB

So /dev/mapper/laptop-root is my "working" partition that I am using with 70 GB of space. I know I have 40 Gb of free space (It's a 120 GB drive)
fdisk just shows a 116GB partition.
How do I get to it?

Thanks

---

### Post by gofishel on 2009-09-29
it's a LVM partition :)

---

