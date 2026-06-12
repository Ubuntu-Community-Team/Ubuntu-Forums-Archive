---
title: "Moving Raid Archive - fsck died with exit status 8"
date: 2008-07-11
forum: General Help
---

### Post by ihatethetv on 2008-07-11
I tried moving a 3 disk RAID5 over from one machine to another.  It booted, saw it and started checking it, it got a while through then died with the following error...I'm retyping this from notes, so there may be some typos:

/dev/md0 is mounted e2fsch: Cannot continue, aborting
       fsck died with exit status 8
    *  File system check failed

A log is at ....  /var/log/fsck/checkfs 

But that contains just the following:

cat /var/log/fsck/checkfs
Log of fsck -C3 -R -A -a
Fri Jul 11 00:50:19 2008

fsck 1.40.8 (13-Mar-2008)
/dev/md2: clean, 4407/18546688 files, 1104095/37090048 blocks
/dev/md0 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8



So what should I do here?  Some things I haven't tried....taking it back to the other machine;  Manually editting mdadm.conf;  reordering the drives on the sata channels.

Thanks,
Glen

---

### Post by CooLGeeK on 2008-07-19
Looking at the logs /dev/md0 seems to be mounted (to a directory).
Check /etc/mtab to be sure.
Unmount it (sudo umount /dev/md0) and run fsck again (sudo fsck /dev/md0).

---

### Post by fjgaude on 2008-07-19
I've done what you are trying many times without issue.

There was a case in which I had to use the old mdadm.conf file in the new installation, but usually all I did was install the OS, after that install mdadm and then:

```
sudo --assemble --scan
```

From there the new .config file is created.

Likely the UUID in the mdadm.conf file is not right.

Changing SATA slots does nothing... mdadm works with its own created UUID, and that goes for the drives within the array.

So you can get the system booted and then try what I normally do, as stated above.

Let us know how you are doing.

---

### Post by ihatethetv on 2008-07-21
Thanks for the responses.  I played around a bit and haven't quite gotten where I wanted.  The problem that I'm running into is that I don't know the UUID of the RAID5 volume and I don't know exactly what these files should look like.  

Here's my fstab.  I tried (blindly) to just add that last line onto it to get the raid5 to mount.  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=5d9d8b9e-f79c-4aaf-95bf-eba6d1073a97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/md2
UUID=6636cef2-7153-478b-beea-54b63b79161f /home           ext3    relatime        0       2
# /dev/md1
UUID=76f049e7-d657-4430-84cd-e6edb345d695 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


#raid 5 array  (ADDED THIS MANUALLY)
/dev/md0 /media/raid5 auto defaults 0 3



Here's my mdadm file:

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=0a644416:bfa75f14:efc0831c:2077c4bd
#ARRAY /dev/md1 level=raid0 num-devices=2 UUID=77bb9dd1:5b833437:2d0a54fa:717b8b46
#ARRAY /dev/md2 level=raid1 num-devices=2 UUID=1e123967:452f501b:94ba157d:4d8cda9d

ARRAY /dev/md0 level=raid5 num-devices=3 UUID=d137a5d6:bba67d0f:f1770e25:97b65a2a


# This file was auto-generated on Mon, 07 Apr 2008 03:59:37 +0000
# by mkconf $Id$


I think I commented out the three md0-2 lines, I was puzzled that they were there at all because I wasn't using any md devices yet and I noticed md0 would conflict with the md0 device I was adding to the system.  This was just me taking a stab at it.  

Anyway as it stands now I did the command

sudo mdadm --assemble --scan

and it doesn't give any feedback, which is better than an error I guess...but then in the /media/raid5 mountpoint there's the same data as my / directory.   I guess it just mounted the /device there too.

Sorry I'm a bit clueless here.  Any suggestions?

---

### Post by CooLGeeK on 2008-07-21
Can you try checking each partition if they are part of a RAID array?
For example, checking partition /dev/sdc1 ...
```
sudo mdadm --examine /dev/sdc1
```

Try doing the check for all your partitions.
You can see all your partition by typing ...
```
cat /proc/partitions
```

Try writing down each partition which is part of a raid (md) array.
Then try reconstructing it by hand.

Please try to examine each disk also (i.e. /dev/sdb).

Please show the output of the above commands.


