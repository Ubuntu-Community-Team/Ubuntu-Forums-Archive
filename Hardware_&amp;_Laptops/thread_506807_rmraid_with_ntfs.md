---
title: "rmraid with ntfs"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by DeltaZero on 2007-07-22
Hi,
   I have nForce2 NVRAID with 2 mirrored NTFS disks, where I keep all my music, documents, etc.
   I have tried to use RMRAID, and it does map the disks correctly (creates one raid core and one linear device in /dev/mapper/), but I cannot mount it. I have tried both supplied ntfs, and ntfs-3g, and neither works.
   When I use the built-in ntfs, and put the RMRAID mapping to mount from fstab, it sais in the disks manager that file system is ntfs, but it does not see how much free space there is, and the mounting point folder is empty. With ntfs-3g that partition shows as unavailable/unknown file system.
   I think I read somewhere that this is a known issue with early version of RMRAID, but there isn't any newer version for Ubuntu (I use 6.06).
   Can anybody help? Thanks!

---

### Post by DeltaZero on 2007-07-27
I gave up, converted to FAT32

---

