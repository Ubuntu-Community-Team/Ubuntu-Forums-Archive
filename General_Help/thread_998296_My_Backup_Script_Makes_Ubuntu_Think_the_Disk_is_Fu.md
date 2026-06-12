---
title: "My Backup Script Makes Ubuntu Think the Disk is Full"
date: 2008-11-30
forum: General Help
---

### Post by z08595 on 2008-11-30
I've been trying to get automated backups to work using rsync and cron.  I have Hardy Heron running on my laptop, and wish to backup to a partition on a machine running Windows XP (actually, I have to use two separate partitions with FAT32 and NTFS formatting due the amount of data I'm backing up).

I set up a shared folder on the Windows machine (thecore), and was able to connect to it on my Ubuntu laptop following [this thread]("http://ubuntuforums.org/showthread.php?t=202605").

I added the machine name to my /etc/hosts file:
```
192.168.1.100 thecore
```

I created two folders, /thecore and /thecore2, for the two shared partitions.

I also added some lines in my /etc/fstab file:
```
/thecore/thecore       /thecore smbfs exec 0 0
/thecore/thecore2	/thecore2 smbfs exec 0 0

```

At this point, I was able to simply access the shared folders via /thecore and /thecore2.

I set up a script to manage my backups:
```
#!/bin/sh

OPTS="-a -z -v --delete --stats"

export PATH=$PATH:/bin:/usr/bin:/usr/local/bin

rsync $OPTS /shared/Documents /thecore
rsync $OPTS /shared/Music /thecore2
```

I ran the backup script as root several times (if I'm not using sudo it will create the folders but not copy the actual files).  Over time, my ext3 partition with my Ubuntu installation went from ~7.5 GB to 20 GB, 100% full.  The files I was transferring were on another partition of my laptop, so don't exist on the ext3 partition.  After the partition was seen as 100% full, I was unable to log in any more.  I tried the tune2fs trick outlined [here]("http://ubuntuforums.org/showthread.php?t=633261"), but was only able to take my disk down to 98% full.  

I eventually figured out that the system was counting the several GB in /thecore and /thecore2 as actually being on the disk.  I deleted these two folders, and was able to boot, but since have had to stop my backups.

Does anyone have any suggestions as to how I can avoid this problem?

---

