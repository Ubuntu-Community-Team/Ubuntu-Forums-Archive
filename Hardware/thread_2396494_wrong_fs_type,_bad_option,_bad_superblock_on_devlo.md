---
title: "wrong fs type, bad option, bad superblock on /dev/loop3, missing codepage or helper"
date: 2018-07-16
forum: Hardware
---

### Post by Javierhermosa on 2018-07-16
Hi guys!

I am trying to mount an image created with clonezilla. I created the image out of an 8TB Partition. I am trying to mount it on a 12TB partition. 

I used zstd for the compression and I got all the parts concatenated and then decompressed with zstd without errors. Now when I try to mount the img file to explore it (I need to rescue a file if it is still in the image), I get the message on the title. 

If I "sudo fdisk -l u=sectors sdb1.img" I get this: 

Disk sdb1.img: 7.3 TiB, 7999393497088 bytes, 15623815424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

That means it's a partition and not a disk, therefore I cannot be making a mistake with the offset of the sectors and stuff.

Any ideas?

Thank you!

---

### Post by TheFu on 2018-07-16
Have you tested the process on smaller clones?  A few hundred MB, then a few GB and larger than 5GB, then 1.999TB and then over 2TB?

---

### Post by Javierhermosa on 2018-07-19
I haven't, because I really need to check this image to see if I can recover some lost files. How should I proceed about testing smaller clones?

---

### Post by TheFu on 2018-07-19
> **Javierhermosa said:**
> I haven't, because I really need to check this image to see if I can recover some lost files. How should I proceed about testing smaller clones?

I'd use a virtual machine with a few virtual HDDs. That would be the easy way, but I'm very comfortable using virtual machines.

But because "everything is a file" in Unix, you can make fake source and target storage devices from files.   The fact that you are mounting a loop device already made me think you understood.

---

