---
title: "Possible corrupted usb HD"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by drumlight on 2006-04-01
HI I've got a 120gb freecom hd that is formated into one ext3 partion /dev/sdb1.  My roomate was streaming movie from it to our xbox and half way through he says it stoped playing and he was unable to access anything on the drive through ubuntu. 
I've been trying to find out what might have happened and apart from running fsck /dev/sdb1 i'm not sure what I can do. The output from fsck is > jake@ubuntu:~$ fsck /dev/sdb1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

  Trying to follow the suggestion I ran e2fsck -b 8193 /dev/sdb1 aand recieved the same error messages.  I'm not sure if I've used either of those tools correctly and what else to try.  The only other messages I see relating to this are during boot where a lot of messages about approx scsi node pointing to dead device.  If needed I can try to write down exactly what it says at boot.
  I've also tried looking looking at the system log viewer but am not sure for exactly what I should look.  Any help recovering from this would be massively appreciated because my other hd is mainly full of operating systems and I use this usb for most of my workspace with games, movies and music. Thanks for your time jake

---

### Post by drumlight on 2006-04-01
I've also just noticed that when I start ubuntu there is occasional disk activity, I guess as it looks for a filesystem, but that now it has been on for about half an hour it has shutdown and there is not even a power light onthe hd drive. I've not noticed this state before even when it hasn't been mounted, ie power connected and no power light. Mind you I miss plenty of obvious thing on a daily basis!

---

