---
title: "HD-DVD Drive Support"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by tommoyer324 on 2007-07-05
I recently purchased a new laptop which has a Toshiba TS-L802A HD-DVD drive.  I am able to boot the Feisty Fawn liveCD, and install everything, but after that whenever I insert a disk, it is detected as a blank disk (in the case of a burned cd/dvd) or doesn't get detected at all ( in the case of manufactured discs).  I had some issue with it not being available after a recent kernel update (from 2.6.20-15 to 2.6.20-16) but I was able to load the ide-generic module and at least access the drive again.  I am able to mount discs manually, and access them, but this really isn't an optimal solution in the long run.

My question is does anyone have any experience with this drive and getting it to work successfully under Linux?  It is the only piece of hardware that isn't being supported nicely.  I am going to try Gutsy Gibbon Tribe 2 to see if it is better supported by a newer kernel, but was wondering if anyone else was having these issues.

The laptop in question is an Acer Aspire 5920G.

---

### Post by geraldm on 2007-07-05
mount uses options specified in the /etc/fstab line for the HD-DVD device.
You did not post the line, but you can explore the options...

---

### Post by tommoyer324 on 2007-07-06
I don't have the machine right now, but I can check soon.  But I'm not seeing how being detected as blank when I insert a burned disc (in this case the one I installed Feisty Fawn from) is a problem with my fstab.

---

### Post by MucRonin on 2007-08-12
> **geraldm said:**
> mount uses options specified in the /etc/fstab line for the HD-DVD device.
You did not post the line, but you can explore the options...

same issue here.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=02de44c4-6d8e-41a8-805a-bd4c2e5628f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=708f17c3-2342-4ec0-ab46-0722d342a67b /LFS            ext3    defaults        0       2
# /dev/sda1
UUID=050a6d98-4274-4b97-83f7-5d7f30e7a5af /boot           ext3    defaults        0       2
# /dev/sda3
UUID=45bfdc9a-b7e6-4230-b535-b5bdc47ad08e /home           ext3    defaults        0       2
# /dev/sda6
UUID=dfffd70d-714a-4b4e-b382-ed585378fe8c none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

wether with or without the # in front of /dev/hda ... the drive is accessible. Same Hardware under Gutsy Gibbon Tribe 4. (Alternate Install works, but after the first boot there is no drive anymore.

---

### Post by tommoyer324 on 2007-08-12
After doing some more trial and error, I have managed to get access to the drive by loading the ide-generic module.  However this module doesn't use DMA so performance is suboptimal, but does allow use of most drive functions (HD-DVD playback not tested).  This appears to be an issue with the kernel in general (drivers getting moved around and such) and not Ubuntu.  I guess I will have to wait and see how things get sorted out.

---

### Post by MucRonin on 2007-08-13
Thanks a lot. I read that on your Laptoptesting Wikipage a couple of days before. Almost two month to final. A lot could happen. I hope so. Greetings from Munich/Bavaria

---

