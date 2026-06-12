---
title: "cant get to partitioning menu"
date: 2008-07-30
forum: General Help
---

### Post by Champy on 2008-07-30
i had problems with how much space i had on ubuntu?

well, i uninstalled it, which isnt too big of a problem because i didnt have any files.

and i used wubi to reinstall it, but this time gave it 30GBs, which is good. but the problem is when i open ubuntu and it starts installing, it stops and says "no root file system is defined, please correct this from the partitioning menu"

which i would like to do because i thiink its in system/administration/partitioning menu

but i dont have like any desktop its just the ubuntu background and the window that says that

so i cant get to the partition menu.

---

### Post by minhmeoke on 2008-07-31
On windows, are you using NTFS or FAT32 filesystem? FAT32 only supports up to 4GB files, so that would be your maximum virtual disk size.

Also, open up a terminal (ctrl+alt+f1) and post the results of the following commands:
cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions

---

### Post by ago on 2008-07-31
You might also want to try to uninstall, defgrament, run chkdsk /r, and install again.

---

