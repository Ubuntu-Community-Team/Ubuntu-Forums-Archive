---
title: "External USB Hard drive NTFS/Fat32 Partition"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by Kpax1 on 2007-08-16
I have my external usb hdd, /dev/sdb1, partitioned as a single NTFS file system. I want to keep a small portion of it NTFS, and format the rest of it using fat32 or ext3 so that I can read/write on it in Linux. Does anyone know a way I can shrink the NTFS partition so that I can format the other part of it using fat32 without losing the data on the NTFS part?

---

### Post by psusi on 2007-08-16
Use gparted.

---

### Post by patrickfromspain on 2007-08-16
you can write to NTFS using ntfs-3g, it's safe to use.. 

To resize ntfs you probably have to install ntfsprogs, search for it in Synaptic

---

### Post by Kpax1 on 2007-08-16
Thanks, 

I'm an idiot. I used ntfsresize to shrink the ntfs filesystem, then gparted and formatted the whole drive volume anyways because I failed to resize the partition in gparted. Luckily I backed up all the data on DVDs.

Thanks!

---

