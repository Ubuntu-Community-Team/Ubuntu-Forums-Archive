---
title: "Mounting drive for data recovery - desperate!"
date: 2013-04-01
forum: Hardware
---

### Post by pcal on 2013-04-01
Hi guys.

I've had a significant hardware failure on a nas drive (Maxtor Shared Storage 200Gb). Couldn't attach to my user account on the drive this morning - was working fine yesterday - so logged into the admin page to discover that **_all_** the user account are **_gone!!_** For the rest of the family, this is inconvenient, but for me it's a disaster. Contains my thunderbird profile with years of mail, all my software downloads and installation images, photo collection - almost everything I own. Have another nas drive with an automatic backup system running. Never needed to recover anything before, but have found a misconfiguration means not everything was making it into the backup. Can get back most of my data from the partial backup and the misc bits and pieces on pc's around the lan, but still need to recover my thunderbird profile.

I've pulled the hdd out of the Maxtor device and plugged it into a usb interface to try and mount it on my 12.04 machine. Googling the device suggests its using reiserfs on the drive. I downloaded the MountManager application, which can see the drive at /dev/sdb and identifies it as a 189.9Gb Drive - but the *moun*t option is greyed out. Went to their support page, but I don't read Russian...

I've also tried manually mounting the drive with the command...

```
local@family-ubuntu:/media$ sudo mount -t reiserfs /dev/sdb /media/recovery
```

...but got the response

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I'm not highly skilled in linux. Can follow the bouncing ball, and have a basic grasp, but find myself sinking beyond my depth. Is there something obvious I've missed? Is there another method with better chances of success? Any options more than welcome.

Thanks in anticipation,

Pcal

---

### Post by pcal on 2013-04-01
Haven't got anywhere mounting the drive, so have tried reinstalling it in the nas enclosure.

On rebooting, it now recognises that the user accounts exist, and has the correct access restrictions on each of them (according to the account managements features of the web admin page), but is still refusing any connection to the drive by any means I have tried (everything I can think of!)

I'm working on the hope that details of the account structure are stored on the hdd itself. In which case, the firmware has been able to access the hdd, which gives me some hope of a resolution (was fearing a complete hdd failure). I still need any clue how to get the hdd media talking to the outside world...

...help!

Regards,

Pcal

---

### Post by tgalati4 on 2013-04-01
Reiserfs is an interesting file system.  The inventor/developer is in jail--and that is an interesting read in itself.  To be able to mount and read it, you would need to install some programs:

tgalati4@Mint14-Extensa ~ $ apt-cache search reiser
libaal-dev - Reiser4's application abstraction library
libreiser4-dev - Reiser4's filesystem access and manipulation library
reiser4progs - administration utilities for the Reiser4 filesystem
reiserfsprogs - User-level tools for ReiserFS filesystems
chiark-scripts - chiark system administration scripts
fstransform - Tool for in-place filesystem conversion
gpart - Guess PC disk partition table, find lost partitions
mountmanager - User-friendly management of disks and partitions
partimage - backup partitions into a compressed image file
partimage-doc - Partition Image User Documentation
partitionmanager - A partition management utility
testdisk - Partition scanner and disk recovery tool

It could be a hardware problem with the NAS.  Perhaps cleaning and reseating cables is all you need.  If the drive itself is failing, then you don't have much time for recovery.  Whatever you do, don't compound the problem by reformating, repartitioning, juggling, boiling, or otherwise destroying the drive.  Take one step at a time and try to determine what is working and what is not--situational awaremenss.  Then prioritize what is most important and go after that--triage.

This sounds like an older NAS.  It could be suffering from bad capacitors or the drive is having aging issues.

Also understand that the reiserfs used on the drive may be slightly different than the reiserfs recognized by Ubuntu.  Most retail NAS operating systems are beyond crapware.  So don't be surprised if you try to resurrect the drive with linux tools and you encounter problems.  If there is a way to upgrade the firmware of the NAS, now would be a good time to do it.  It may fix some bugs in the crapware/firmware that will allow you to gain access.

---

