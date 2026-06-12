---
title: "Grub error 2 after cloning disk. Help needed"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2009-10-14
Hi,

I cloned a disk having Windows XP, Ubuntu 8 desktop and Ubuntu 9 server. I used dd to clone it from sda to sdb.

$sudo dd if=/dev/sda of=/dev/sdb bs=450M

fdisk -l shows same partition sizes and types in both disks. If I mount and list files in the cloned partitions, I can see files present. 

When I try to boot sdb I get grub error 2. I changed the cabling and made sdb to sda and tried to boot from sda which was earlier sdb. The error is the same Grub error 2.

Thanks in anticipation.

Regards,
Deepak

---

### Post by dandnsmith on 2009-10-14
The manual says:
"2:Bad file or directory type
This error is returned if a file requested is not a regular file,but something like
a symbolic link,directory,or FIFO."

I can't think what that might be, but you have the actual thing to look at.

Were the HDDs identical? If there was a geometry difference, that might be the cause.

---

### Post by prshah on 2009-10-14
> **deepakdeshp said:**
> 
When I try to boot sdb I get grub error 2.

Did you make any partition active? Eg, on your original (sda) hdd, check the output of fdisk -l to see which partition is marked as "boot" (It will contain a "*"). Then, use fdisk on your second (sdb) and ensure that the same partition is marked "*" in the boot column.

---

### Post by Bucky Ball on 2009-10-14
[http://members.iinet.net.au/~herman546/p15.html#2_](http://members.iinet.net.au/~herman546/p15.html#2_)

Might give some more clues.

---

### Post by deepakdeshp on 2009-10-20
Thanks Bucky. The link about Grub is very helpful. I am going through it.

dd gave errors at the end and I will be trying Clonezilla for cloning the disks. Both the disks are 40gb but of different make.

The active boot partiotion indicated by * is the same on both the disks.

---