NOTE:
Also, you may find this information useful:
When I was first experimenting with Linux software raid (mdadm) I accidentally assembled the disk instead of the raid partition inside the disk. This resulted in an md superblock written BOTH on the raid partition AND the disk itself.
After that mdadm keeps on automatically creating two (2) md device when it fact there is only one.
What I deed was to forcibly assemble the raid array from the raid partitions (i.e. /dev/sdb1, /dev/sdc1, /dev/sde1) and backup the data inside the raid array for safety.
Then I used the --zero-superblock on the device (/dev/sdb).

---

### Post by ihatethetv on 2008-09-01
Sorry for the slow response, been busy...

CoolGeek, thanks for the info.  I am examining now...here's the output

glen@g-livingroom:~$ sudo mdadm --examine /dev/sd* > mdadm_sd_all
mdadm: No md superblock detected on /dev/sda.
mdadm: No md superblock detected on /dev/sda1.
mdadm: No md superblock detected on /dev/sdb.
mdadm: No md superblock detected on /dev/sdc.
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdd.
mdadm: No md superblock detected on /dev/sde.

The file 'mdadm_sd_all' contains:
glen@g-livingroom:~$ cat mdadm_sd_all
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d137a5d6:bba67d0f:f1770e25:97b65a2a
  Creation Time : Fri May 16 22:54:32 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jul  6 14:31:13 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 6cf375f9 - correct
         Events : 0.36

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0a644416:bfa75f14:efc0831c:2077c4bd
  Creation Time : Sun Apr  6 22:51:08 2008
     Raid Level : raid1
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
     Array Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Aug 31 23:34:43 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 14b95050 - correct
         Events : 0.11


      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       49        1      active sync   /dev/sdd1
/dev/sdd2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 77bb9dd1:5b833437:2d0a54fa:717b8b46
  Creation Time : Sun Apr  6 22:51:26 2008
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Sun Apr  6 22:51:26 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : aae4367a - correct
         Events : 0.1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync

   0     0       8        2        0      active sync
   1     1       8       18        1      active sync
/dev/sdd3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1e123967:452f501b:94ba157d:4d8cda9d
  Creation Time : Sun Apr  6 22:51:34 2008
     Raid Level : raid1
  Used Dev Size : 148360192 (141.49 GiB 151.92 GB)
     Array Size : 148360192 (141.49 GiB 151.92 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2

    Update Time : Sun Aug 31 23:34:43 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 8840a110 - correct
         Events : 0.17


      Number   Major   Minor   RaidDevice State
this     1       8       51        1      active sync   /dev/sdd3

   0     0       8       67        0      active sync   /dev/sde3
   1     1       8       51        1      active sync   /dev/sdd3
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0a644416:bfa75f14:efc0831c:2077c4bd
  Creation Time : Sun Apr  6 22:51:08 2008
     Raid Level : raid1
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
     Array Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Aug 31 23:34:43 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 14b9505e - correct
         Events : 0.11


      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       49        1      active sync   /dev/sdd1
/dev/sde2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 77bb9dd1:5b833437:2d0a54fa:717b8b46
  Creation Time : Sun Apr  6 22:51:26 2008
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Sun Apr  6 22:51:26 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : aae43668 - correct
         Events : 0.1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync

   0     0       8        2        0      active sync
   1     1       8       18        1      active sync
/dev/sde3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1e123967:452f501b:94ba157d:4d8cda9d
  Creation Time : Sun Apr  6 22:51:34 2008
     Raid Level : raid1
  Used Dev Size : 148360192 (141.49 GiB 151.92 GB)
     Array Size : 148360192 (141.49 GiB 151.92 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2

    Update Time : Sun Aug 31 23:34:43 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 8840a12e - correct
         Events : 0.16


      Number   Major   Minor   RaidDevice State
this     0       8       67        0      active sync   /dev/sde3

   0     0       8       67        0      active sync   /dev/sde3
   1     1       8       51        1      active sync   /dev/sdd3

---

### Post by ihatethetv on 2008-09-01
Looking at it...

/dev/sdb1:
     Raid Level : raid5
--
/dev/sdd1:
     Raid Level : raid1
--
/dev/sdd2:
     Raid Level : raid0
--
/dev/sdd3:
     Raid Level : raid1
--
/dev/sde1:
     Raid Level : raid1
--
/dev/sde2:
     Raid Level : raid0
--
/dev/sde3:
     Raid Level : raid1


...I think I was trying to be too fancy.  I was making one big raid5 partition and a raid 1 for the OS and then a raid 0 for the tmp.  I've forgotten what I had now so I'm going to just go ahead and wipe it and start over.  Luckily I hadn't yet brought this into production with real data...because I didn't trust it...so I can do this.

Thanks for all the help.

-Glen

---

