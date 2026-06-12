---
title: "help mounting &quot;LACIE internet space&quot; NAS drive"
date: 2009-11-09
forum: Hardware
---

### Post by dragonflyFZX on 2009-11-09
Hi,

I just installed the latest kubuntu and bought a lacie internet space drive. In windows, after installing the software, it shows a back-up, a SharedFiles and a MyFiles directory. How do I mount this in (k)ubuntu?

sudo mount -t cifs //192.168.1.114/SharedFiles /media/LACIE/openshare/ -rw -o umask=0000,username=xxxxx,password=xxxxx

gets me somewhere, the drive gets mounted, but ls -l gives:

drwxrwxrwx 6   48 users    0 2009-11-08 20:46 openshare

and I am not user 48 so I can not write to the disk. What am I doing wrong here???

---

### Post by blueghoti on 2010-04-26
Hi Dragonfly - 

I see this post was some time ago.  Were you successful?  I have just installed Ubuntu 9.10 for the first time and it seemed to recognise my Lacie Internet Space quickly (once I got my wireless networking sorted out, that is!)

What do you use for a backup utility?  I want to do a backup of all my user files and email content, then do incremental backups.  (I was using Vista backup to protect 20 gig of data, but within a few weeks, it inflated the storage to 700 gigs on the drive!)

Chris

---

