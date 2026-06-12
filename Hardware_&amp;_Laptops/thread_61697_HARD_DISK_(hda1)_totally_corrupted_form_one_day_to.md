---
title: "HARD DISK (hda1) totally corrupted form one day to another!"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by xbaez on 2005-09-01
Dear Ubuntu users

I am a happy Ubuntu user but what happened to me today was not fun

One day before yesterday everything on my computer was working fine.
All I remember adding/updating was a new Win98 Virtual Disk (using VMware Workstation 5), and a new LG DVD-Writer

I even burned a DVD and was able to run Win98 from Linux.

Today I went to work, turned my PC on, and it started booting normally.
Suddenly, as KDE/Gnome (don't remember which one excactly) was loading, the system stopped.
I checked the logs (the console actualy), and /dev/hda1 had been remounted as read-only

There was NOTHING i could do, so I rebooted the machine, next boot, not even Grub was loading.

Can somebody please tell me what happened, or why?
esfsck, fsck... didn't worked, Partition Magic didn't even recognized my file system in that partition (the other ext3 systems were fine)

For my good luck I have all the Linux downloads and apt repositories on another partition (apart from the DVD I just created), and my /home is on a RAID partition as well

Anyway, I reinstalled Ubuntu today, but I'm nervous, why did this happened?

HDA1 is part of a 160 GB disk and I surely wouldn't like that to happen to other partitions.
I presume it happened there because of a OS issue, else why will only hda1 was corrupted?

---

