---
title: "How to partition disk"
date: 2008-10-18
forum: Hardware
---

### Post by vedanta_2004 on 2008-10-18
Hi,
I need to partition my disk since it keeps getting corrupted. I've installed ubuntu 8.04 on a dell inspiron 6000 laptop...
Following is the output fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

I want to partition /dev/sda1 so that I've a separate boot partition and 
it won't get corrupted by anything else...

Thanks in advance,
-Vedanata.

---

