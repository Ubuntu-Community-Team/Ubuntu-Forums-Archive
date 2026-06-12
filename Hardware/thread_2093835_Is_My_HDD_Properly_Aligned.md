---
title: "Is My HDD Properly Aligned?"
date: 2012-12-12
forum: Hardware
---

### Post by Herg on 2012-12-12
[FONT="Arial"][img]http://i.imgur.com/jjdW5.png[/img]

and how do you check if it's properly aligned? I did some Google search and people say that if it's divisible 512 or 8 and you get a whole number then it's properly aligned, but what exactly is it divided by? Is it the first sector? [/FONT]

---

### Post by oldfred on 2012-12-12
Welcome to the forums.

The first sector of every writable partition. The extended partition does not count, but each logical in it does.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?tit](http://ubuntuforums.org/showthread.php?tit)'s 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
sudo parted /dev/sda unit s print

---

### Post by ahallubuntu on 2012-12-12
In a terminal, type

```
sudo fdisk -lu

```

Here's my drive's first partition:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    71296469    35648203+   7  HPFS/NTFS
```

Mine isn't aligned because it starts at sector 63 - but my drive is an older 512K sector drive so no problem.  If it were aligned, it would probably start at 2048.  

I think starting with Ubuntu 11.04, Gparted (if you use that to partition) will automatically align new partitions.  Did for me on my advanced format drives.  Yes, it makes a huge difference in performance.

---

