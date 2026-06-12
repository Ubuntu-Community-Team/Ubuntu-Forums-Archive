---
title: "Will the following dual boot system cause applications to run slowly?"
date: 2009-01-18
forum: Hardware
---

### Post by ubantuwannabe on 2009-01-18
hi,

Will the following dual boot system cause applications to run slowly?

/dev/sda1   *           1        1031     8281476    7  HPFS/NTFS
/dev/sda2            1032        3825    22442805    f  W95 Ext'd (LBA)
/dev/sda5            2296        3825    12289693+   7  HPFS/NTFS
/dev/sda6            1032        2235     9671067   83  Linux
/dev/sda7            2236        2295      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order
chunhung@chunhung-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.1G  2.6G  6.1G  30% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  260K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-9-generic/volatile

thanks

---

### Post by ibutho on 2009-01-18
I've never experienced multi boot systems slow down applications, so I doubt that your set up will cause applications to slow down.

---

### Post by sandip26879 on 2009-01-18
Partition has nothing to do with slowdowns.

---

### Post by steveneddy on 2009-01-18
> **sandip26879 said:**
> partition has nothing to do with slowdowns.

+1

---

