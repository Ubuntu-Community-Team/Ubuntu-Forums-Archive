---
title: "Repairing a damaged file system"
date: 2008-11-30
forum: General Help
---

### Post by rayofash on 2008-11-30
I have 2 hard drives setup as such:

sda (has 3 partitions, sda1 is root, sda2 is an ntfs with Windows Xp, and sda3 is the swap)

sdb (is ntfs)

sda1 has Ubuntu but got damaged when I created the sda2 partition. I had made a backup of the entire partition and placed it in sdb beforehand, so I completely cleared out sda1 and just replaced it with the backup. I loaded a live CD and replaced the old UUID information in menu.lst and fstab with the new UUIDs.

Everytime I tried to booting I got errors that the file system is unsupported and read only and couldn't find the swap so it had to make a virtual one or something. I went back into fstab and removed the line that sets it to read only on errors. This time it loads, but only to a shell and it wont let me log in (it says my username and password are incorrect).

Is there any way to fix this, or do I have to do a complete reinstall?

---

### Post by sdowney717 on 2008-11-30
it will likely be easier and less stressful to just reinstall.
I Use IBEX

---

