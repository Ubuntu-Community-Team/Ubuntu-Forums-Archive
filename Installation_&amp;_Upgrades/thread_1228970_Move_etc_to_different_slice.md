---
title: "Move /etc to different slice"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by slakkie on 2009-08-01
Hello,

I needed to make some changes to my partitions, and decided to put /etc on a seperate slice. The idea behind it was to make sure that /etc can be recovered in case I need to reinstall my OS... 

I've added the mountpoint /etc in fstab, but as you know /etc is where fstab resides so some problems pop up once you boot the OS (it hangs).

Is there somewhere I can tell Ubuntu before it mounts all my disks where /etc resides? /boot/grub/menu.lst??

Many thanks.

---

### Post by andrewc6l on 2009-08-01
Because of the way Unix works, /etc has to reside on the root partition. In addition to fstab, there are a number of other files (including /etc/init.d/) that need to be there before going to multiuser mode.

You might want to consider creating a second partition (/etcbackup?) and backing /etc up to it in a cron job instead. (Some Unix systems have an entire duplicate / partition - so if the "regular" / partition happens to get corrupted, you can still boot using the alternate root. Of course, you still have the issue of keeping things up to date when you make changes to / :-) )

---

