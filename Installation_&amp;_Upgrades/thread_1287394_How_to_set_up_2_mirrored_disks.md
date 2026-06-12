---
title: "How to set up 2 mirrored disks?"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by htadeleeuw on 2009-10-10
Hi,
 
I want to set up my PC (VIA PC3500G board, with 2 Gb RAM, 2 x 1Tb WD10EADS, and a Pure Power BQT L7 300W PSU) as a reliable and energy efficient home server (running dns, samba, scalix, mysql, apache, moinmoin wiki, and what not).
Dedicated Ubuntu server, no dual booting, no other operating systems.
 
I wasn't sure how to set up my disk and there is too much (inconsistent) information out there to determine what's best.
 
I have done this:
- In the BIOS I've switched the SATA mode from RAID to IDE, so I will not use the on-board RAID features.
- During the Ubuntu install, in the disk partitioning section I did:
- create a single 1 Tb primary partition on each disk and set it to "be used in a RAID"
- created 1 mirrored partition to be used by LVM that uses the 2 primary partitions
- created 1 volume group, vg01, that contains 1 mirrored partition
- in the volume group I have created these logical volumes:
- lvol1, 2Gb ext3, for /
- lvol2, 2Gb swap for swap
- lvol3, 2Gb ext3 for /boot
- lvol4, 2Gb ext3 for /opt
- lvol5, 2Gb ext3 for /var
- lvol6, 2Gb ext3 for /var/spool
- lvol7, 2Gb ext3 for /var/tmp
- lvol8, 2Gb ext3 for /tmp
- lvol9, 2Gb ext3 for /home (which will probably be extended, and extended, ...)
 
It seems to work fine (except, that after initial boot the system appeared to be sync-ing the mirror for a very long time, but I guess that must have been to synchonize the two 1 Tb partitions).
 
Did I do wrong? Does my set up impose certain risks? I'm not sure, and any feedback would be appreciated.
 
Cheers,
Henk

---

### Post by borahshadow on 2009-10-10
I'm not a RAID Guru but i've set up RAID systems before. It looks like you set it up fine. I've never used LVM so I can't comment on that one. for me it just added complexity because I had no *real* need for it.  As long as /cat/proc/mdstat shows that it is fine and syncing you should be good to go.

If I can offer a suggestion on the best way to get some of that other stuff set up it would be to use tasksel and select LAMP. That will install Apache Mysql and PHP for you. Samba can be a trick to set up sometimes but there are lots of tutorials out there.

Hope I helped.

---

### Post by htadeleeuw on 2009-10-11
Thanks. LAMP, OK, will do.
I'm having high hopes of Samba. Hopefully I can pretend it to be a Windows domain controller. Have to implement roaming profiles some way as well, for the Windows clients. Should be fun.
True, that there is plenty of material out there. Too much sometimes, if you ask me :-) ; I don't know who to believe.
Cheers,
Henk

---

