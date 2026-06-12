---
title: "Software raid in HW raid enclosure?"
date: 2012-12-18
forum: Hardware
---

### Post by sexzual on 2012-12-18
Hello!  I've been using linux for about a year and a half now, but i do almost everything through gui,  not terminal.  I'm learning slowly.  Anyway, just picked up a buffalo hd-wiu2 drivestation which i'm to believe has hardware raid?  It seems more like a fake raid to me.  Needless to say there is no linux program to make use of this drive in a raid configuration for linux. (correct me if i'm wrong)  So i looked into doing a software raid setup using mdadm.  For the past few days i've poured over outdated online tutorials and read through the man page of mdadm.  But for the life of me i can't seem to set up a raid 1 on this device.  

At this time, i've formatted the drives (2 500gb) with fdisk.  1 partition each with t option fd.  

Then i  "mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1"

As it sits:
 Every 2.0s: cat /proc/mdstat                                             Tue Dec 18 19:08:26 2012  Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] md0 : active raid1 sdc1[1] sdb1[0]       488254336 blocks super 1.2 [2/2] [UU]       [===>.................]  resync = 18.1% (88783296/488254336) finish=680.4min speed=9783K/se c  unused devices: <none>


Is everything ok so far?  I've tried to speed it up by making:
dev.raid.speed_limit_min = 50000
dev.raid.speed_limit_max = 200000
but that hasn't made the speed any different.

If this is correct, where do i go from here?  As this is an external usb enclosure, i'm just going to be throwing important data and backups on it.  Not planning on installing any os or software on it.  I would like it to mount on boot though.  

Thanks for any help!  Hope this is in the right topic...  And FYI i'm running kubuntu 12.10

---

