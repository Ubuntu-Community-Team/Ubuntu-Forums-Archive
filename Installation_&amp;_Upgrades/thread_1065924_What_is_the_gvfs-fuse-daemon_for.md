---
title: "What is the gvfs-fuse-daemon for?"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2009-02-10
I am running HH with all updates applied. I moved my system to a new machine and the only change I made in the disk partitions was to make home a separate partition. It now looks like this:
```

tommy1@tommy1-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  2.6G   11G  20% /
varrun                1.7G  100K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   48K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda3             676G   14G  629G   3% /home
gvfs-fuse-daemon       14G  2.6G   11G  20% /home/tommy1/.gvfs
tommy1@tommy1-desktop:~$ 

```

```

tommy1@tommy1-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ac3c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1    29296875    14648437+  83  Linux
/dev/sda2        29296876    37007812     3855468+  82  Linux swap / Solaris
/dev/sda3        37007813  1465149167   714070677+  83  Linux
tommy1@tommy1-desktop:~$ 

```

What is the gvfs entry for?

I do not remember having that in my old system but I have given it away so I can't check.

Thanks for any info.

---

### Post by cariboo on 2009-02-10
.gvfs has been around for quite a while, it is used for mounting network drives, when you got to Places-->Network.

Jim

---

### Post by Tom Atkins on 2009-02-10
Thanks for the information. I was just wondering.

---

