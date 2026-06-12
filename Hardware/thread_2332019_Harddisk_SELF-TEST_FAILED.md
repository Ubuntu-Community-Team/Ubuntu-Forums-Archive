---
title: "Harddisk SELF-TEST FAILED"
date: 2016-07-27
forum: Hardware
---

### Post by Shinger on 2016-07-27
Hi guys,

i am kind of stuck to not knowing what to do. I have a selfbuild server/NAS case with a RAID5 (5 disks) configuration-setting. I have installed on that Ubuntu Server edition and every 2 years i do a migration to another LTS version. Currently 16.04 LTS.

Server/NAS - case: [http://4.bp.blogspot.com/-wxzWSq6rswM/UCyYI2Wam9I/AAAAAAAAAkw/kqiX_2NnToI/s1600/lian_internal.JPG](http://4.bp.blogspot.com/-wxzWSq6rswM/UCyYI2Wam9I/AAAAAAAAAkw/kqiX_2NnToI/s1600/lian_internal.JPG)

(This is NOT a picture of my case, but i also have 5 disks in the rack and i have additional 5 disks(2.5 inch) on the lowerpart of the case.

In this server/NAS configuration i have installed webmin as my webconfig and a few months back it showed me that one disk has failed and that the RAID was degraded. I searched the net and i was hinted that it could be the SATA cable being the problem. Although for me very strange to say a cable is at fault while i never moved the cables around after putting it together, i followed the advice and replaces the SATA cable. Then turned on and RAID was back on and alive.

Now a few months have gone by, the same disk again has failed. When i try to put it back in to the RAID after maybe even 1 day it will fail again at first it even failed the rebuild process.

I have taken the drive out and put it in to a external case for further examination. With ¨gparted¨ by removing the partition, giving it another fs then formatting it, then checking it i had no problem at all.

I now have opened ¨gnome-disks¨ and and did a benchmarkt test (see attachments) and also a SELF-TEST (see attachments)

Where do i see additional information and/or does this mean the disk is dead? Because as far as you can see, no crucial points have reached the threshold of the SELF-TEST. I am no expert, so could somebody please help me understand this better and/or help me come to a conclusion what to do next.

Although the RAID i ONLY use to backup valuable data, other additional disks i have in the NAS-case i use for downloads etc. Also could be that the vibration of the other disk are doing additional damage to the disks? 

The temperature of the RAID-disks that are currently in the case

```
shinger@K-NAS:/media$ sudo hddtemp /dev/sdc
/dev/sdc: WDC WD20EZRX-00D8PB0: 31°C

shinger@K-NAS:/media$ sudo hddtemp /dev/sdd
/dev/sdd: WDC WD20EARS-00MVWB0: 32°C

shinger@K-NAS:/media$ sudo hddtemp /dev/sde
/dev/sde: WDC WD20EARS-00MVWB0: 33°C

shinger@K-NAS:/media$ sudo hddtemp /dev/sdf
/dev/sdf: WDC WD20EARS-00MVWB0: 30°C

```

Thanks in advance for you time and knowledge.

---

### Post by weatherman2 on 2016-07-27
> **Shinger said:**
> Although the RAID i ONLY use to backup valuable data, other additional disks i have in the NAS-case i use for downloads etc. Also could be that the vibration of the other disk are doing additional damage to the disks? 

WD20EARS is a "Green" disk and not designed to be used in a RAID with multiple drives (more than two).  You've got it right: the vibration of the other disks could indeed be causing issues.

[http://support.wdc.com/KnowledgeBase/answer.aspx?ID=996](http://support.wdc.com/KnowledgeBase/answer.aspx?ID=996)

You should be using the WD Red drives for a RAID like yours.

In any case, any drive that has failed a self-test and given you repeated problems should be replaced.

---

### Post by Shinger on 2016-07-27
> **weatherman2 said:**
> WD20EARS is a "Green" disk and not designed to be used in a RAID with multiple drives (more than two).  You've got it right: the vibration of the other disks could indeed be causing issues.

[http://support.wdc.com/KnowledgeBase/answer.aspx?ID=996](http://support.wdc.com/KnowledgeBase/answer.aspx?ID=996)

You should be using the WD Red drives for a RAID like yours.

In any case, any drive that has failed a self-test and given you repeated problems should be replaced.

Yeah, i found out just 1-2 years ago about the red drives. But yeah, too late, i guess. Although the green drives were not made for RAID with multiple drives, i have been using 1 TB green disks 2008-2012 and then went over to 2 TB drives since then. Surprisingly as you can see i have been using it already for almost 5 years in a row and no problems at all.

Although i just recently added additional 3 2.5 inch drives on the bottom.

But thanks for the answer. I will try just few more times if indeed the self-test again fails, then it´s time to make the coffin ready to bury it.

Thanks for the quick answer.

---

