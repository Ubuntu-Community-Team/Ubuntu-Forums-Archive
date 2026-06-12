---
title: "harddisk goes standby way too fast (after few seconds)"
date: 2011-12-17
forum: Hardware
---

### Post by Blindleistung on 2011-12-17
Hi community.

There are loads of forums discussing how to make harddisks park using hdparm. And why disks spin up when they shouldn't.

I got the opposite problem: One of the four disks of my raid-6 array always spins down after only 2(!) seconds of idle time. :frown: Which is bad for the disk and keeps interrupting any media-playback running from the raid array.

All four disks are configured in a similar way.

From hdparm.conf:
>>>
/dev/sde {
        apm = 80
        keep_features_over_reset = on
        spindown_time = 242
}
<<<

I also set the features manually using

>  sudo hdparm -S242 -B80 -k1 -K1 /dev/sde

When issuing this command, the disk spins up, takes settings (ignoring the K-sets), then spins down 2 seconds later.

console:

blind@box:~$ sudo hdparm -S242 -B80 -k1 -K1 /dev/sde
/dev/sde:
 setting keep_settings to 1 (on)
 HDIO_SET_KEEPSETTINGS failed: Inappropriate ioctl for device
 setting drive keep features to 1 (on)
 setting Advanced Power Management level to 0x50 (80)
 setting standby to 242 (1 hours)
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 APM_level      = 80


I have no idea what to do now? I could think about a little python script to access the disk every 500ms as long as the other disks won't park.   But that would not be very nice.

There are two of those samsung disks in the array. The other behaves normally.

The disk is new.  Shouldn't have a bug?


One more hint:

The disk was added to the raid-6 array at a later time. First, I set up the raid with 3 disks only. After adding this one and having it synced, I adjusted the hdparm for it and the problem was there. Can mdadm have something to do with it?

mdadm does not report any problems with the array...

  > cat /proc/mdstat
  Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
  md127 : active raid6 sdd1[4] sdc1[1] sdb1[0] sde1[5]
        3906251776 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]

   unused devices: <none>



:confused:

Thanks all.

---

