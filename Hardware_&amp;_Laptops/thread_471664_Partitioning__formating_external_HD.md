---
title: "Partitioning / formating external HD"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by bleakcabal on 2007-06-12
Hi, I have a 160gb external HD. Right now it's NTFS. 

I would rather have it under a format that would be more conductive to sharing files between Linux and Windows. 

I was thinking FAT32 since both Linux and Windows can Read/Write FAT32. 
Since FAT32 limits the partition size I tried partitioning the driving and formating the partition as FAT32 using GParted ( gnome partition app ).

Thing is, since I did this I can't read/write the drive under windows and under Linux, I can't mount the drive. When I plug it in, I see an icon appearing on my desktop but it's the unmounted icon. When I try to safely unmount the drive I'm getting an error saying the device isn't mounted.

I'm thinking I did something wrong while partitioning/formating.

Is there anything special I should do when partitioning/formating an external drive ( first time I'm doing this on an external drive ) ???

---

### Post by Gausian on 2007-06-12
ntfs-3g will allow you to share files on the existing ntfs partition, and is way easier.

besides, 160gb as FAT32 isnt a good idea

---

