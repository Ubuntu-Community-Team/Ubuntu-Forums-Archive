---
title: "Trying to resurrect a RAID5 array"
date: 2009-07-14
forum: Hardware
---

### Post by orangejon on 2009-07-14
Hi,

I had a 3x160Gb Software RAID5 array running in my old machine, connected to two 2-port SATA cards.  I have now moved the drives and cards across to my new machine, which itself has a larger RAID5 array (3x1TB on a 4-port SATA card).  It is possible that different drives are plugged into different cards, but I hope this isn't important.  I am now trying to mount the old array, and copy the files over to the new array.

I ran this command yesterday:```
/sbin/mdadm --create --verbose /dev/md1 --level=5 --raid-devices=3 /dev/sdb /dev/sdf /dev/sdg
```

That seemed to work, and mdadm showed it as active but one drive rebuilding.  I let it rebuild but then I had to shut the machine down overnight.  On rebooting it doesn't seem to be active (and it's called md_d1 instead of md1? or am I just confused?):
```
root@server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d1 : inactive sdf[1](S)
      160086464 blocks
       
md0 : active raid5 sde1[2] sdd1[1] sdc1[3]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      [========>............]  recovery = 43.5% (425708672/976759936) finish=547.1min speed=16784K/sec
      
unused devices: <none>

```

I tried re-running the same command as yesterday to re-create the array, but got errors:
```
root@server:~# /sbin/mdadm --create --verbose /dev/md1 --level=5 --raid-devices=3 /dev/sdb /dev/sdf /dev/sdg
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sdb appears to be part of a raid array:
    level=raid5 devices=3 ctime=Mon Jul 13 13:44:09 2009
mdadm: Cannot open /dev/sdf: Device or resource busy
mdadm: /dev/sdg appears to be part of a raid array:
    level=raid5 devices=3 ctime=Mon Jul 13 13:44:09 2009
mdadm: create aborted

```

Not sure what is causing those errors!  To be honest I'm not really sure if I'm going about this in the right way and I'm a bit worried about losing my data.  Also worrying is that apparently there's no valid partition table on /dev/sdg:
```
root@server:~# fdisk -l /dev/sdg

Disk /dev/sdg: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00060e10

Disk /dev/sdg doesn't contain a valid partition table

```

The other two drives (sdb and sdf) have identical partition tables, as they should:
```
root@server:~# fdisk -l /dev/sdf

Disk /dev/sdf: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00077e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       19452   156248158+  fd  Linux RAID autodetect
/dev/sdf2           19453       19561      875542+  fd  Linux RAID autodetect
/dev/sdf3           19562       19929     2955960   fd  Linux RAID autodetect
```

GParted shows /dev/sdb1 as being an LVM partition (but not /dev/sdf1).  I have a feeling I may have enabled LVM so this seems correct (but why only on one drive?).

Strangley mdadm now shows one spare rebuilding on the large array, md0.  Presumably that is just co-incidence.  Do these rebuilds happen often?

I'm at a bit of a loss as to how to proceed, and would really appreciate any pointers you can give me! :)

---

