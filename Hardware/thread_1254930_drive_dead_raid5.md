---
title: "drive dead? raid5"
date: 2009-08-31
forum: Hardware
---

### Post by quantumstitch on 2009-08-31
Hi,
This weekend i finished a raid5 array with three drives. Today, I checked the array with mdadm -D and found that one of the drives has failed. This is the drive with /boot on it. I'm not sure how to recover this. I want to pull out the drive to replace, but will I have to reinstall and resync?

Luckily, I still have all the data I placed on the array on other disks and can do this. What's the best way to make sure I don't have this problem again. Can I use raid1 on /boot?

Here's some output to help. 

```
root@daphne:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Aug 29 15:15:54 2009
     Raid Level : raid5
     Array Size : 179686784 (171.36 GiB 184.00 GB)
  Used Dev Size : 89843392 (85.68 GiB 92.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Aug 31 22:12:08 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : b085de5b:cdba7b9c:73cc3a82:042ac684
         Events : 0.7932

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2

       3       8        2        -      faulty spare   /dev/sda2
You have new mail in /var/mail/root
```

```
root@daphne:~# mdadm -D /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Sat Aug 29 15:16:31 2009
     Raid Level : raid5
     Array Size : 15631104 (14.91 GiB 16.01 GB)
  Used Dev Size : 7815552 (7.45 GiB 8.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Aug 31 22:07:47 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 73a67ca7:045fd49c:2a873bdd:0c4f85c1
         Events : 0.12

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3

       3       8        3        -      faulty spare   /dev/sda3
```
```
root@daphne:~# mdadm -D /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Sat Aug 29 15:17:06 2009
     Raid Level : raid5
     Array Size : 2734760832 (2608.07 GiB 2800.40 GB)
  Used Dev Size : 1367380416 (1304.04 GiB 1400.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Mon Aug 31 22:04:22 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : c4bfb4e4:c41baa2c:918107c5:5c75ee87
         Events : 0.26786

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       20        1      active sync   /dev/sdb4
       2       8       36        2      active sync   /dev/sdc4

       3       8        4        -      faulty spare   /dev/sda4
```

```
root@daphne:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              172G   25G  148G  15% /
tmpfs                 2.9G     0  2.9G   0% /lib/init/rw
varrun                2.9G  136K  2.9G   1% /var/run
varlock               2.9G     0  2.9G   0% /var/lock
udev                  2.9G  200K  2.9G   1% /dev
tmpfs                 2.9G  396K  2.9G   1% /dev/shm
lrm                   2.9G  2.5M  2.9G   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1              92M   33M   54M  39% /boot
/dev/md2              2.6T  545G  2.1T  21% /storage
/dev/sr0              6.9G  6.9G     0 100% /media/cdrom1
```

---

### Post by quantumstitch on 2009-08-31
Ok so here's what I've done after checking mdstat,
```
root@daphne: cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sda4[3](F) sdc4[2] sdb4[1]
      2734760832 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
md0 : active raid5 sda2[3](F) sdc2[2] sdb2[1]
      179686784 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
md1 : active raid5 sda3[3](F) sdc3[2] sdb3[1]
      15631104 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
```

I marked the partitions on the failed drive as failed and removed them from the array.

```

root@daphne:  mdadm --manage /dev/md0 --fail /dev/sda2
root@daphne:  mdadm --manage /dev/md1 --fail /dev/sda3
root@daphne:  mdadm --manage /dev/md2 --fail /dev/sda4

root@daphne: mdadm --manage /dev/md0 --remove /dev/sda2
root@daphne: mdadm --manage /dev/md1 --remove /dev/sda3
root@daphne: mdadm --manage /dev/md2 --remove /dev/sda4

```

the drive is removed and it doesn't show up in mdstat expected,

```

root@daphne: cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sdc4[2] sdb4[1]
      2734760832 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
md0 : active raid5 sdc2[2] sdb2[1]
      179686784 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
md1 : active raid5 sdc3[2] sdb3[1]
      15631104 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]

```

Now I need a little guidance on what to do next. Here's what I think I should do next:
1) Shutdown machine
2) Remove bad drive and replace (Unfortunately, it involves a trip to the store maybe tomorrow.)
3) Boot with Ubuntu CD and restore /boot (How do I do this properly?)
4) Redo partitions on new drive in gparted once booted (Is there a better way to do this?)
5) Add new partitions to array
6) Enjoy a cold one while array resyncs

I need some guidance with restoring /boot. It was on /dev/sda1 which is now toast because /dev/sda failed. Can I install this on /dev/sdb1 or /dev/sdc1 somehow? Is it better to install it on a separate drive or to raid /boot? 

I also wonder if there's a simple way to just copy the partitions from the other drives to new drive.

Thanks for any help,
--stitch

---

### Post by quantumstitch on 2009-09-01
bump!

---

