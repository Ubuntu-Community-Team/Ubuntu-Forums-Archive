---
title: "mp3 player shows wrong free space"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by _chAos_ on 2006-07-26
I searched the forum and i can't find what's wrong. I have a 512mb philips mp3-player. Nautilus shows 2 items on the disk totalling 4.9KB, and 322MB free space. 

There are no hidden files on the drive: (VOICE is empty)
> dean@chAos:/media/usbdisk$ ls -al
total 16
drwx------ 3 dean dean 4096 1970-01-01 01:00 .
drwxr-xr-x 6 root root 4096 2006-07-26 17:08 ..
-r-x------ 1 dean dean  948 1999-12-31 23:00 SETTINGS.DAT
drwx------ 2 dean dean 4096 2002-12-27 17:44 VOICE
dean@chAos:/media/usbdisk$

Gparted says it is a 495.97 MB disk, with 173.80 MB used (322.18 MB free).

the partition seems to be right:
> dean@chAos:/media/usbdisk$ fdisk /dev/sdb -l

Disk /dev/sdb: 520 MB, 520093696 bytes
256 heads, 62 sectors/track, 64 cylinders
Units = cylinders of 15872 * 512 = 8126464 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64      507873    b  W95 FAT32
dean@chAos:/media/usbdisk$

I'm rather new to linux, so i might have made a really stupid mistake :). Any ideas?

btw my other mp3-player works well (creative rhomba nx)

---

### Post by philippe_carlo on 2006-07-26
Could it be that the /dev/sdb1 partition is not taking up the entire available space?

---

### Post by _chAos_ on 2006-07-26
> **philippe_carlo said:**
> Could it be that the /dev/sdb1 partition is not taking up the entire available space?

no, it shows the correct amount of free space in windows.

---

### Post by TheRecluse on 2006-07-27
i had a similar problem with a memory stick. try looking for a folder called "trash" or something to that effect on your mp3 player.

after deleting it through linux, it may have just gone to a trash folder instead of removing it from the player

---

### Post by _chAos_ on 2006-07-27
> **TheRecluse said:**
> i had a similar problem with a memory stick. try looking for a folder called "trash" or something to that effect on your mp3 player.

after deleting it through linux, it may have just gone to a trash folder instead of removing it from the player

I already checked that (ls -al). It does not seem to be the case :).

---

### Post by Cyphen on 2007-08-23
I know that this is an old thread but just had a similar problem, where my creative player didn't show correct storage space after i deleted the contents, when i emptied the wastebasket it returned my full storage space, i am total n00b to Linux but thought i would suggest in case someone has a similar issue!! :)

---

