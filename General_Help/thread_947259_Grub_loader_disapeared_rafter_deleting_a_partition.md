---
title: "Grub loader disapeared rafter deleting a partition"
date: 2008-10-14
forum: General Help
---

### Post by Wickd on 2008-10-14
Hi there

I seem to be having some problems with my Grub bootloader. 

Here is what I did:

I had the following partitions
hd0,1 windows (8gb) fat32 (sda1)
hd0,2 ubuntu  (18gb) ext3 (sda2)
hd0,3 swap
hd0,4 Files (200gb) fat32 (sda4)

I then proceeded to remove all partitions and enlarging my ubuntu partition to 248 gb and a 1 gb swap, without formatting anything. I use the Ubuntu partitioner on the live cd

When I rebooted grup dissapeared and was replaced by an Intel(r) Boot Agent v1.2.50

I have tried various methods and also studied the Grub Bootloader process and came to the conclusion that maybe the Master Boot Record (MBR) refered to hd0,2 where it has now changed to hd0,1.

Also my Ubuntu still has the Ubuntu partition saved as  sda2. So I would like to change the partition name to sda1 and also have the Grub bootloader configured to run instead of the Intel bootloader, since the Intel bootloader is not working at present

Please if you have a solution I would be incredibly happy,since I have been trying to fix this for a week

Thanks in advance

---

### Post by justleen on 2008-10-14
you will have to reinstall grub. [This can be done from the live cd ]("http://ubuntuforums.org/showthread.php?t=224351")
the drive names will be trickier though, im not sure wether you can rename this. AFAIK this name changes according to the parition layout (thus is should be sda1 once there are no more partitions in front of it).

---

### Post by geirha on 2008-10-14
It was created as /dev/sda2, and will remain with that name, even though it is the first partition on the drive. There's no danger in that, everything will work as if it was named /dev/sda1. I recommend you just "live with it".

---

