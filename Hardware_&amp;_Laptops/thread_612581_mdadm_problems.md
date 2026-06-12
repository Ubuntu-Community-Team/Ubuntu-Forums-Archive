---
title: "mdadm problems"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by Soggy Chips on 2007-11-14
Hi guys,

heres a nub plead for help, I have a wee mdadm raid5 array of 5 x 400gig drives on my Ubuntu box. Long story short the array is playing up. Any assistance would be greatly appreciated

Some things think the drives are down and some things don't. Device 3 appears to be stuffed in most of the reports however when I try and start array it does this
```
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
```

mdadm --examine /dev/sda yeilds this 
```
 /dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e10e5fd1:1584c8fe:f7f338c5:ef182b41
  Creation Time : Fri Feb  9 19:28:20 2007
     Raid Level : raid5
    Device Size : 390711296 (372.61 GiB 400.09 GB)
     Array Size : 1562845184 (1490.45 GiB 1600.35 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Mon Aug 20 06:26:59 2007
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2ac277c4 - correct
         Events : 0.792890

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     3       8        0        3      active sync   /dev/sda

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8        0        3      active sync   /dev/sda
   4     4       8       64        4      active sync   /dev/sde

```

sdb says this
```
      Number   Major   Minor   RaidDevice State
this     4       8       48        4      active sync   /dev/sdd

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       0        0        3      faulty removed
   4     4       8       48        4      active sync   /dev/sdd

```
sdc says this
```
      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       0        0        3      faulty removed
   4     4       8       48        4      active sync   /dev/sdd

```
sdd says this 
```
      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
```
sde  says this
```
      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed

```

so not only do so things seem to think there are no failed devices or one, some think that there are three. Also why when I examine sde does it think it is sda?

I have tried removing a drive from the array so I can try re-add it but it says this

```
mdadm: cannot get array info for /dev/md0 
```
Any help I am very grateful for as I simply want to bring it up so I can migrate 1.6tb of data to a hw array. That and the missus is going to hate me if I've lost all her data

---

