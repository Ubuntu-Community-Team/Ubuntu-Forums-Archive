---
title: "Where has 200GB of my disk space gone?"
date: 2014-06-09
forum: Hardware
---

### Post by roadhog on 2014-06-09
Hello,

I am running Ubuntu Server 12.04.4 LTS  on an old Dell machine. It runs a Samba server that serves our home. To take backups I have a 320GB USB hard drive plugged in, and backups are taken nightly.

I am very confused as I can only see 118GB of this disk. It used to be in two partitions, one around 118GB and another around 200GB. I am sure I repartitioned to give one 320GB.

This is the result of 'df -h':
```

root@DC0532:/mnt/backupdrive# df -h
Filesystem     Size  Used Avail Use% Mounted on
/dev/sda1     458G  165G  270G  38% /
udev            489M   12K  489M   1% /dev
tmpfs           100M  320K   99M   1% /run
none            5.0M   16K  5.0M   1% /run/lock
none            497M  8.0K  497M   1% /run/shm
[COLOR=#ff0000]/dev/sdb1       118G   42G   71G  38% /mnt/backupdrive[/COLOR]

```

The above makes me very confused as 'fdisk /dev/sdb' and then 'p' , 'n' , 'p' , '2' gives this!:
```

root@DC0532:/mnt/backupdrive# fdisk /dev/sdb

Command (m for help): p


Disk /dev/sdb: [COLOR=#ff0000]320.1 GB[/COLOR], 320072933376 bytes
81 heads, 63 sectors/track, 122504 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc83d7a75


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   625142447   312570200   83  Linux


Command (m for help): n
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): p
Partition number (1-4, default 2): 2
[COLOR=#ff0000]No free sectors available[/COLOR]

```

Has anybody got any ideas to what may be happening? If any more diagnostics info is needed I'm happy to provide it.

Thanks!

---

### Post by nknwn on 2014-06-09
Use **gparted** to take a look at the partition on that disk. Take care not to accidentally delete something.

---

### Post by roadhog on 2014-06-10
Thanks, I've done that over X11 and get this result! The result of 'df -h' is still the same. ??

---

### Post by spjackson on 2014-06-10
> **roadhog said:**
> I am sure I repartitioned to give one 320GB.

How did you repartition? Did you use fdisk? It looks like the partition has been resized but not the filesystem that is on that partition. You need to run resize2fs, but read the man page carefully first.

I am pretty sure that if you resize a partition using gparted, it also resizes the filesystem. So if you are not confident with using resize2fs, shrinking and re-enlarging the partition in gparted should put it right for you.

---

### Post by nknwn on 2014-06-10
I wonder if the drive has been mounted a long time and in between times you have removed one partition. Leading to incorrect reporting by **df**

Bit of a shot in the dark having read this:
[https://lists.debian.org/debian-devel/2011/12/msg00777.html](https://lists.debian.org/debian-devel/2011/12/msg00777.html)
[SIZE=3][FONT=arial]**Re: bug#10363: /etc/mtab -> /proc/mounts symlink affects df(1) output for**[/FONT][/SIZE]

---

### Post by roadhog on 2014-06-10
> **spjackson said:**
> How did you repartition? Did you use fdisk? It looks like the partition has been resized but not the filesystem that is on that partition. You need to run resize2fs, but read the man page carefully first.

I am pretty sure that if you resize a partition using gparted, it also resizes the filesystem. So if you are not confident with using resize2fs, shrinking and re-enlarging the partition in gparted should put it right for you.

I usually use fdisk to do partitioning so I think you may be right, about just resizing but not partitioning! I'll give resize2fs a try and report back.

---

### Post by roadhog on 2014-06-10
Ok, this is what I did:

```

root@DC0532:~# resize2fs -p /dev/sdb1 78142550
resize2fs 1.42 (29-Nov-2011)
Please run 'e2fsck -f /dev/sdb1' first.

root@DC0532:~# e2fsck -f /dev/sdb1
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 15/7864320 files (0.0% non-contiguous), 21271430/31457280 blocks
root@DC0532:~# resize2fs -p /dev/sdb1 78142550
resize2fs 1.42 (29-Nov-2011)
Resizing the filesystem on /dev/sdb1 to 78142550 (4k) blocks.
Begin pass 1 (max = 1425)
Extending the inode table     XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
The filesystem on /dev/sdb1 is now 78142550 blocks long.

```

And now, to confirm everything is right:
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       458G  163G  272G  38% /
udev            489M   12K  489M   1% /dev
tmpfs           100M  324K   99M   1% /run
none            5.0M   16K  5.0M   1% /run/lock
none            497M  8.0K  497M   1% /run/shm
[COLOR=#ff0000]/dev/sdb1       294G   80G  200G  29% /mnt/backupdrive[/COLOR]

```

I have got this disk space back now, so thank you all who helped.
Solved

---

