---
title: "Mdadm raid 5 add drive"
date: 2008-11-03
forum: General Help
---

### Post by tb52726 on 2008-11-03
Hi this is a simple question and i'm sure there is a simple answear but i'm just not finding it.

I created a Raid 5 array with 4x500gb no hot spare all used to give array size 1.5tb, its all working.

Now i want to test the raid 5, so i power off the system and pull one of the drives power then restart.

Raid is still avaiable now

- Should the array have booted without any warning?

I power off, connect the drive back and boot the array it is still active

i run mdadm --examine /dev/sdd1

> /dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d676c305:563cfb40:e368bf24:bd0fce41
  Creation Time : Fri Oct 17 19:20:40 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Oct 19 19:48:19 2008
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 256800fa - correct
         Events : 0.7

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1


i then run mdadm --examine /dev/sda1

> /dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d676c305:563cfb40:e368bf24:bd0fce41
  Creation Time : Fri Oct 17 19:20:40 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Oct 19 23:08:09 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 25682ff3 - correct
         Events : 0.42

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed


i try mdadm --examine /dev/sdb1 and mdadm --examine /dev/sdc1 they all say /dev/sdd1 is faulty removed but when i run mdadm --examine /dev/sdd1 it says active sync?

- so is the drive faulty or active? If i pull another drive would i kill the array?

---

### Post by tb52726 on 2008-11-04
well looks like i gotthe array rebuilding need to runthe assemble mode first then the add command.

Still reckon it should not have mounted a degraded array but at least i know it was working

now just have to wait 9 hours for the rebuild....

---

### Post by fjgaude on 2008-11-04
A raid5 array mounts and runs, but with degraded performance, okay with one drive missing.

You use the -D command to see the health of the array.

And use this command to watch an array re-build:

```
sudo watch cat /proc/mdstat
```

Here's some stuff I used to learn from:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Good luck and let us know how you are doing.

---

### Post by psusi on 2008-11-05
Yea, use -D to see the status of the array, rather than examining each drive.  The faulty drive does not know it was faulty and removed because it was not connected at the time.

---

