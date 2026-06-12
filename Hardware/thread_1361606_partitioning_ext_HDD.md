---
title: "partitioning ext HDD"
date: 2009-12-22
forum: Hardware
---

### Post by AM_SOS on 2009-12-22
hi all !
i have recently bought a new WDC ext HDD (2.5 inches).
now this has NTFS formatting by default and its installed itself automatically on my XP SP2 platform.
however , i also use ubuntu 9.10 as dual boot with XP.
is it possible to use the ext HDD to backup files from both OS's ?
how do i create an ext3 format partition on the NTFS formatted drive ?
is this advisable? any possible side effects of using the ext HDD in this way?
and finally, how am i to do this? :-)
thanks !

---

### Post by IcarusR on 2009-12-22
Have you tried plugging it in & see if it works & if you can write to it as it is ? 
Ubuntu should support NTFS filesystem, if not drivers are available in the repos 'ntfs-3g'

---

### Post by AM_SOS on 2009-12-23
thanks Icarus!
actually that was the first thing i did. i have had no problems with pen drives (FAT 32 format) on my 9.10 and XP.

i expected the same with the WDC ext HDD. alas, there was no activity. i mean that there should have been an icon on the desktop and it wasn't there.

btw, i checked the manuals supplied with the WDC 250 GB and the only operating systems they talk of are the Windows platforms and Mac OS :-(

does this mean that my ext HDD will never run on Linux ? :-(

Please help !
thanks

---

### Post by IcarusR on 2009-12-23
This is strange as Karmic has ntfs support by default.

Does the drive show up in fdisk ?
```
sudo fdisk -l
```

Check in gparted to see if it has hidden flag set.
```
sudo gparted
```


To answer your origional question....

I believe the WDD external drives use a proprietary software on windows to access the drive & to do backups.
If you shrink the ntfs partition & create an ext partition I'm not sure if the wd software will work any more under windows. Is partition size hardwired in software ?
Personally I would dump the wd software (which, by the way, will not backup hidden files on os backup) & reformat it fat32 & use rsync to do backups under both os's.

Gparted can be used to shrink partition & then create an ext partition.
Check out gparted docs at 

[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

---

