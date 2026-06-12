---
title: "[SOLVED] Using ntfs-3g from Hardy to read/write files on external harddrive"
date: 2008-07-30
forum: General Help
---

### Post by rtrdom on 2008-07-30
I have Hardy Heron installed and working well. Also have external harddrive
from old lap top with Windows XP on it. How do I mount/create a mount point
in Ubuntu terminal so I can read/write the files in the old harddrive?
using ntfs-3g --help does not give me the answer I need. 
Thanks for a response.

---

### Post by 3rods on 2008-07-30
First you have to create a directory you want to mount it to as root. (or use a directory you already have.)

Create the dir
```
sudo mkdir /media/xpdisk
```

Find out where the USB drive is being attached:
```
sudo fdisk -l /dev/sd*
```
Should be something like /dev/sda1

Mount the USB to the dir
```
sudo mount -t ntfs-3g -o rw /dev/sda1 /media/xpdisk
```

That should do it.

---

### Post by rtrdom on 2008-07-30
Thanks a bunch. It mounted (after I typed it correctly). Now if I can
get it to open a program named Microsoft Streets and Trips I think I
will be happy. There are several programs on the harddrive for which there
is no equivalent Linux program. One I would like to use is Office Tutorial
for teaching "old" folks how to use a computer.
Thanks again for the correct information and assistance.

---

### Post by 3rods on 2008-07-30
> **rtrdom said:**
> Thanks a bunch. It mounted (after I typed it correctly). Now if I can
get it to open a program named Microsoft Streets and Trips I think I
will be happy. There are several programs on the harddrive for which there
is no equivalent Linux program. One I would like to use is Office Tutorial
for teaching "old" folks how to use a computer.
Thanks again for the correct information and assistance.

Check out wine, I don't use it much because I triple boot, but others speak highly of it. 

[http://www.winehq.org/]("http://www.winehq.org/")

Virtualbox might be an option too if your PC is fast enough.

[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by rtrdom on 2008-07-31
Thanks for the info. I have wine installed but didn't want to
install the Microsoft Office Tutoria on sda1 but rather on the
external sdb1. I'll try to get it to open the office thing there
first. I have to use my laptop for the classes as all of the PCs
there, even if reserved, do not permit changes of programs, for
obvious reasons. I do appreciate your assistance with ntfs-3g and
will mark this thread as solved.

---

