---
title: "Grub Error 22"
date: 2008-10-05
forum: General Help
---

### Post by O-pos on 2008-10-05
Hi,

I want to give my old laptop to my sister. I had dual boot, so I deleted all ubuntu partitions and formatted as one NTFS partition, because she does not know anything about Linux.

So, now after I resterted my laptop, the system does not boot, instead it shows message Error 22. How could I deal with that? the partition C, where all windows files are, remain unaffected.

---

### Post by caljohnsmith on 2008-10-05
You just need to replace Grub in the MBR (Master Boot Record) with a Windows MBR. If you have a Windows Install CD, boot that, go to the recovery console, and run:
```
fixmbr
```
If you don't have a Windows Install CD, you can use the [Super Grub Disk]("http://www.supergrubdisk.org") to install a Windows-compatible MBR.

---

### Post by O-pos on 2008-10-05
Thanks, Super Grub Disk helped!

---

