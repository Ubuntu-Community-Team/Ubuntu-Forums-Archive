---
title: "file permissions"
date: 2008-11-17
forum: General Help
---

### Post by rusty_jones on 2008-11-17
How do I set fat32 hard drive permissions on ubuntu 8.10.

I am also a newbie with ubuntu. Currently my permissions are set for root and i want to set them for Rusty.

Rusty

---

### Post by bodhi.zazen on 2008-11-17
You set the permissions of a FAT partition at the time of mounting the partition.

How did you mount it ?

See :

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: 
[list=number]
[*]vfat (FAT) use dmask=027,fmask=137
[indent]more permissive permissions : dmask=000,fmask=111[/indent]
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent]
[/list]

---

### Post by rusty_jones on 2008-11-17
for some reason I can't unmount my hard drive. Used gksudo nautilus to unmount drive and it comes back Drive busy. I new to ubuntu and 
I don't know what you mean by ```
use dmask=027,fmask=137
```.

I need to set permissions on vfat32 not NTFS.

Rusty

---

### Post by bodhi.zazen on 2008-11-17
can you provide more information ?

What is the partition you are trying to modify ? 
How did you mount it ?

When it says a partition is in use, it generally means you are using something on the partition, an open file, or if you are in a terminal you have cd into the partition.

umask and dmask are options for mounting, see :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

(scroll down to the section on vfat)

and ntfs-config works on vfat as well as ntfs partitions.

---

