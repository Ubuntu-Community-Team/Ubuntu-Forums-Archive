---
title: "Error mounting secondary parition"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by cajunaggie on 2005-02-18
I have my harddrive split into two 40GB paritions (one for Ubuntu and the other for a possible dula boot of Windows) and one 80GB partition. The 80GB use the FAT file system to that if I dual boot Windows can read data and I can share between the two OS's.
I keep running into two problems:
1)The partition won't mount either in boot up or manually. The error messages says
"mount: wrong fs type, bad option, bad superblock on /dev/hda7, or too many mounted file systems." What the heck?
2)On the rare occasion when the partition does mount (I have no idea why it mounts sometimes or not others) it's inaccessible except through root.

I've read and followed the procedures for mounting Windows paritions/harddrives in the Unofficial User's Guide, but to no avail.

Any thoughts or suggestions?

---

### Post by dewey on 2005-02-18
Make sure the volume isn't already mounted.
Make sure that you're using the filesystem type "vfat" for fat.
Make sure that the directory you're mounting to, actually exists beforehand.

---

### Post by cajunaggie on 2005-02-19
I fixed it. Apparently I kept mistyping a command.

---

