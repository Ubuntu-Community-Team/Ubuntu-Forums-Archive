---
title: "External hard drive wont mount (ntfs)"
date: 2008-07-16
forum: Hardware
---

### Post by Exile666 on 2008-07-16
for a while i have had vista duel booted with Ubuntu. And whilst i was using Ubuntu i have been able to access my external hard drive. However, now i have gotten rid of vista and now only have Ubuntu, but now i can't use my hard drive. Is this because ntfs is strictly a windows format, and now that i have uninstalled vista its not working now, help anyone? ntfs-3g doesn't work.

---

### Post by ProbablyX on 2008-07-16
Maybe this will help:
[http://www.linux-ntfs.org/doku.php?id=ntfsmount](http://www.linux-ntfs.org/doku.php?id=ntfsmount)

on ubuntu ntfsmount is installed via the package "ntfsprogs"

---

### Post by mtbsoft on 2008-07-17
It may just be that you didn't unmount (Safely Remove) the USB drive before unplugging it in Windows - I've had this myself.

Just plug it in to any latter version Windows (2K, XP, Vistugh) machine which supports NTFS, let it mount it there, then use the Remove USB Device taskbar thing to Safely Remove it.  You should then find it will mount in Linux.

---

### Post by Exile666 on 2008-07-17
Thanks for the help, but i just formatted the entire thing to fat32

---

### Post by mtbsoft on 2008-07-17
Just ought to mention that I've had issues with FAT32 partitions over 32Gb in size.  I spent ages tracking down a bug with VMWare Workstation, trying to access images on a 40Gb FAT32 partition - soon as I resized it to under 32Gb, the issues went away.

---

