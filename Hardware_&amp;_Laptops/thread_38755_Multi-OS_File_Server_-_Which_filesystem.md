---
title: "Multi-OS File Server - Which filesystem?"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by slunk on 2005-06-01
I plan on using my second hard drive (hdb) as a file server for my home network.  I added the 160GB drive today and would like to use it as the main network share.  I have three other systems: 2 XP and 1 OS X Tiger.  What is the best filesystem to use for the whole 160GB?  Do I have to use fat32 for full read/write access for all users?  If so, what utility will setup the drive and allow me to format it as fat32?

Thanks for any help!

---

### Post by somuchfortheafter on 2005-06-01
cfdisk *whatever drive it is*
like sudo cfdisk /dev/hdb
and then parition it as you wish and you will see the option of type and you select fat 32.. that has worked for me anyway, however your /etc/fstab will also have to be altered to access the new partition.

---

