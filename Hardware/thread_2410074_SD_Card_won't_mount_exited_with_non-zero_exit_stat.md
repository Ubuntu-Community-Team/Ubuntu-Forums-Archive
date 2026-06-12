---
title: "SD Card won't mount: exited with non-zero exit status 32: mount: mount /dev/mmcblk0p1"
date: 2019-01-10
forum: Hardware
---

### Post by stillnotthateasy on 2019-01-10
Hi there,
My SD card won't mount. I understand it's probably because I removed it without unmounting it first.

Here is what Xubuntu tells me when trying to mount it:

"Error mounting /dev/mmcblk0p1 at /media/username/TEST EXT4: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/mmcblk0p1" "/media/username/TEST EXT4"' exited with non-zero exit status 32: mount: mount /dev/mmcblk0p1 on /media/username/TEST EXT4 failed: File exists"

What should I do? My OS is Xubuntu.

---

### Post by stillnotthateasy on 2019-01-10
by the way, the OS is:
Description:	Ubuntu 16.04.5 LTS (XUBUNTU)
Release:	16.04
Codename:	xenial

---

### Post by mikasu on 2019-01-11
Did you try formatting it or you want to keep the files absolutely? Is the file system the right one? Because, as I see, it's trying to mount it on ext4 file system, is it formatted in ext4 or is it fat, fat32, exfat...?

---

### Post by stillnotthateasy on 2019-01-15
> **mikasu said:**
> Did you try formatting it or you want to keep the files absolutely? Is the file system the right one? Because, as I see, it's trying to mount it on ext4 file system, is it formatted in ext4 or is it fat, fat32, exfat...?

believe it or not: now it works and all files are visible... 
I have no idea how this has happened... I did try to verify everything trough GParted but, after that, it still did not work and suddenly everything was OK...
no idea why... but at least it works now

---

### Post by mikasu on 2019-01-15
Maybe it is formatted in fat and your system was thinking it was in ext4? Anyway, glad it was a minor issue, surely unmount your stuff first, better be safe than sorry.

---

