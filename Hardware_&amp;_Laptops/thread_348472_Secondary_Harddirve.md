---
title: "Secondary Harddirve"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by digitizemd on 2007-01-28
I recently installed ubuntu, without any trouble, and quickly began to set things up to my liking.  I realized that for some reason my second HD (/dev/hdb1, mounted at /media/storage, using reiserfs) for some reason didn't appear mounted despite the fact that after i booted up i checked it , and saw it mounted correctly.  I decided that maybe something just got screwed up, so I rebooted and everything was back to normal, until I later found a repeat of the incident.  I decided to take a look at fstab, which contained the following:

proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ff8f26bd-b4e0-4197-95c7-fbbe50914973 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=799f9be6-8e04-4c73-a424-d18b1c293f50 /home           reiserfs defaults        0       2
# /dev/hdb1
UUID=12f1136a-6d6b-4e94-bf5c-8d860288576b /media/storage  reiserfs defaults        0       2
# /dev/hda1
UUID=243bd9de-f90c-43f6-b7ab-c6f4225ba984 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

I'm more accostumed to only seeing /dev/hdax, as opposed to UUID=..., but both hda2 and hda3 have had no problems, more importantly hda2 since it has nearly the identical setup.  Any suggestions?

---

