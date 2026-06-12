---
title: "RAID 5 Array rebuilds itself after each reboot/shutdown"
date: 2016-09-28
forum: Hardware
---

### Post by siwy654 on 2016-09-28
Hi,

I'm using Ubuntu 16.04.1 LTS and using two raid arrays: 0 (2 SSDs) and 5 (4 disks), both are hardware raids configured on motherboard level.

The issue is that after every reboot or shutdown raid 5 array rebuilds itself which takes 6 hours....

I didn't have this issue with Centos.

I have looked through many forums/posts but didn't find any answer to solve this issue.

Please help!!

Motherboard: Gigabyte GA-H170N-WIFI (H170 PCI-E DDR4)
HDDs: 4x Seagate 4TB 5900 64MB NAS

/proc/mdstat

Personalities : [raid0] [raid6] [raid5] [raid4] [linear] [multipath] [raid1] [raid10]
md124 : active raid5 sda[3] sdb[2] sdc[1] sdd[0]
      11721048064 blocks super external:/md125/0 level 5, 128k chunk, algorithm 0 [4/4] [UUUU]
      [>....................]  resync =  4.6% (183038904/3907016192) finish=352.5min speed=176063K/sec

md125 : inactive sda[3](S) sdb[2](S) sdd[1](S) sdc[0](S)
      9552 blocks super external:imsm

md126 : active raid0 sde[1] sdf[0]
      488391680 blocks super external:/md127/0 16k chunks

md127 : inactive sde[1](S) sdf[0](S)
      5224 blocks super external:imsm

unused devices: <none>

P.S. md125 and md127 are containers created automatically

/etc/mdadm/mdadm.conf

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY metadata=imsm UUID=3681254a:3f91e1ee:b201102d:4cabf69f
ARRAY /dev/md/Data container=3681254a:3f91e1ee:b201102d:4cabf69f member=0 UUID=e47d3075:147551bd:d406d2a8:0ff87f3e
ARRAY metadata=imsm UUID=9d3d0784:cfd7a94e:0f4de1f9:102d378a
ARRAY /dev/md/System container=9d3d0784:cfd7a94e:0f4de1f9:102d378a member=0 UUID=e1cdd171:94cd720f:c43a55f0:0ba36731

# This file was auto-generated on Sat, 13 Aug 2016 16:47:25 +0200
# by mkconf $Id$

UUIDs are OK 
update-initramfs -k all -u - didn't help

From journal:

wrz 28 17:45:43 nas kernel: md: raid6 personality registered for level 6
wrz 28 17:45:43 nas kernel: md: raid5 personality registered for level 5
wrz 28 17:45:43 nas kernel: md: raid4 personality registered for level 4
wrz 28 17:45:43 nas kernel: md/raid:md124: not clean -- starting background reconstruction
wrz 28 17:45:43 nas kernel: md/raid:md124: device sda operational as raid disk 0
wrz 28 17:45:43 nas kernel: md/raid:md124: device sdb operational as raid disk 1
wrz 28 17:45:43 nas kernel: md/raid:md124: device sdc operational as raid disk 2
wrz 28 17:45:43 nas kernel: md/raid:md124: device sdd operational as raid disk 3
wrz 28 17:45:43 nas kernel: md/raid:md124: allocated 4374kB
wrz 28 17:45:43 nas kernel: md/raid:md124: raid level 5 active with 4 out of 4 devices, algorithm 0
wrz 28 17:45:43 nas kernel: RAID conf printout:
wrz 28 17:45:43 nas kernel:  --- level:5 rd:4 wd:4
wrz 28 17:45:43 nas kernel:  disk 0, o:1, dev:sda
wrz 28 17:45:43 nas kernel:  disk 1, o:1, dev:sdb
wrz 28 17:45:43 nas kernel:  disk 2, o:1, dev:sdc
wrz 28 17:45:43 nas kernel:  disk 3, o:1, dev:sdd
wrz 28 17:45:43 nas kernel: md124: detected capacity change from 0 to 12002353217536
wrz 28 17:45:43 nas kernel: md: md124 switched to read-write mode.
wrz 28 17:45:43 nas kernel: md: resync of RAID array md124
wrz 28 17:45:43 nas kernel: md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
wrz 28 17:45:43 nas kernel: md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
wrz 28 17:45:43 nas kernel: md: using 128k window, over a total of 3907016192k.
wrz 28 17:45:43 nas kernel: random: nonblocking pool is initialized
wrz 28 17:45:43 nas kernel: clocksource: Switched to clocksource tsc
wrz 28 17:45:43 nas kernel: [drm] RC6 on
wrz 28 17:45:43 nas kernel: md: linear personality registered for level -1
wrz 28 17:45:43 nas kernel: md: multipath personality registered for level -4
wrz 28 17:45:43 nas kernel: md: raid1 personality registered for level 1
wrz 28 17:45:43 nas kernel: md: raid10 personality registered for level 10
wrz 28 17:45:43 nas kernel: EXT4-fs (md126p2): mounted filesystem with ordered data mode. Opts: (null)

Thanks in advance!

---

