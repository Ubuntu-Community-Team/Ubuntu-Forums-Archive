---
title: "Sata III problem on Asus Sabertooth X58"
date: 2011-04-19
forum: Hardware
---

### Post by wirre on 2011-04-19
I have a Asus Sabertooth X58 motherboard on which I’m trying to use all 8 SATA ports.
I can’t get the 2 disks connected to the SATA III ports to work in software raid.
The plan is to use 2 SSD disk for / /boot and swap
And 6 disk in a raid 5 setup.
Im running the latest beta of Ubuntu Server to get as fresh drivers as possible.
```
root@kris:~# uname –a
Linux kris 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
When I try to make a mdadm software raid5 device it fails the to disks connected to the Marvell ports after a moment.
```
root@kris:~# mdadm --create /dev/md2  --level=raid5 --raid-devices=6 --spare-devices=0 /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh
mdadm: partition table exists on /dev/sdc but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sdd but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sde but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sdf but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sdh but will be lost or
       meaningless after creating array
Continue creating array? Yes
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md2 started. 
```
```
root@kris:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sdh[6] sdg[4] sdf[3] sde[2] sdd[1] sdc[0]
      9767564800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/5] [UUUUU_]
      [>....................]  recovery =  0.0% (20736/1953512960) finish=26671.6min speed=1219K/sec
md0 : active raid1 sdb1[1] sda1[0]
      194548 blocks super 1.2 [2/2] [UU]
md1 : active raid0 sdb3[1] sda3[0]
      144189440 blocks super 1.2 512k chunks
unused devices: <none>
```
After 1-2 min wait:
```
root@kris:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sdh[6](F) sdg[4](F) sdf[3] sde[2] sdd[1] sdc[0]
      9767564800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/4] [UUUU__]
md0 : active raid1 sdb1[1] sda1[0]
      194548 blocks super 1.2 [2/2] [UU]
md1 : active raid0 sdb3[1] sda3[0]
      144189440 blocks super 1.2 512k chunks
unused devices: <none>
 
root@kris:~# mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Tue Apr 19 18:45:59 2011
     Raid Level : raid5
     Array Size : 9767564800 (9315.08 GiB 10001.99 GB)
  Used Dev Size : 1953512960 (1863.02 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent
    Update Time : Tue Apr 19 18:47:22 2011
          State : clean, FAILED
 Active Devices : 4
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 512K
           Name : kris:2  (local to host kris)
           UUID : bf837ffe:1c415c01:aff105c3:71d6d4fc
         Events : 5
    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8       64        2      active sync   /dev/sde
       3       8       80        3      active sync   /dev/sdf
       4       0        0        4      removed
       5       0        0        5      removed
       4       8       96        -      faulty spare   /dev/sdg
       6       8      112        -      faulty spare   /dev/sdh
```
I have updated the BIOS to the latest firmware and changed the disk controllers from IDE to AHCI.
Extra info:
```
root@kris:~# lspci | grep SATA
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
01:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9123 PCIe SATA 6.0 Gb/s controller (rev 11)
06:00.0 SATA controller: JMicron Technology Corp. JMB362 AHCI Controller (rev 10) 
```
The disk used in the Raid 5 are: Western Digital Caviar Green 2TB (IntelliPower / 64MB Cache / SATA II / NCQ)
Does anyone have any idea on how to make this work?

---

