---
title: "K3B: &quot;No non-local files supported&quot;"
date: 2005-11-21
forum: General Help
---

### Post by cinematography on 2005-11-21
This is strange. 

My home partition is hda2, and for some reason when I try to burn files from hda3 I get this error message: "No non-local files supported". Is there a way to burn files from another partition using K3B?

---

### Post by blastus on 2005-11-21
If /dev/hda3 is mounted and you can drag n drop files from it to create a CD then there should be no problem. I routinely burn files from my both my hard drives with no problems. You can't burn any files at all? To start, make you are not trying to burn any files that are hard or soft links. Also make sure you have read permission on those files and execute permission for directories.

You should also make sure that the drive you are burning from is on a different IDE channel than your CD burner. For example, both my hard drives are on the primary channel and my CD burner is on the secondary channel. In your case, your CD burner should be either /dev/hdc or /dev/hdd.

---

### Post by cinematography on 2005-11-22
[QUOTE=blastus]If /dev/hda3 is mounted and you can drag n drop files from it to create a CD then there should be no problem. I routinely burn files from my both my hard drives with no problems. You can't burn any files at all? To start, make you are not trying to burn any files that are hard or soft links. Also make sure you have read permission on those files and execute permission for directories.

You should also make sure that the drive you are burning from is on a different IDE channel than your CD burner. For example, both my hard drives are on the primary channel and my CD burner is on the secondary channel. In your case, your CD burner should be either /dev/hdc or /dev/hdd.[/QUOTE]
Excellent suggestions. Thank you very much!

---

