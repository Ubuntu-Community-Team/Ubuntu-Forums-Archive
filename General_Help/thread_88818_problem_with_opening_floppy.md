---
title: "problem with opening floppy"
date: 2005-11-11
forum: General Help
---

### Post by ento on 2005-11-11
Hi 
i have just installed edubuntu and now i can't mount floppy.
The floppy is working i did type cat /dev/fd0 and it reda the floppy.
But i can not mount it.
What to do?

/stefan

---

### Post by hajk on 2005-11-11
This is a known problem with the "pmount" package in breezy. You could *temporarily* add the dapper repository and install its "pmount" package.

A work-around is to open a terminal (or hit Alt-F2) and give the command
"mount /media/floppy". 

The auto-detection of the file system on the floppy sometimes fails. If the file system is msdos (or vfat), then you could change the word "auto" in  the /etc/fstab file entry for the floppy to "msdos". Some people use ext2 file system on their floppies, in which case you change it to "ext2". The floppy should mount with the above command. Unmounting works by right-clicking on the icon and selecting Unmount Volume.

Why isn't the pmount package in dapper added to the breezy-updates repository? Good question...;)

---

### Post by Elitist_Phoenix on 2005-11-11
mount /dev/fd0 /mnt/floppy
? Maybe, worked in slackware :P

---

