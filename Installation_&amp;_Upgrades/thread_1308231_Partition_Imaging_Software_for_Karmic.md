---
title: "Partition Imaging Software for Karmic ?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Bruce R on 2009-10-31
Ever since Ubuntu 6.06.1 (Dapper Drake) I have used Kurt Fitzner's XP/BartPE hosted SelfImage to create progressive Partition Images of new versions of Ubuntu and a lot of other distributions, so that I haven't had 'to go back to square one' when encountering an installation problem.
However with Ubuntu 9.10 (Karmic Koala) and its use of ext4 plus flawed GRUB 1.97beta4, SelfImage cannot cope, so can anyone recommend a proven, faithful restoration after creation, preferably free alternative ? ;)

I should add that whilst my little Ghost 2003 Utility diskette still works for Windows 7, it has never worked for Linux, whilst expensive products like Acronis TrueImage have had problems or limitations. :(
Because it offers the possibility of being universal by use of choice of core imaging program at run-time, at the moment I am trying out different versions and configurations of Clonezilla, in stand-alone or in PartEdMagic form, so far without success. :confused:

---

### Post by phillw on 2009-10-31
> **Bruce R said:**
> Ever since Ubuntu 6.06.1 (Dapper Drake) I have used Kurt Fitzner's XP/BartPE hosted SelfImage to create progressive Partition Images of new versions of Ubuntu and a lot of other distributions, so that I haven't had 'to go back to square one' when encountering an installation problem.
However with Ubuntu 9.10 (Karmic Koala) and its use of ext4 plus flawed GRUB 1.97beta4, SelfImage cannot cope, so can anyone recommend a proven, faithful restoration after creation, preferably free alternative ? ;)

I should add that whilst my little Ghost 2003 Utility diskette still works for Windows 7, it has never worked for Linux, whilst expensive products like Acronis TrueImage have had problems or limitations. :(
Because it offers the possibility of being universal by use of choice of core imaging program at run-time, at the moment I am trying out different versions and configurations of Clonezilla, in stand-alone or in PartEdMagic form, so far without success. :confused:

Have you ever considered the wonderful package called tar ? ... it's what all those fancy GUI beasties use -- Being free, of course, causes people problems.

But, anyways, it's alive, it's free and it will backup anything that linux can mount ...

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

If you want to get really picky & just want to 'photo-copy' a storage device, use copy & convert, handily called dd.

tar is probably the easiest to use, but dd will copy anything at the bit level, so it doesn't need filenames etc.

Phill.

---

