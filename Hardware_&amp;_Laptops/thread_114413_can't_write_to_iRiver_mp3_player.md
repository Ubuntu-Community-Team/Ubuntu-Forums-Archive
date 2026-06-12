---
title: "can't write to iRiver mp3 player"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by aimless on 2006-01-08
No matter what I do I can't get my iRiver 190TC mp3 player to be writable. It mounts fine (albeit sloooowly) but whenever I try to transfer files to it, it says that I don't have the permissions to write to it. This, even though I've checked all the files in the disk and the mount point itself and it says I have writable permissions across the board(user,group,others).
      I used umask=000 in my fstab.  Dmesg gives me the following output after I try          to transfer files,      FAT: Filesystem panic (dev sda)
                               invalid access to FAT (entry 0x0000fd1e) 

Device works fine in WinXP, and other Linuxes I've used.

Going nuts(ARRRRGHHHHH!!!). Any Ideas?

---

### Post by professor_chaos on 2006-01-08
try placing your user id in /etc/fstab like "rw,user=1000,auto"

---

### Post by MetalMusicAddict on 2006-01-08
Or if you can't get that working right do a **sudo nautilus** from the terminal and set the permissions through there.

---

### Post by aimless on 2006-01-09
Thanks for the advice everyone. The problem turned out that the file system on my iRiver was corrupted. I did a chkdsk on it in XP (yuck!!) that found the problem and repaired the file system. Thanks again.

---

