---
title: "RAID 5 array refuses to reshape after &quot;grow&quot; command"
date: 2013-10-24
forum: Hardware
---

### Post by danBhentschel on 2013-10-24
I currently have a 14 TB RAID 5 array created with the following command:

```
mdadm --create /dev/md1 --metadata=1.2 --level=5 --chunk=8m --raid-devices=n /dev/sdXX /dev/sdXX ...
```

Sorry that I don't have the exact command. The array was created a couple of years ago, I believe originally with 4 devices, and has already been grown once or twice. Right now, it has six 3 TB drives in the array. I have purchased a new 3 TB drive, and am attempting to add it into the array. Here are the commands executed:

```
mdadm --add /dev/md1 /dev/sdg2
mdadm --grow /dev/md1 --raid-devices=7
```

Almost immediately after executing the second command, the content of /proc/mdstat is as follows:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]md1 : active raid5 sdg2[6] sdh[5] sda2[4] sdf2[0] sdb2[2] sdd2[1] sde2[3]
      14650654720 blocks super 1.2 level 5, 8192k chunk, algorithm 2 [7/7] [UUUUUUU]
      [>....................]  reshape =  0.0% (8192/2930130944) finish=761446338.7min speed=0K/sec


unused devices: <none>
```

Notice that it gets just 8192 units (blocks?) into the reshape (1 x chunk size), and then stalls. After sitting for a couple of days now, /proc/mdstat still looks *exactly* as shown above. No change. It's still stuck at 8192. A look at "top" shows:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 3014 root      20   0 70648  56m  332 R   99  0.4   2123:24 mdadm
  390 root      20   0     0    0    0 S   40  0.0 850:27.26 md1_raid5
 3013 root      20   0     0    0    0 S   10  0.0 215:26.79 md1_reshape



```

The system certainly thinks that it's doing something. I am now on my third attempt at this. Each time, the result has been the same. If I reboot the machine, then the array comes up as broken. I don't remember the exact error message that it gives me, but a paraphrase is that I interrupted the reshape before passing the critical section. I have been able to recover from this only by recreating the original 6-device array with the --assume-clean option.

Here is my kernel info:

```
Linux raidman 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

The output of mdadm --detail:

```
/dev/md1:
        Version : 1.2
  Creation Time : Tue Oct 22 20:14:20 2013
     Raid Level : raid5
     Array Size : 14650654720 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 2930130944 (2794.39 GiB 3000.45 GB)
   Raid Devices : 7
  Total Devices : 7
    Persistence : Superblock is persistent


    Update Time : Thu Oct 24 12:58:09 2013
          State : clean, reshaping
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 8192K


 Reshape Status : 0% complete
  Delta Devices : 1, (6->7)


           Name : (none):1
           UUID : 62a4488b:1cc65acc:fa645bd4:32b98e5b
         Events : 16


    Number   Major   Minor   RaidDevice State
       0       8       82        0      active sync   /dev/sdf2
       1       8       50        1      active sync   /dev/sdd2
       2       8       18        2      active sync   /dev/sdb2
       3       8       66        3      active sync   /dev/sde2
       4       8        2        4      active sync   /dev/sda2
       5       8      112        5      active sync   /dev/sdh
       6       8       98        6      active sync   /dev/sdg2

```

Relevant portions of dmesg:

```

[    1.660874] md: linear personality registered for level -1
[    1.664086] md: multipath personality registered for level -4
[    1.665224] md: raid0 personality registered for level 0
[    1.666492] md: raid1 personality registered for level 1
[    1.772223] md: bind<sde2>
[    1.796549] md: bind<sdd2>
[    1.805198] md: bind<sdb2>
[    1.816434] md: bind<sdf2>
[    1.868596] md: bind<sda2>
[    1.910839] md: raid6 personality registered for level 6
[    1.910841] md: raid5 personality registered for level 5
[    1.910843] md: raid4 personality registered for level 4
[    1.914238] md: raid10 personality registered for level 10
[    6.916469] md: bind<sdh>
[    6.919287] md/raid:md1: device sdh operational as raid disk 5
[    6.919289] md/raid:md1: device sda2 operational as raid disk 4
[    6.919291] md/raid:md1: device sdf2 operational as raid disk 0
[    6.919292] md/raid:md1: device sdb2 operational as raid disk 2
[    6.919293] md/raid:md1: device sdd2 operational as raid disk 1
[    6.919294] md/raid:md1: device sde2 operational as raid disk 3
[    6.919624] md/raid:md1: allocated 6450kB
[    6.919777] md/raid:md1: raid level 5 active with 6 out of 6 devices, algorithm 2
[    6.919808] md1: detected capacity change from 0 to 15002270433280
[    6.923722]  md1: unknown partition table
[    7.613648] XFS (md1): Mounting Filesystem
[    7.998905] XFS (md1): Ending clean mount
[   56.913734] md: bind<sdg2>
[  106.463293] md: reshape of RAID array md1
[  106.463296] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[  106.463298] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for reshape.
[  106.463309] md: using 128k window, over a total of 2930130944k.

```

---

### Post by danBhentschel on 2013-11-18
I was eventually able to get this to work. The only things that I changed that I believe were relevant are:

1) I enabled swap on the machine. I had not setup swap when I last installed the OS because my main drive is an SSD, and I figured that with 16 GB of RAM, it wasn't all that necessary. I think this is less likely to be the solution to the problem because I saw no indication of rampant memory usage while mdadm was running (or failing to run) before.

2) I reshaped the 6-drive array to have a chunk size of 1024K instead of 8192K. I don't remember what madness drove me to pick 8192K in the first place, but it is quite out-of-the-ordinary, and it occurred to me that it might fall over a boundary condition that is not tested too often: reshaping an array with chunk size of 8192K to a size exceeding 16TB. The command I used to reshape the array:

```
mdadm --grow /dev/md1 --verbose --backup-file=/root/mdadm.backup --chunk=1024
```

This reshape succeeded after chugging away for about 5 days. I then re-executed my previous reshape command:

```
mdam --add /dev/md1 /dev/sdg2
mdadm --grow /dev/md1 --verbose --backup-file=/root/mdadm.backup --raid-devices=7
```

At the time of this posting, it hasn't completed yet, but after about 9 hours, it is at 8.5% complete, as opposed to before, I let the reshape run for more that 3 weeks at one point, and it never got further than 0.0%, always stuck on the first 8192 blocks.

The chunk size seems to me to be the most likely point of failure, but I can say with certainty that I have added drives to this same array (with the 8192K chunk size) on at least one, and I believe on two occasions in the past. If memory serves, I think that I originally started the array with 4 devices. So I suspect, as I mentioned above, that the problem was with the combination of a large chunk size and exceeding 16TB on the array size. That is just conjecture, though. I have no real evidence to support this.

 - dan B hentschel

---

