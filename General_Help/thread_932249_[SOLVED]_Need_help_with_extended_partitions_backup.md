---
title: "[SOLVED] Need help with extended partitions backup"
date: 2008-09-28
forum: General Help
---

### Post by kozlovsk on 2008-09-28
Hi!

I'm trying to follow the [guide]("http://www.partimage.org/Partimage-manual_Backup-partition-table") on the Partimage page to backup MBR and the entries of the extended partitions.

MBR backup is OK, but after 

sudo sfdisk -d /dev/hda > backup-hda.sf

I get "Permission denied" error.

There is a [manual]("http://manpages.ubuntu.com/manpages/hardy/man8/sfdisk.html") in Ubuntu documentation pages, according to which this command should work.

Any ideas?

---

### Post by jigsaws on 2008-09-28
Try

sudo su
sfdisk -d /dev/hda > backup-hda.sf

Probably you have no permission to write to current directory from user (only 'sfdisk -d /dev/hda' is running as root).

---

### Post by kozlovsk on 2008-09-28
It worked, thanks a lot!

In Partimage guide the working directory is /root/partition-backup

to save there I needed to do 
sudo su 
first, but it was not needed when saving to the Home derectory

---

