---
title: "Backup specific folders"
date: 2014-12-11
forum: Hardware
---

### Post by desantos2 on 2014-12-11
Which tool do I use to backup certain folders on my Ubuntu Server 14 system.

I would like to have specific folders copied from this location '/files' in /dev/sda to /dev/sdb each day for 7 days then once those 7 days are up have the backup repeat and overwrite the files copied to /dev/sdb/ from the past 7 days.  I would also like this ran at 2am in the morning.


H/W path        Device      Class          Description
======================================================
/0/1/0.0.0      /dev/sda    disk           500GB ST3500620AS
/0/2/0.0.0      /dev/cdrom  disk           DVD+-RW TS-H653G
/0/3/0.0.0      /dev/sdb    disk           500GB M3 Portable

Thanks in advance for any help

---

### Post by kpatz on 2014-12-11
You could use cp -a.  You'll need to have the two drives mounted.  For this example we'll assume they're mounted as /mnt/sda and /mnt/sdb, and you want to backup files/dir1, files/dir2, and files/dir3 only from /mnt/sda to /mnt/sdb.  The backups will be stored in /mnt/sdb/files/1 thru 7 (based on day of week), and a prior backup is deleted before being overwritten.  I use cp -av so you get verbose output (seeing what was copied and where).

If you could post the output of 'mount', and/or your /etc/fstab file, we can tweak this script to more accurately reflect what /dev/sda and /dev/sdb really are and where they're mounted.

```

#!/bin/bash

#Specify source and target directories here.  Use directories where /dev/sda and /dev/sdb are mounted.

SRC="/mnt/sda/files"    # Files folder on mounted /dev/sda
DIRS="$SRC/dir1 $SRC/dir2 $SRC/dir3"   # Directories to backup
DEST=/mnt/sdb/files/`date "+%u"`        # Place to backup to including day of week 1-7

test -d "$DEST" && rm -rf "$DEST"          # Delete backup dir from a week ago if it exists

cp -av $DIRS "$DEST"     #Do the backup

```

If you want to backup to another machine instead of a 2nd drive in the same machine, you could use rsync instead of cp.

If you want to backup everything in /mnt/sda/files, instead of specific directories, you could either have DIRS="$SRC" or use cp -av "$SRC" "$DEST".

---

### Post by weatherman2 on 2014-12-11
rsync is awesome.

I also use rdiff-backup, which uses the same rsync library but with differential backup.  That means it saves file history: changes and deleted files.  For example, if you do this:

```

rdiff-backup /files/original-folder /backup-disk/backup-folder

```

Every day, after seven days /backup-disk/backup-folder will be an exact copy of the original folder - but you can also retrieve any version of any file from any of those days, even if you erased it.

If you want to save only seven days of history, you can purge it every day as part of your backup:

```

rdiff-backup --remove-older-than 7D /backup-disk/backup-folder

```

[http://www.nongnu.org/rdiff-backup/examples.html](http://www.nongnu.org/rdiff-backup/examples.html)

---

