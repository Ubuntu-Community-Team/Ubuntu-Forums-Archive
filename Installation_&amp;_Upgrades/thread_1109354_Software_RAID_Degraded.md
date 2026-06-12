---
title: "Software RAID Degraded"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by SuperMe79 on 2009-03-28
I have installed ubuntu 8.10 server. I configured software raid with 3 raid1 devices

```

sda1 + sdb1 = md0 swap
sda2 + sdb2 = md1 ext3 /
sda3 + sdb3 = md2 ext3 /data

```

I have booted the server and discovered that the software raid is not working

```

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 dm-2[0]
      163083776 blocks [2/1] [U_]

md1 : active raid1 dm-3[0]
      78123968 blocks [2/1] [U_]

md0 : active raid1 dm-1[0]
      3903680 blocks [2/1] [U_]

unused devices: <none>

```

mdadm reports a degraded array. All three raid arrays report the same.

```

# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Mar 28 20:45:44 2009
     Raid Level : raid1
     Array Size : 3903680 (3.72 GiB 4.00 GB)
  Used Dev Size : 3903680 (3.72 GiB 4.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Mar 28 21:19:09 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : e0514f53:06fa9306:fa1c93f5:ba501f28
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0     254        1        0      active sync   /dev/block/254:1
       1       0        0        1      removed

```

```

# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e0514f53:06fa9306:fa1c93f5:ba501f28
  Creation Time : Sat Mar 28 20:45:44 2009
     Raid Level : raid1
  Used Dev Size : 3903680 (3.72 GiB 4.00 GB)
     Array Size : 3903680 (3.72 GiB 4.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Sat Mar 28 21:27:01 2009
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : d8bc9a6d - correct
         Events : 18


      Number   Major   Minor   RaidDevice State
this     0     254        1        0      active sync   /dev/block/254:1

   0     0     254        1        0      active sync   /dev/block/254:1
   1     1       0        0        1      faulty removed

```

```

# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e0514f53:06fa9306:fa1c93f5:ba501f28
  Creation Time : Sat Mar 28 20:45:44 2009
     Raid Level : raid1
  Used Dev Size : 3903680 (3.72 GiB 4.00 GB)
     Array Size : 3903680 (3.72 GiB 4.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Sat Mar 28 21:27:01 2009
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : d8bc9a6d - correct
         Events : 18


      Number   Major   Minor   RaidDevice State
this     0     254        1        0      active sync   /dev/block/254:1

   0     0     254        1        0      active sync   /dev/block/254:1
   1     1       0        0        1      faulty removed

```

```

# cat /etc/mdadm/mdadm.conf
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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e0514f53:06fa9306:fa1c93f5:ba501f28
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=1168b618:0b03c90a:0531a492:831787b1
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=59828836:a271882f:72976378:e41c5711

# This file was auto-generated on Sat, 28 Mar 2009 20:51:49 +0000
# by mkconf $Id$

```

This is what I have tried to resolve this problem

[LIST]
[*]Disabling / enabling the fakeraid support on my motherboard
[*]Editing /etc/mdadm/mdadm.conf and specifying that only /dev/sd[ab]* should be checked
[*]Using mdadm /dev/md0 -r /dev/sd[ab]1 and corresponding add command to remove / add the discs from the array
[/LIST]

None of this has worked. My array is still reported as degraded. Any ideas would be greatly appreciated.

This post may be of similar ilk

[http://ubuntuforums.org/showthread.php?t=917675&highlight=degraded+software+raid]("http://ubuntuforums.org/showthread.php?t=917675&highlight=degraded+software+raid")

---

### Post by combatwombat_nz on 2009-03-28
Try replacing your SATA cabling. Dodgy/cheap cables cause stupid errors like missing drives.

---

### Post by SuperMe79 on 2009-03-29
Thanks for the suggestion. Unfortunately this isn't the problem in my case. The hardware including cables are fine. I know this because before I installed ubuntu the hardware was running a gentoo server with software raid configured and working fine. The ubuntu kernel is newer than the gentoo kernel. I installed the gentoo system about 3 years ago using the kernel that was current at that time.

---

### Post by SuperMe79 on 2009-03-30
Unfortunately I still haven't been able to resolve this problem. Please help.

---

### Post by SuperMe79 on 2009-04-03
Seems like no-one is going to help me with this issue. Very disappointing.

---

### Post by ronparent on 2009-04-03
Have you tried posting to the Server Platforms forum? The people who populate that forum may be more knowledgable of mdadm protocols and associated problems. Although I myself have configured both raid0 and raid1 systems I never progress past dmraid to get them reconized in my ubuntu installs. Someone more knowledgeble might be able to make more sense of you original posting.

---

### Post by SuperMe79 on 2009-04-05
Problem solved. I abandoned Ubuntu and installed Gentoo instead.

---

### Post by ziegi on 2009-04-13
I just faced the same problem!
The solution is to uninstall the dmraid package
just using mdadm works fine

---

