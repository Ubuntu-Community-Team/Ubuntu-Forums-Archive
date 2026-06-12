---
title: "RAID5 4 drives multiple out of sync?"
date: 2023-07-04
forum: Hardware
---

### Post by chris.arney on 2023-07-04
It looks like I got my drives out of sync... I was trying to upgrade my 4TB drives to 10TB, but at this point, I'd rather just get my current 4x4TB RAID 5 back running again. I'm ok if I lose a little bit of data... Important things are backed up, but it would take an eternity to restore all 12TB. How can I get my current setup back and running?

```
:~$ sudo mdadm --examine /dev/sd[b-e]1 | grep 'dev\|Events'
/dev/sdb1:
         Events : 29259
   Device Role : Active device 0
/dev/sdc1:
         Events : 29256
   Device Role : Active device 1
/dev/sdd1:
         Events : 29253
   Device Role : Active device 2
/dev/sde1:
         Events : 29259
   Device Role : Active device 3
```


```
:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdd1[2](S) sdc1[1](S) sde1[4](S) sdb1[0](S)
      15627541790 blocks super 1.2
       
unused devices: <none>
```

Here's the full output from --examine:

```
:~$ sudo mdadm --examine /dev/sd[b-e]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e73fc900:63b29dac:59abec6d:a9ed6e02
           Name : ubuntu1:0  (local to host ubuntu1)
  Creation Time : Mon Feb  1 14:28:44 2021
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 11720655360 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=655 sectors
          State : clean
    Device UUID : fc1484e3:9dd42927:050c3334:510f959c

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jul  3 22:53:17 2023
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : e373a9f0 - correct
         Events : 29259

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e73fc900:63b29dac:59abec6d:a9ed6e02
           Name : ubuntu1:0  (local to host ubuntu1)
  Creation Time : Mon Feb  1 14:28:44 2021
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 11720655360 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=655 sectors
          State : clean
    Device UUID : ef83a829:fb3b15d5:a8efbc06:6e1ce6ff

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jul  3 22:48:11 2023
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : d606fcd - correct
         Events : 29256

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e73fc900:63b29dac:59abec6d:a9ed6e02
           Name : ubuntu1:0  (local to host ubuntu1)
  Creation Time : Mon Feb  1 14:28:44 2021
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 11720655360 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=655 sectors
          State : clean
    Device UUID : 33674b45:e1670e28:6357bac7:54feeea5

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jul  3 22:45:08 2023
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : e301c7e1 - correct
         Events : 29253

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e73fc900:63b29dac:59abec6d:a9ed6e02
           Name : ubuntu1:0  (local to host ubuntu1)
  Creation Time : Mon Feb  1 14:28:44 2021
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 11720655360 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=655 sectors
          State : clean
    Device UUID : effdc94e:e1c09065:676782d9:11099abc

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jul  3 22:53:17 2023
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 5274d44e - correct
         Events : 29259

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : A..A ('A' == active, '.' == missing, 'R' == replacing)

```

---

### Post by chris.arney on 2023-07-09
I found this command below fixed the syncing issue. I mostly understand it, but also don't know what I don't know about this.

One learning was that I didn't have to have the /dev/sdx1 drives in any specific order. As a software RAID on Linux, it reads the identifying information from the drives, and uses that info to assemble it. I'm just passing which devices to consider.

mdadm --assemble --run --force --update=resync /dev/md127 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

---

