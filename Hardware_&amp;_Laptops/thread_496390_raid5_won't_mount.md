---
title: "raid5 won't mount"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by LenzM on 2007-07-09
My computer froze and I had to do a hard reboot.  Since then my raid array won't start up.  It looks like one of my hard drives failed, but gparted recognizes the partition.  I can't find a clear answer on what to do next.  

I would appreciate any help.

I'm attaching whatever relevant information that I can think of.

```

$ sudo mount /mnt/raid/
mount: /dev/md0: can't read superblock

```

Here is the applicable part of syslog:
```

Jul  9 01:08:35 localhost kernel: [17180495.316000] md: md0 stopped.
Jul  9 01:08:35 localhost kernel: [17180495.316000] md: unbind<sda1>
Jul  9 01:08:35 localhost kernel: [17180495.316000] md: export_rdev(sda1)
Jul  9 01:08:35 localhost kernel: [17180495.316000] md: unbind<sdd1>
Jul  9 01:08:35 localhost kernel: [17180495.316000] md: export_rdev(sdd1)
Jul  9 01:08:35 localhost kernel: [17180495.316000] md: unbind<sdb1>
Jul  9 01:08:35 localhost kernel: [17180495.316000] md: export_rdev(sdb1)
Jul  9 01:09:01 localhost /USR/SBIN/CRON[17707]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print
0 | xargs -r -0 rm)
Jul  9 01:09:34 localhost kernel: [17180554.452000] md: md0 stopped.
Jul  9 01:09:34 localhost kernel: [17180554.520000] md: bind<sdb1>
Jul  9 01:09:34 localhost kernel: [17180554.524000] md: bind<sdc1>
Jul  9 01:09:34 localhost kernel: [17180554.524000] md: bind<sdd1>
Jul  9 01:09:34 localhost kernel: [17180554.524000] md: bind<sda1>
Jul  9 01:09:34 localhost kernel: [17180554.524000] md: kicking non-fresh sdc1 from array!
Jul  9 01:09:34 localhost kernel: [17180554.524000] md: unbind<sdc1>
Jul  9 01:09:34 localhost kernel: [17180554.524000] md: export_rdev(sdc1)
Jul  9 01:09:34 localhost kernel: [17180554.524000] md: md0: raid array is not clean -- starting background reconstruction
Jul  9 01:09:34 localhost kernel: [17180554.588000] raid5: device sda1 operational as raid disk 0
Jul  9 01:09:34 localhost kernel: [17180554.588000] raid5: device sdd1 operational as raid disk 3
Jul  9 01:09:34 localhost kernel: [17180554.588000] raid5: device sdb1 operational as raid disk 1
Jul  9 01:09:34 localhost kernel: [17180554.588000] raid5: cannot start dirty degraded array for md0
Jul  9 01:09:34 localhost kernel: [17180554.588000] RAID5 conf printout:
Jul  9 01:09:34 localhost kernel: [17180554.588000]  --- rd:4 wd:3 fd:1
Jul  9 01:09:34 localhost kernel: [17180554.588000]  disk 0, o:1, dev:sda1
Jul  9 01:09:34 localhost kernel: [17180554.588000]  disk 1, o:1, dev:sdb1
Jul  9 01:09:34 localhost kernel: [17180554.588000]  disk 3, o:1, dev:sdd1
Jul  9 01:09:34 localhost kernel: [17180554.588000] raid5: failed to run raid set md0
Jul  9 01:09:34 localhost kernel: [17180554.588000] md: pers->run() failed ...

```

```

$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Apr 15 18:17:26 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul  8 23:58:33 2007
          State : active, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3909883c:c305d98c:0f60eccb:78b4bc11
         Events : 0.3332721

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       8       49        3      active sync   /dev/sdd1

```

```

$ cat /etc/mdadm/mdadm.conf 
DEVICE partitions
ARRAY /dev/.static/dev/md0 level=raid5 num-devices=4 UUID=3909883c:c305d98c:0f60eccb:78b4bc11
   spares=1

```

```

$ cat /proc/mdstat 
Personalities : [raid5] [raid4] 
md0 : inactive sda1[0] sdd1[3] sdb1[1]
      1465151808 blocks
       
unused devices: <none>

```

---

### Post by LenzM on 2007-07-09
I tried running fsck:

```

mike@oompahland:~$ sudo fsck /dev/md0
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

mike@oompahland:~$ sudo e2fsck -b 8193 /dev/md0
e2fsck 1.39 (29-May-2006)
e2fsck: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

