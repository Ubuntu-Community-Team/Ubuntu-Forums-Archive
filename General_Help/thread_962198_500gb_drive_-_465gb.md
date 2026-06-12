---
title: "500gb drive - 465gb??"
date: 2008-10-29
forum: General Help
---

### Post by Roasted on 2008-10-29
Windows recognized my 500gb drive as being 487, or something of that nature.

Ubuntu recognizes it as 465gb. Why the difference?

Note - I know the partitions on that drive aren't effecting the difference in reading between the operating systems, because I have a second 500gb drive that's identical to the one with my OS's on it, and that one (which has 1 single large partition with no leftover space) has the same reading with 465gb total size.

---

### Post by ryanhaigh on 2008-10-29
Ubuntu reserves 5% of the partition for access by root. This is implemented as a means to allow administration even if the filesystem is otehrwise full. You can easily changed this using tune2fs.

```
sudo umount /dev/sdb1 #just for safety not sure if its actuall needed
sudo tune2fs -m 1 /dev/sdb1 #this reserves only 1%

```

---

### Post by Roasted on 2008-10-29
Ahh, it's not a problem. I simply wanted to know why. Thanks!

---

### Post by sdennie on 2008-10-29
I'm surprised the reserved space would cause a difference in partition size reporting.  Are you sure this isn't a case of the two operating systems reporting sizes using a different definition of kilobyte?  This is common even between apps on Linux.  The Definitive Standard for understanding this difference can be found here: [http://xkcd.com/394/](http://xkcd.com/394/)

---

### Post by alienprdkt on 2008-10-29
Maybe difference in file system (compression, maybe)

see here: 

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

scroll down to #127

---

### Post by Roasted on 2008-10-29
I noticed this before I even had installed Ubuntu. I installed XP and saw how much space was available on the hard drive, which was 480 or something around that. Shortly after I installed Ubuntu, which read the drive (with XP installed) as 465 total. That's why I wasn't sure.

---

