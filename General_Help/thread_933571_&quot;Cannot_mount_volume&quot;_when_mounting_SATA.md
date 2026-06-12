---
title: "&quot;Cannot mount volume&quot; when mounting SATA HDD"
date: 2008-09-29
forum: General Help
---

### Post by alastabesta on 2008-09-29
Hi all,

I am using ubuntu 8.04 and experienced the following problem when I try to mount the sata drive on:

"Cannot mount volume
unable to mount the volume SATA

$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Mount is denied because NTFS is marked to be in use"

When I was partitioning for linux I wanted to use the old ATA for dual booting and ubuntu somehow prefers SATA (sorry do it manually was out of the question as I don't know how). As a result I disconnected the SATA and now that I reconnect it back up I am unable to mount it.

My system setup is 2x HDD (ATA & SATA), windows & linux on ATA and SATA is where I keep all my files, would like to use SATA as storage space only.

Any help would be greatly appreciated.

---

### Post by Titan8990 on 2008-09-29
Usually happens when the drive is on Windows and then Windows is not shut down properly. If this is the case boot in to Windows, shut it down properly, and then try to mount the drive.

---

### Post by alastabesta on 2008-09-29
Thank you Titan8990, its working now :D

---

