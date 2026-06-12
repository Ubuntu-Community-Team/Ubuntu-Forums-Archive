---
title: "Not able to access NTFS Partition."
date: 2008-07-21
forum: Hardware
---

### Post by navrddy on 2008-07-21
Hi Frnds,

i,am not able to NTFS Partition on my other Secondary disk...
Earlier i was able to access the same...Problem has cropped only recently.


I,am attaching screenshot of the same below as attachement.


PLEEZZZ HELP

---

### Post by Rocket2DMn on 2008-07-23
Hello, 
If you haven't figured this out yet, there are two ways to proceed.  If you have a windows install, you can boot into that, then safely remove the partition from there or just do a normal shutdown.  Otherwise you can force the partition to mount:
```
sudo mount -t ntfs-3g /dev/sda9 /media/SOFT -o force
```
That should reset the log file and mount the drive.  Are there actually ' ' around the SOFT?  You get the idea.

---

### Post by Milyardo on 2008-07-23
As it says in the error this drive has been marked "unclean". That usually means if you have Windows installed on that partition it wasn't shut down properly last time you were in Windows.
To fix it start up Windows and shut down properly. Its best to make sure you always shut down properly rather than force the mount.

---

