---
title: "Ubuntu Harddisk Convertor"
date: 2008-06-26
forum: Hardware
---

### Post by boho103 on 2008-06-26
Well I've ran into a problem in Ubuntu, I want to convert my EXTERNAL hard drive to ntfs, right now its currently fat32. Is there a program to convert fat32 drives to ntfs for ubuntu or thats ubuntu supported? Thanks! Oh and windows xp will NOT convert it in the cmd console.

---

### Post by volkswagner on 2008-06-26
> **boho103 said:**
> Well I've ran into a problem in Ubuntu, I want to convert my EXTERNAL hard drive to ntfs, right now its currently fat32. Is there a program to convert fat32 drives to ntfs for ubuntu or thats ubuntu supported? Thanks! Oh and windows xp will NOT convert it in the cmd console.

Gparted.

System>Administration>Partition Manager

I am running Ultimate Edition 1.8, my only 8.04 system.  All other version had partition manager in the above location.  TheMann must have removed it or it is not installed by default in 8.04.

Make sure you choose the correct drive, upper right corner is a selection window.  You will need to unmount it first.

---

### Post by logos34 on 2008-06-26
Gparted cannot convert filesystems.  You'd have to copy/backup everything, reformat it as ntfs, then copy everything back.
> 
Oh and windows xp will NOT convert it in the cmd console.you tried CONVERT [driveletter]: /FS:NTFS ?

[http://support.microsoft.com/kb/156560/](http://support.microsoft.com/kb/156560/)

---

