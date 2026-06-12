---
title: "Accessing Linux Partition from Windows Vista"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by ubuntuubuntu on 2007-06-18
Hi,
My computer's hard drive has one Windows Vista partition and one Ubuntu partition. I want to access my files in the Ubuntu partition from Windows Vista. Is there a software that can do that?
I have tried Explore2fs, but it seems that it is not compatible with Windows Vista.

Thank you.

---

### Post by Kodfish on 2007-06-18
How does this belong in hardware?

Anyways, i think the ideal solution would be to move the files that you need to acess directly onto vista's partition, or another ntfs/fat32 partition. ext2/3 drivers in Windows suck as per my experiance, and it's not difficult to move files around from partition to partition. Try ntfs-3g. I think it's stable in 7.04.

---

### Post by ubuntuubuntu on 2007-06-21
I want to access my files in the Ubuntu partition from Windows Vista. Is there a software that can do that?

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-06-24
[http://www.fs-driver.org/](http://www.fs-driver.org/)

This should work under the 32bit version of VISTA using compatibility mode -- I have yet to find a way to get this badboy installed on the 64bit VISTA OS....I assume this is mainly due in part that the driver itself is not "M$" approved/signed.

---

