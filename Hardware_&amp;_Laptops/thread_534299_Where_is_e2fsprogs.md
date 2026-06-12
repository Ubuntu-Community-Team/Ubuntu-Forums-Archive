---
title: "Where is e2fsprogs?"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by ZootNerper on 2007-08-25
Hi,

I have a bad partition on an unmounted disk, that I would like to retrieve some files from, before I partition it. I think e2fsprogs may do this. I accidently found out that it's is somewhere on the computer when I tried the following apt-get:

zoot@Bollocks5:~/e2fsprogs/build$ sudo apt-get install e2fsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e2fsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But I don't know where it is. If I try to run it, I get this:

zoot@Bollocks5:~/e2fsprogs/build$ e2fsprogs -help
bash: e2fsprogs: command not found
zoot@Bollocks5:~/e2fsprogs/build$ 

Could someone point me in the right direction. (using 7.04)

-- Zoot

---

### Post by seattleweb on 2007-08-25
You need to read the man pages of mke2fs... mke2fs is the command I think your looking for

---

### Post by Rui Pais on 2007-08-25
hi,
e2fsprogs is just a name for a bunch of programs (that install under /sbin/)

you probably need e2fsck:
```
sudo e2fsck -f /dev/xxxx
```

check man e2fsck too.

---

### Post by ZootNerper on 2007-08-25
Thanks for your suggestions.

I've attached a screen shot from gparted showing the disk concerned. (Not sure where it will appear in this post)

If I try e2fsck on sdb2 I get:

[INDENT]zoot@Bollocks5:/media/sda5/Temp$ sudo e2fsck -f /dev/sdb2
Password:
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?
[/INDENT]

If I try e2fsck on sdb5 I get:

[INDENT]zoot@Bollocks5:/media/sda5/Temp$ sudo e2fsck -f /dev/sdb5
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: No such file or directory while trying to open /dev/sdb5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
[/INDENT]

So, at the moment I can't check and or fix the partition.

I looked at "man mke2fs" and it says it is used to create a file system, whereas I want to retrieve the files before I do this. I'm not sure about this, but I thought it may be easier to retrieve them before I delete the old bad partition and create a new. I'm new to Linux so I could easily be wrong!  Is there a program in e2fsprogs to do this?

Cheers.

-- Zoot

---

### Post by ZootNerper on 2007-08-25
OK, problem solved. I ran Seatools boot disk from Ultimate Boot CD, ran a long test and it found 13 errors on the disk and fixed them. Now, I have my disk and files back. [http://ubuntuforums.org/images/smilies/eusa_dance.gif](http://ubuntuforums.org/images/smilies/eusa_dance.gif)

\\:D/

Tanks for your time.

-- Zoot

---

