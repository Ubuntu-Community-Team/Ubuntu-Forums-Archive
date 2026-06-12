---
title: "Using permanently attached USB drive for backup"
date: 2011-09-13
forum: Hardware
---

### Post by Jethro_uk on 2011-09-13
Hi guys,

I currently have 2x1TB USB drives in a RAID 1 array. So I am protected against drive failure. However, this is not a backup solution. Obviously backing up 1TB of data is a challenge.

I have been wondering about getting a 2TB USB drive, which I will plug in and use for a weekly backup. The idea is that for most of the time the drive is off (and therefore "safe") and that every so often, it "wakes up" and works long enough for the backup to run, and then powers down again.

The drive I am considering is a Hitachi XL2000.

Does anyone know if this is possible (or suggest a different approach ?)

---

### Post by varunendra on 2011-09-14
Once a usb hard drive sits idle for a certain amount of time (perhaps 1-2 minutes), it automatically goes to "sleep" state. At least this is what I have noticed with my external USB hard drives.

So you may simply create a backup script, add it to a cron job ([see how]("http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/")), and leave the drive permanently plugged in and powered on. It will automatically become active when invoked by the script, store the backup, then 'should' again go to its 'sleep' state after sitting idle for a while.

However, if you want a professional (I'm not one;)) approach, have a look at [FreeNAS]("http://www.freenas.org/category/version-comparison") (version 0.7 stable, as the latest '8' demands at least 4GB RAM). You may install and run it on a virtual machine with just about 256 MB of virtual RAM. Besides its amazing inbuilt features, it also allows to run custom scripts and cron jobs.
You may download version 7 from sourceforge: [http://sourceforge.net/projects/freenas/files/FreeNAS-7-Stable/](http://sourceforge.net/projects/freenas/files/FreeNAS-7-Stable/)

User Manual (online): [http://wiki.freenas.org/documentation:setup_and_user_guide](http://wiki.freenas.org/documentation:setup_and_user_guide)

User Guide (pdf for version 0.684): [http://www.mendax.com/images/slnImages/s85/FreeNAS-SUG.pdf](http://www.mendax.com/images/slnImages/s85/FreeNAS-SUG.pdf)

---

