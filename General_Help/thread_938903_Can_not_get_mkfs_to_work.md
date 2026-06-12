---
title: "Can not get mkfs to work"
date: 2008-10-05
forum: General Help
---

### Post by lsutiger on 2008-10-05
Output of df:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9690316   4023688   5178256  44% /
varrun                  972052       244    971808   1% /var/run
varlock                 972052         0    972052   0% /var/lock
udev                    972052        52    972000   1% /dev
devshm                  972052       400    971652   1% /dev/shm
lrm                     972052     39760    932292   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2            180733740  89106696  84282448  52% /home
gvfs-fuse-daemon       9690316   4023688   5178256  44% /home/complexity/.gvfs
/dev/sdb1               976064    946544     29520  97% /media/KINGSTON

```

output of sudo mkfs -V -t fat32 /dev/sdb1
```
mkfs (util-linux-ng 2.13.1)
mkfs.fat32 /dev/sdb1 
mkfs.fat32: No such file or directory


```

Huh???

---

### Post by Rocket2DMn on 2008-10-05
The correct command is
```
mkfs.vfat /dev/sdb1
```
(or even mkdosfs)
Most users prefer to use graphical programs for doing partitioning, like GParted which is available on the LiveCD and in the repositories.
So, if you'd like:
```
sudo apt-get install gparted
```
Then access it from System->Administration->Partition Editor

---

### Post by lsutiger on 2008-10-05
Thanx!
I like the cli a bit more for small tasks like this.

---

### Post by Rocket2DMn on 2008-10-05
+1 for terminal interface, I like to suggest graphical alternatives as they tend to be more user friendly, esp. for beginners (which is who Ubuntu caters to).

---

