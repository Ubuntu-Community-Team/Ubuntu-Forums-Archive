---
title: "Cannot boot Ubuntu"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by ovistanciu on 2007-02-06
Hi!

I'm running Ubuntu 6.10 on a Dell Inspiron 5150, P4 3GHz, 512 MB RAM, 40 GB HDD, nVidia Go5200 32MB.

Ubuntu is installed on a 9 GB logical partition (hdc6, formatted with ext3).

I had some problems with my filesystem, i.e. when running automaticaly fsck (it is scheduled to run after 30 boots) got some errors. After that, I usually booted from LiveCD and ran fsck on hdc6, and the problems were solved. 

The last time, unfortunately, things went wrong. Booted, fsck checked the filesystem for errors, booted LiveCD, repaired errors and then started Ubuntu normally. Worked for a while, then locked my screen and went for coffee :) When I tried to unlock my screen, X crashed and I rebooted. Fsck told me that i had a file system with errors, so it forced a check, found a single error (something like "last access time is in the future") and fixed that, then did an automatically reboot in 5 sec. When it booted again, the same thing happened, so right now i'm caught in some kind of a loop and i can't boot my Ubuntu.

I tried booting liveCD again, but when I ran fsck, hdc6 came out clean. 

How can I fix this? How can I boot in an interactive way (so i can skip fsck check)?

---

### Post by ovistanciu on 2007-02-06
Tried booting in Recovery Mode

Here's what I got:

```
/dev/hdc7 contains a filesystem with errors, check forced.
[17179797.892000] Buffer I/O error on device hdc7, logical block 65590
Error reading block 65590 (Attempt to read block from filesystem resulted in short read) while doing inode scan.

fsck died with exit status 4

```

BTW, Ubuntu is installed on hdc7, NOT hdc6, like i mentioned in my previous post.

---

### Post by Rodolfo_Hermans on 2007-06-08
In a laptop HP Pavilion dv6225us (AMD 64) with Ubuntu 7.04 64 bit I am gettinga forced check.
The problem is that during the check, fsck hangs up the computer before reaching 100% and there is no way to skip it. What can I do? I can NOT boot!!! :(

---

### Post by Herman on 2007-06-09
Hello Rodolfo_Hermans,
I would boot the Ubuntu LiveCD and open a terminal and run 'sudo e2fsck -f -y -v /dev/hda2', if you have an ext3 file system and it is in partition number 2 of your first IDE disk, ```
sudo e2fsck -f -y -v /dev/hda2
``` If you aren't sure what partitions you have, run 'sudo fdisk -lu' first to find out or look with GParted in the Live CD. Adjust the command accordingly. 
Hopefully, that should fix it,
Regards, Herman :D

---

