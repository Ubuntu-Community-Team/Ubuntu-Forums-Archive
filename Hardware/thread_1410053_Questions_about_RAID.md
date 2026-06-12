---
title: "Questions about RAID"
date: 2010-02-18
forum: Hardware
---

### Post by Gorgamel on 2010-02-18
1) Can I append another disk to an existing RAID with disks?

2) If so, can I then start with just one disk. Or will this make a problem?

3) Do all the disks have to be of the same size?

---

### Post by Gorgamel on 2010-06-01
Sorry for the late bumping, but... :)

---

### Post by 337Manni on 2010-06-01
1. The simple answer is yes. You can expand your raid array by adding disks.
   
  2. I remember reading somewhere that you can have raid on one disk. There is no gain for one disk raid and I could see it leading to more of a headache. The idea is either increased performance (RAID 0), or fault tolerances to some degree (Other RAID's). One disk wouldn't give either of these.
   
  3. No. You can use disks of different sizes. If you had a 1TB hdd and a 500GB hdd you would make partitions of equal sizes on each disk and point the raid at that.
   
  e.g.
          Disk A (1TB)
500GB Partition - Used in the RAID array
500GB Partition - Used for data storage

Disk B (500GB)
500GB Partition - Used in the RAID array

If you had RAID 0 that would be a 1TB RAID 0 array and a 500GB for storage
If you had RAID 1 that would be a 500GB RAID 1 array and a 500GB for storage


  What size hdd have you now or are you planning on getting?
What type and how are you planning on setting up your RAID?

I read a lot into the subject a few years ago when I was looking into building my last system. I've slept since, but will try getting the old gray matter working again. :)
   
  Some good links:
  [http://en.wikipedia.org/wiki/RAID#New_RAID_classification](http://en.wikipedia.org/wiki/RAID#New_RAID_classification)
  [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

---

