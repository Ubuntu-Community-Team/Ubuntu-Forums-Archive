---
title: "Ubuntu Drive Space"
date: 2008-09-16
forum: General Help
---

### Post by Doug Biel on 2008-09-16
Before I installed Ubuntu with Wubi I made a partition E:\ from my Hard Drive C:\ and after I installed the operating system it said that all the files on its "filesystem" was using 8.3 GB (Ubuntu filesystem)more or less.  The thing that bothers me is that I Only allowed 7GB (NTFS)maximum for the Hard Drive since the partition holds no more than 8 GB (NTFS).  Is it that it can use more space since it is a different fyle system or is it expanding into another partition?  If this is possible, what is the ratio so I know how much space I acutally have to work with on my Filesystem.

---

### Post by ago on 2008-09-16
The max space is calculated as max free space for the selected drive - 1G. This is to accommodate for the ISO and leave some headroom. That said if you already have a dedicated partition available you might want to consider a full installation.

---

### Post by Doug Biel on 2008-09-17
> **ago said:**
> The max space is calculated as max free space for the selected drive - 1G. This is to accommodate for the ISO and leave some headroom. That said if you already have a dedicated partition available you might want to consider a full installation.

I have always found problems installing the system manually, so I deiced using this, easier, method of installing the system.  I made the partition, long story on how I managed to make it, so it would not interfere with my MS Windows XP, not Vista :), drive.

---

