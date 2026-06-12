---
title: "Error mounting: mount exited with exit code 1"
date: 2010-01-07
forum: Hardware
---

### Post by sepia-shots on 2010-01-07
Until a few days ago, my system seemed to work perfectly. However I now get the error 

Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/cdrom2 does not exist

when I put a disk into either of my DVDROM drives. The only change that I know of has been a number of patches coming through. 

The message is right in that in /dev the mount points don't exist. cdrom3 and cdrom4 do exist (the machine has never had 4 CDROMS). In places in finds the CDROM and names the disk in there (the error above occurs when you click on the listed device.

uname -a
Linux ubuntu-64 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

Please help!

---

### Post by peyre on 2010-05-04
I get the same thing, but I haven't found a solution for it yet.

---

