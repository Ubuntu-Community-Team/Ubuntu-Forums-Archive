---
title: "Can I install to RAID-6?"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Kissell on 2008-12-21
I have a large RAID-6 volume, but I have two problems.

1) My Ubuntu OS installation is on a single disk, so it's not redundant at all, if that disk dies my system is down.  :(

2) The RAID-6 volume is out of space, and I have no more hard disk slots... 

My solution... Should Ubuntu choose to accept it, would be to get rid of the disk the OS is installed on, replace it with an additional drive for the RAID-6 and partition off a few GB from each disk in the RAID-6 to use to boot from.  

But, I've been trying all night, and can't get it to work...  I'm using Hardy 32-bit, and I can boot to Ubuntu normally and create RAID-6 paritions for "/", "/swap", and "/mnt/md0", but when I then boot to the Ubuntu installation disk it doesn't see those partitions I created, so I can't install the OS to them...  

I also tried to create the partitions from inside the installation disk's partitioner, but raid-6 is not an option.  I have thirteen 750GB disks in the array, so RAID-5 is really not an option, too risky, I really want that extra disk for more redundancy.

---

### Post by infamous-online on 2008-12-21
Have you tried raid 1? raid 6 is fairly uncommon, and I have to ask are you using it for advanced data guarding purposes?

---

### Post by Kissell on 2008-12-21
well, I have 12 disks, i'm using RAID-6 instead of RAID-5 just so I have a 2nd disk that can fail without losing the data.  But, the array is full (both physically and in byte capacity), so I wanted to replace "the C drive" (lol) with a 13th disk (because there is no money).  

If I replace "the C drive" with a 13th disk, I can make the storage capacity grow on the RAID-6 data volume, and make the Ubuntu OS's disk drive redundant...  

I hadn't tried RAID-1, because I would have to carve out like 20GB of space on all 13 disks just to run RAID-1 on two disks...  But I could carve out just 2GB of space on each disk and partition it as RAID-6 just like the data partition is...  If I do a RAID-1 parition on these disks I loose 220GB on the RAID instead of only 20GB...  and if I do RAID-5 I risk the server dying after a 2nd disk failure.  Yes, the data partition would still be okay, but the server would crash after the 2nd disk failed.  (That's actually kinda a poor-mans protection, lol).  But, I'm leaving this in the care of another (newbie) admin, I'll only be available for support via e-mail.  So I really wanted to make Ubuntu boot via RAID-6.  This is an old server, it's actually prone to lose a disk quite often, usually the disk is fine, it just thinks it lost a disk because a controller temporarily goes a little nutty.  It's not uncommon that throughout the year there would be times where two disks were down at once.

---

