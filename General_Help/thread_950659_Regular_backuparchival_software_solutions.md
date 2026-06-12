---
title: "Regular backup/archival software solutions?"
date: 2008-10-17
forum: General Help
---

### Post by enigma_0Z on 2008-10-17
I had written a script to automatically back up my "Documents" folder (personal, school, church, work documents, etc.) to an external hard disk periodically...

Specifically, I wrote the scripts so they were scheduled with at. It evolved into something fairly advanced, I had my backup schedule set to run every four hours for an incremental, and if there was a problem (eg. AC not connected, drive not connected) then it would try every hour until it worked. I chose at because it will run past-due jobs when the system boots up instead of skipping them like cron.

A separate script I had ran a full backup once a week, with the same retry policy as the incremental backup. The scripts *just worked* and would send me an email through the unix mail spool when a backup was completed or failed for the first time since a good backup. 

The incremental backup script was rather sophisticated in a hackish way--it would check files against the date of the last backup, as well as a list of previously backed up files so that it got new files and modified files but didn't get whole "modified" directories when only one file in the dir changed.

Anyway, I did all this work and like I said, the scripts just worked and I would, as Ron popeil would say, "Set it and forget it". I would check once in a while because I'm paranoid, but usually it was doing fine. It had it's issues (eg. a directory was locked from a backup process that was running and killed when the lappy was shut down), but for the most part, it worked quite well.

Well, my Dell Vostro's nVidia card self-destructed and I bought an external SATA to USB adapter to get my stuff off the hdd in the meantime. The adapter fried the motor in my disk, so now I have a (nearly full) 160 GB paperweight. The problem is that I backed up my documents, but I did not back up my scripts to do the backups!!!

So, rather than doing the work all over again, I was wondering if there's a good, robust piece of backup software that I can use instead? What are the community recommendations on Linux-based automated backup software?

Thanks, and sorry that was so long!

---

### Post by hyper_ch on 2008-10-17
I use my own little script, it's actually very simple...

it uses rsync to synchronize data and then it uses hardlinks to create a snapshot and after XX days it deletes old snapshots... all you need to to do is

(1) set the amount of days after which old snapshots shall be deleted
(2) make a cron that runs the script regurarly
(3) set your exclude list of what directories shall not be synced

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=**************
MYSQLHOST=localhost
MYSQLBACKUPDIR=/mysql_backup
EXCLUDES=/backup/backup_exclude        # File containing exludes
DAYS=90         # After how many days shall the backups be deleted?

# PATH VARIABLES
CP=/bin/cp;
MK=/bin/mkdir;
DATE=/bin/date;
RM=/bin/rm;
GREP=/bin/grep;
MYSQL=/usr/bin/mysql;
MYSQLDUMP=/usr/bin/mysqldump;
RSYNC=/usr/bin/rsync;
TOUCH=/bin/touch;
FIND=/usr/bin/find;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING CURRENT DATE / TIME
$MK $BACKUPDIR/current
$MK $BACKUPDIR/old
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
MKDIR=$BACKUPDIR/old/$NOW/
$MK $MKDIR

# CREATE MYSQL BACKUP
# Remove existing backup dir
$RM -Rf $MYSQLBACKUPDIR

# Create new backup dir
$MK $MYSQLBACKUPDIR

#Dump new files
for i in $(echo 'SHOW DATABASES;' | $MYSQL -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST|$GREP -v '^Database$'); do
  $MYSQLDUMP                                                    \
  -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST                         \
  -Q -c -C --add-drop-table --add-locks --quick --lock-tables   \
  $i > $MYSQLBACKUPDIR/$i.sql;
done;

# RUN RSYNC INTO CURRENT
$RSYNC                                                          \
        -avzp --delete --delete-excluded                        \
        --exclude-from="$EXCLUDES"                              \
        /                                                       \
        /$BACKUPDIR/current ;

# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current

# MAKE HARDLINK COPY
$CP -al $BACKUPDIR/current/* $MKDIR

# REMOVE OLD BACKUPS
for file in "$( $FIND $BACKUPDIR/old/ -maxdepth 1 -type d -mtime +$DAYS )"
do
  $RM -Rf $file
done

exit 0

```

backup_exclude
```

/backup/
/bin/
/boot/
/cdrom/
/dev/
/initrd/
/initrd.img
/ionitrd.img.old
/lib/
/lost+found/
/media/
/mnt/
/opt/
/proc/
/sbin/
/srv/
/sys/
/tmp/
/usr/
/var/backups/
/var/cache/
/var/crash/
/var/local/
/var/lock/
/var/log/
/var/opt/
/var/run/
/var/spool/
/var/tmp/
/vmlinuz
/vmlinuz.old

```

If you don't run mysql, you can also comment that part.

---

### Post by ilrudie on 2008-10-17
Seems like I always answer backup questions right after hyper_ch but I'd suggest looking into [bacula]("http://www.bacula.org/en/").

---

