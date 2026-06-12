---
title: "software RAID 1 on advanced format drives"
date: 2013-02-25
forum: Hardware
---

### Post by ahevans on 2013-02-25
Hi

I have attempted and failed to setup a software RAID 1 in ubuntu 12 LTS due to my 3tb WD green drives using advanced formatting and so ending up misaligned.

I have googled and searched this forum for a tutorial on setting up these drives from scratch so they are correctly partitioned and the raid setup using mdadm but I cant find anything.

I have ubuntu on a single 250g primary drive then the two 3tb drives seperate purely for the RAID 1 setup. Can anyone help please?

---

### Post by SaturnusDJ on 2013-02-26
Soon I'll have to deal with this also. Therefor I already did some research. I've found this one to be the most useful:
[http://linuxconfig.org/linux-wd-ears-advanced-format](http://linuxconfig.org/linux-wd-ears-advanced-format)

Also read the comments! Especially the one of "tios." His comment sounds obvious to me.

It's wise to verify these recommendations. So create aligned and misaligned partitions, create a filesystem on them (ext3 is a good indicator) and check the performance of both.
After this tests, do another one with mdadm included.

---

### Post by SaturnusDJ on 2013-03-01
It might be a bit easier after all. 
[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)
:)

---

