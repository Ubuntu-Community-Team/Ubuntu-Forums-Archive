---
title: "MDADM: 3-drive RAID5 wont assemble (event count off by 2)"
date: 2015-01-11
forum: Hardware
---

### Post by tylersontag on 2015-01-11
I just upgraded from 12.04 LTS to 14.04 LTS and when i tried to fire up my RAID it will not assemble... even using --force won't help, which is odd because yes the event counts are off but only by 2...

Heres some cmd output.

```
    XXXXX@XXXXXX:~$ sudo mdadm --examine /dev/sd[f,g,h]1 
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e75e7cfe:1509311f:bd0aec7f:702bf588
           Name : :TagRAID
  Creation Time : Mon Aug 29 22:09:26 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907022850 (1863.01 GiB 2000.40 GB)
     Array Size : 3907022848 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 1152 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a9c1a20d:9f0005a1:a54b977c:26624121

    Update Time : Sat Jan 10 14:11:21 2015
       Checksum : 3c0221d6 - correct
         Events : 541076

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e75e7cfe:1509311f:bd0aec7f:702bf588
           Name : :TagRAID
  Creation Time : Mon Aug 29 22:09:26 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907023730 (1863.01 GiB 2000.40 GB)
     Array Size : 3907022848 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f6c6f6c9:4ba185eb:e7bbac15:22dec345

    Update Time : Sun Jan 11 11:21:47 2015
       Checksum : 6bd4a1 - correct
         Events : 541078

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA. ('A' == active, '.' == missing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e75e7cfe:1509311f:bd0aec7f:702bf588
           Name : :TagRAID
  Creation Time : Mon Aug 29 22:09:26 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907023730 (1863.01 GiB 2000.40 GB)
     Array Size : 3907022848 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 57d63e25:a17b7770:2fc56a58:23a99531

    Update Time : Sun Jan 11 11:21:47 2015
       Checksum : f359c67 - correct
         Events : 541078

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AA. ('A' == active, '.' == missing)
xxxx@XXXXXXX:~$ sudo mdadm -A --force /dev/md0 /dev/sd[f,g,h]1
mdadm: /dev/md0 has been started with 2 drives (out of 3).
xxxx@xxxxxx:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdh1[0] sdg1[1]
      3907022848 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]

unused devices: <none>
```

Any suggestions?

---

### Post by tylersontag on 2015-01-11
UPDATE:  So i tried assembling with just F and G and got mdadm to update f's event count... but now it still won't build with this error:
```
xxx@xxxxxx:~$ sudo mdadm -A --force /dev/md0 /dev/sd[f,g,h]1
mdadm: ignoring /dev/sdh1 as it reports /dev/sdf1 as failed
mdadm: /dev/md0 has been started with 2 drives (out of 3).
```
:mad:

---

### Post by tylersontag on 2015-01-11
I think i should be OK just adding /dev/sdh1 to the array and letting it resync... it just seems like a waste of time and potentially an irrecoverable action.  What does everyone think?

---

### Post by tylersontag on 2015-01-11
Well, glad i didn't do anything rash :-)

After getting to a state described above (behavior changed from spinning up the RAID with only G,H to only F,G, caused by attempting to build the RAID with only F,G to get F's event count back in line) i simply rebooted and the drives all came up after that.

I'm running a data scrub right now (i like the new diskutil interface, and data scrub as a term to "re-sync") to make sure everything on the level.

Hopefully anyone with a similar situation to mine can get something from me talking to myself on a forum :-)   As with anything mdadm, just keep calm and don't start blowing things away.

---

