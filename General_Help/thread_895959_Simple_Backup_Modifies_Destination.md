---
title: "Simple Backup Modifies Destination"
date: 2008-08-20
forum: General Help
---

### Post by mauimike on 2008-08-20
I like Simple Backup because of its easy restore feature but it has an annoying behavior that frequently causes my system to run out of disk space.

I have a hard drive mounted as media/disk (/dev/sda1) that I use as a daily backup drive. When simple backup fills up the disk it renames the mounted volume to /media/disk-1 and creates a new /media/disk on my main hard drive (/dev/sdb1) and then starts backing up to that destination and soon fills up my main drive.

How can I restrict simple backup to only use the /dev/sda1) drive?

---

### Post by Zill on 2008-08-20
> **mauimike said:**
> ...How can I restrict simple backup to only use the /dev/sda1) drive?
Configure Simple Backup to automatically purge old backups - look at the options in "Simple Backup Config".

---

