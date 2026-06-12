---
title: "How to recover disc space"
date: 2009-04-17
forum: Hardware
---

### Post by norm.h on 2009-04-17
I must have made a mistake with partitioning when installing Ubuntu over Fedora.
I know my disc is 20GB, as fdisk shows, but only 8.4 GB seems to be seen.
How do I recover the rest of the space?

compaq@compaq-laptop:~$ sudo fdisk -l
[sudo] password for compaq: 

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e5a0e59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1170     9397993+  83  Linux
/dev/sda2            2284        2432     1196842+   5  Extended
/dev/sda3   *        1171        2283     8940172+  83  Linux
/dev/sda5            2340        2432      746991   82  Linux swap / Solaris
/dev/sda6            2284        2339      449757   82  Linux swap / Solaris
Partition table entries are not in disk order

compaq@compaq-laptop:~$ sudo df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda3     ext3    8.4G  2.9G  5.1G  37% /
varrun       tmpfs    125M  100K  125M   1% /var/run
varlock      tmpfs    125M     0  125M   0% /var/lock
udev         tmpfs    125M   60K  125M   1% /dev
devshm       tmpfs    125M   12K  125M   1% /dev/shm
compaq@compaq-laptop:~$ 

norm

---

### Post by drs305 on 2009-04-17
norm,

I just wrote a guide on lost disk space. Your situation may be different as it could be a partitioning error but the guide is pretty extensive. You can go directly to Sections 6 or 8 to get right to the solutions and read the rest if you get stumped. #6g deals with cloned partitions if you copied a partition into the old system partition.

[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by HankB on 2009-04-17
Hi Norm,
It looks like some errors when you partitioned. I see two Linux partitions about the same size:

```
/dev/sda1   1    1170 9397993+ 83 Linux
/dev/sda3 * 1171 2283 8940172+ 83 Linux
```

df shows /dev/sda3 in use.

and likewise two swap partitions:
```
/dev/sda5   2340 2432 746991   82 Linux swap / Solaris
/dev/sda6   2284 2339 449757   82 Linux swap / Solaris
```
(You can benefit from multiple swap partitions, but not on the same drive.)

You can have a go with sorting this out using gparted. It has some capabilities to rearrange, grow and shrink partitions. You would almost certainly have to do this from a live CD. Unless you've already got a lot of time invested in getting this set up, it might be about as quick to just redo the install and get the partitioning right.

You could also see if you could live with what you have here by putting your home directory in /dev/sda1. At the moment, I'm using only 5.9 GB of my root partition with 1760 packages installed (/home is on a separate partition.) Unless you plan to install a *lot* of stuff, 8.4 GB should be more than enough. So that might provide a workable solution. You should still consider coalescing the two swap drives or deleting one and growing an adjacent partition into the space.

HTH,
hank

---

### Post by norm.h on 2009-04-17
Thanks to drs305 and HankB for your interest and replies.
Now I've got something to think about!
norm

---

