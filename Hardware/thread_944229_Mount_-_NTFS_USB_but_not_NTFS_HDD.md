---
title: "Mount - NTFS USB but not NTFS HDD"
date: 2008-10-11
forum: Hardware
---

### Post by h3llh0l3 on 2008-10-11
Hi all,

Just a quick question which came up to me while I was mounting a USB stick which I formatted to NTFS FS.
Why does
```
mount /dev/sdb1 /media/sdb1
```
mount the NTFS formatted USB stick and
```
mount /dev/sda1 /media/windows
```
does not mount the HDD partition.
Why do I have to use
```
ntfs-3g /dev/sda1 /media/windows
```
to the job?

It may be silly but it just striked me... :)

---

