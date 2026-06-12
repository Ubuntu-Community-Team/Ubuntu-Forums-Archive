---
title: "Resizing data-only NTFS disk"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by gerbman on 2005-08-20
I have a 120 GB NTFS disk that I previously used alongside my Windows (now Ubuntu) disk.  The disk is about half full, and I would like to shrink the NTFS partition to make room for a FAT partition.  I used the ntfsresize tool in an attempt to resize the NTFS partition, and executing ntfsresize --info on the partition gives the following:

```
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 59999994368 bytes (60000 MB)
Current device size: 120023253504 bytes (120024 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 52502 MB (87.5%)
Collecting shrinkage constrains ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :      3254 MB             0
Multi-Record       :     37291 MB         12089
```

This looks correct to me, with the current volume being around 60 GB and the entire device being around 120 GB.  Next I tried using fdisk to create a FAT partition in the free space, but fdisk still thinks the NTFS partition takes up the whole drive.  I installed gparted, and not only does it think that the NTFS partition takes up the whole drive, but won't let me make the NTFS partition smaller.  I think i'm missing something obvious here, but for the life of me can't figure it out.  Any thoughts?

Thanks.

---

