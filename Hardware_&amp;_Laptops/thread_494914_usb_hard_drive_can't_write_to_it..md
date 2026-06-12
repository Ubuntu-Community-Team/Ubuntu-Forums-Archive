---
title: "usb hard drive can't write to it."
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by jdeng@mtoliveboe.org on 2007-07-07
I have a usb external hard drive connected to a hp laptop. I won't let me write to the drive. reported the drive as read only device. any have any idea?

---

### Post by ddrichardson on 2007-07-18
Is the drive formatted as NTFS? NTFS support is limited to read only and AFAIK although there are ways around it the NTFS write support in Linux is sketchy.

If you need to keep the data intact on the drive, then google "convert ntfs to fat32" it's possible. If not then reformat the drive as ext2/3 or fat32 if it needs to be used with Windows.:)

---

### Post by merlinus on 2007-07-18
> 
Is the drive formatted as NTFS? NTFS support is limited to read only and AFAIK although there are ways around it the NTFS write support in Linux is sketchy.


I have been using ntfs-3g for quite awhile now to write to my ntfs partitions, with zero problems.

ymmv....

-merlin

---

### Post by vnrat on 2007-07-18
or ntfs-config 
sudo apt-get install ntfs-config

---

