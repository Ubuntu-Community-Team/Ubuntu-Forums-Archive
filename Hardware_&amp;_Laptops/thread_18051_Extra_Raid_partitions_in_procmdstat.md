---
title: "Extra Raid partitions in /proc/mdstat"
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by phill on 2005-03-04
I have a very weird problem.  After a little bit of messing around I got my main partition mirrored as Raid 1 with a spare and then used the remaining space to create two Raid 5 arrays with spares too.  My system looks good:

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.6G  1.8G  7.8G  19% /
tmpfs                 505M     0  505M   0% /dev/shm
/dev/md1               86G  5.1G   81G   6% /home
/dev/md2              191G   13G  179G   7% /backup

However when I view /proc/mdstat two additional raid partitions are there that I did not create:

```
Personalities : [raid1] [raid5]
read_ahead 1024 sectors
md4 : active raid5 ide/host0/bus0/target0/lun0/part4[0] ide/host0/bus0/target1/lun0/part4[2]
      2586240 blocks level 5, 32k chunk, algorithm 2 [3/2] [U_U]

md3 : active raid1 ide/host0/bus1/target1/lun0/part1[1]
      10000320 blocks [2/1] [_U]

md2 : active raid5 ide/host0/bus1/target1/lun0/part3[2] ide/host0/bus0/target1/lun0/part3[1] ide/host0/bus0/target0/lun0/part3[0]
      199992960 blocks level 5, 32k chunk, algorithm 2 [3/3] [UUU]

md1 : active raid5 ide/host0/bus1/target1/lun0/part2[2] ide/host0/bus0/target1/lun0/part2[1] ide/host0/bus0/target0/lun0/part2[0]
      89995904 blocks level 5, 32k chunk, algorithm 2 [3/3] [UUU]

md0 : active raid1 ide/host0/bus0/target0/lun0/part1[0] ide/host0/bus0/target1/lun0/part1[1]
      10000320 blocks [2/2] [UU]

unused devices: <none>

```

This is very wierd as I've only created three partitions (md0, md1 and md2) and my raidtab is as follows:

```
raiddev /dev/md0
        raid-level      1
        nr-raid-disks   2
        nr-spare-disks  1
        persistent-superblock 1
        device          /dev/hda1
        raid-disk       0
        device          /dev/hdb1
        raid-disk       1
        device          /dev/hdd1
        spare-disk      0


raiddev /dev/md1
        raid-level      5
        nr-raid-disks   3
        nr-spare-disks  1
        persistent-superblock 1
        parity-algorithm        left-symmetric
        chunk-size      32
        device          /dev/hda2
        raid-disk       0
        device          /dev/hdb2
        raid-disk       1
        device          /dev/hdd2
        raid-disk       2
        device          /dev/hdc2
        spare-disk      0


raiddev /dev/md2
        raid-level      5
        nr-raid-disks   3
        nr-spare-disks  1
        persistent-superblock 1
        parity-algorithm        left-symmetric
        chunk-size      32
        device          /dev/hda3
        raid-disk       0
        device          /dev/hdb3
        raid-disk       1
        device          /dev/hdd3
        raid-disk       2
        device          /dev/hdc3
        spare-disk      0

```


Can anyone explain where these two extra partitions have come from?  I can stop both md3 and md4 using raidstop which freaks me out even more...  :confused:

---

