---
title: "Raid :What does &quot;local to host ubuntu &quot; mean"
date: 2012-12-11
forum: Hardware
---

### Post by RED666 on 2012-12-11
Hi I've been busy learning about Linux Raid .  I've three straight forward questions...


1)Can someone explain to me what does "local to host ubuntu" mean in the following output?

Until today I got this when I looked at mdadm --detail /dev/md(x) & blkid /dev/(xxx)

```

root@ubuntu:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 0.90
  Creation Time : Sat Dec  3 18:08:49 2011
     Raid Level : raid1
     Array Size : 1953514432 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 1953514432 (1863.02 GiB 2000.40 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 127
    Persistence : Superblock is persistent

    Update Time : Tue Dec 11 06:12:45 2012
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 79607c5c:84632425:12f9938a:7c5726ef
         Events : 0.548

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1

root@ubuntu:~# blkid /dev/md127
/dev/md127: UUID="1f607c88-35f2-4387-b38a-2a4217e47a06" TYPE="xfs" 
root@ubuntu:~# blkid /dev/sdd1
/dev/sdd1: UUID="79607c5c-8463-2425-12f9-938a7c5726ef" TYPE="linux_raid_member" 
root@ubuntu:~# blkid /dev/sdb1
/dev/sdb1: UUID="79607c5c-8463-2425-12f9-938a7c5726ef" TYPE="linux_raid_member" 
root@ubuntu:~# 
root@ubuntu:~# 

```Now I see:

```

root@ubuntu:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 0.90
  Creation Time : Wed Dec 12 02:38:55 2012
     Raid Level : raid1
     Array Size : 1953514432 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 1953514432 (1863.02 GiB 2000.40 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 127
    Persistence : Superblock is persistent

    Update Time : Wed Dec 12 02:42:04 2012
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 79607c5c:84632425:e368bf24:bd0fce41 [COLOR=Red](local to host ubuntu)[/COLOR]
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
root@ubuntu:~# 
root@ubuntu:~# blkid /dev/md127
/dev/md127: UUID="1f607c88-35f2-4387-b38a-2a4217e47a06" TYPE="xfs"
root@ubuntu:~# blkid /dev/sdb1
/dev/sdb1: UUID="79607c5c-8463-2425-e368-bf24bd0fce41" TYPE="linux_raid_member"

```Another thing I noticed is in etc/mdadm.conf:

```

ARRAY /dev/md/127_0 metadata=0.90 UUID=79607c5c:84632425:12f9938a:7c5726ef

```2) What does, " _0" at the end of the name, mean?


3) How can I change manipulate the UUID for a HD or a partition (that's part of an array)?



If you Need to know more about my setup: [http://ubuntuforums.org/showthread.php?t=2089826](http://ubuntuforums.org/showthread.php?t=2089826)

---

