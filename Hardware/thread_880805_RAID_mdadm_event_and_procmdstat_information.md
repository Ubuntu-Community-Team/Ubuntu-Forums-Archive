---
title: "RAID mdadm event and /proc/mdstat information"
date: 2008-08-05
forum: Hardware
---

### Post by GMU_ninja on 2008-08-05
Can someone please explain what all this means?!  I have scoured the internet, and nothing will explain it to me... not even the man pages.

> This is an automatically generated mail message from mdadm
running on cake

A DegradedArray event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda1[0] sdd1[3] sdb1[1]
     351654528 blocks level 5, 64k chunk, algorithm 2 [4/3] [UU_U]

unused devices: <none>

I understand that a "DegradedArray" event has happened.  I don't know what that is, and I don't know how to interpret the /proc/mdstat info.

I have 4 SATA drives (sda1, sdb1, sdc1, and sdd1) in a hardware RAID 5 array (md0).  Why isn't sdc1 showing up?  What does "[UU_U]" mean?

Where can I find more information, if I need it in the future?

Thanks!!

---

### Post by tamoneya on 2008-08-05
the degradation error means that mdadm thinks one of your drives has failed.  It seems to me like it is sdc in this case.  See if it shows up in ```
sudo fdisk -l
```  It may just be that mdadm cant find it.  Otherwise it probably means you need to replace the drive.

---

### Post by cariboo on 2008-08-05
If you look at this line from your post

> md0 : active raid5 sda1[0] sdd1[3] sdb1[1]

You can see that one of your drives has gone missing. I would suggest that /dev/sdc1 has either died, or has big problems.

Jim

---

### Post by nonovo on 2010-06-23
Hi guys,

This is my mdstat: 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb[3] sdc[0] sdd[1]
      488396928 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [====>................]  recovery = 22.6% (55411584/244198464) finish=68.3min speed=46011K/sec

unused devices: <none>

Q: Could you please explain what the sdb[3] sdc[0] sdd[1] mean?
I do understand that sdX are the drives, but I don't understand the [3] [0] [1]. I thought its number of the drive in the raid, but then I don't understand the gap [2] ?

Thx,
N.

---

