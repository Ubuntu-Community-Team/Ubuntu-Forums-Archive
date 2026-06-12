---
title: "Backup on Ubuntu?"
date: 2008-10-31
forum: General Help
---

### Post by blazemore on 2008-10-31
What can I use to do a daily backup to an external hard-drive, only overwriting files which have changed?
Preferably one where I can browse a list of changes over time (ie NOT just a tar and copy script!)

And also: WHY is there no feature like this in Ubuntu! Linux is so not ready for the desktop yet!

---

### Post by sdowney717 on 2008-10-31
[http://ubuntuforums.org/showthread.php?t=964988](http://ubuntuforums.org/showthread.php?t=964988)

I just figured out how to backup and restore my home folders and files.
granted it is a snapshot of my entire /home at a moment in time.

Why bother to backup the OS as it is easily reinstalled.
All you need is /home, so perhaps a daily script could be setup to overwrite copy /home/username on a daily basis.

As far as incremental backups of /home. maybe there is something better.

[http://www.cyberciti.biz/tips/flyback-time-machine-backup-software-for-linux.html](http://www.cyberciti.biz/tips/flyback-time-machine-backup-software-for-linux.html)

---

### Post by bytor4232 on 2008-10-31
> **blazemore said:**
> What can I use to do a daily backup to an external hard-drive, only overwriting files which have changed?
Preferably one where I can browse a list of changes over time (ie NOT just a tar and copy script!)

Look into rsync.  We use it on most of our 200 servers to replicate customer's installations.  We do the entire drive, here is the rsync command we use:  
```

/usr/bin/rsync -vvaH --delete --numeric-ids --exclude=/mirror --exclude=/proc /. /mirror/.

```
In terms of browsing, you will have to use a file manager, and sort by the date stamp.  You can also use the command "find" to display a list of changes for a certain date.

> **blazemore said:**
> And also: WHY is there no feature like this in Ubuntu! Linux is so not ready for the desktop yet!

Perhaps YOUR not ready for Linux.  I've been using it since 1998 exclusively, and have been pleased with it.  Just because you don't know how to do something doesn't mean it doesn't exist.

---

### Post by blazemore on 2008-11-02
No, I'm just saying, Vista has a very good backup app integrated. Linux has always been more cutting edge than Windows, so why not pioneer the most easy to use backup app (Turns out to be FlyBack)

---

### Post by gjosef on 2008-11-10
Is Flyback being actively maintained?

---

### Post by cdtech on 2008-11-10
It's a shame you don't like "tar". I use it specifically for my backup's and even incremental backup's: using the --newer flag. I end up with a daily, monthly, and a weekly compressed file which can be viewed using the zcat command. Then again I've always been a CLI person using GNU/Linux.

---

