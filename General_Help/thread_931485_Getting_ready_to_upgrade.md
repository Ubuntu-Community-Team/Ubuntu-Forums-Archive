---
title: "Getting ready to upgrade"
date: 2008-09-27
forum: General Help
---

### Post by 3pinner on 2008-09-27
hello,
I'm getting ready to upgrade from 7.10 to 8.04 and would like to know if there are any specific issues I should watch for. My current setup is:

Dual Boot with Windows 2000, with each OS on a seperate hard disk.

I have some 3rd party programs installed. Any issues there?

I have some programs installed under WINE - any issues here?

Anything in general I should watch out for?

Thanks!
3pinner

---

### Post by ju2wheels on 2008-09-27
Upgrading is not a fail proof procedure. I would highly recommend at a minimum that you **backup** your home directory. 

Also, for the most part you may need to upgrade certain packages to the hardy version (if one is available). Personally, I just make separate partitions for my /home and for / that way I can do a clean install on / without having to worry about such upgrade issues and/or loosing my files.

The programs installed under wine are in your home folder, so again backing this up is important. You shouldnt have any problems running your applications on a newer version of wine if you currently have them working.

---

### Post by 3pinner on 2008-09-27
When I first installed gutsy, I set up a / partition, /home, and /swap partitions as well.
So I can backup my /home partition, and just do a clean install over the
 / partition?
Sorry about the basic question, but upgrading Ubuntu is new to me.

Thanks

---

### Post by ju2wheels on 2008-09-28
Yes thats correct. But when doing the partitioning during the clean install make sure you do it manually and tell the partitioner to use  sda1 and mount to / (and select format), and sda2 and mount to /home (do not select format), and sda3 and mount to swap for example and substitute your appropriate partitions. The key point is to make sure to add the mount points and you should be all set.

For your windows partition you just leave it and dont do anything (unless you want it to be mounted automatically to a particular location. For example if you wanted your windows partition to always be automatically mounted to /windows, and if sda4 were your windows partition then select sda4 and manually add /windows as the custom mount point in the partition and make sure to not select format.

---

