---
title: "Backup script problems"
date: 2008-09-27
forum: General Help
---

### Post by flxfxp on 2008-09-27
Hey,

I'm running ubuntu server 8.04 and i'm having some problems regarding my backup script. I took a nice script from [http://allthingsgreat1.blogspot.com/2008/04/ongoing-backup-with-tar-cron-ftp-and.html](http://allthingsgreat1.blogspot.com/2008/04/ongoing-backup-with-tar-cron-ftp-and.html)

Mine currently looks like this:

```
#!/bin/sh
# full and incremental backup script
# created 07 February 2000
# Based on a script by Daniel O'Callaghan
# and modified by Iain McMullin>

#Change the 5 variables below to fit your computer/backup (currently set for Ubuntu)

COMPUTER=domus # name of this computer
DIRECTORIES="/data/capsule" # directories to backup
BACKUPDIR=/data/backups # where to store the backups
TIMEDIR=/data/backups/last-full # where to store time of full backup
TAR=/bin/tar # name and locaction of tar
FILENAME="" # placeholder for filename

#You should not have to change anything below here

PATH=/usr/local/bin:/usr/bin:/bin
DOW=`date +%a` # Day of the week e.g. Mon
DOM=`date +%d` # Date of the Month e.g. 27
DM=`date +%d%b` # Date and Month e.g. 27Sep

# On the 1st of the month a permanet full backup is made
# Every Sunday a full backup is made - overwriting last Sundays backup
# The rest of the time an incremental backup is made. Each incremental
# backup overwrites last weeks incremental backup of the same name.
#
# if NEWER = "", then tar backs up all files in the directories
# otherwise it backs up files newer than the NEWER date. NEWER
# gets it date from the file written every Sunday.

# clean out the daily directory
rm $BACKUPDIR/current/*.gz

# Monthly full backup
if [ $DOM = "01" ]; then
NEWER=""
FILENAME=$COMPUTER-$DM.tar.gz
$TAR $NEWER -czf $BACKUPDIR/$COMPUTER-$DM.tar.gz $DIRECTORIES
fi

# Weekly full backup
if [ $DOW = "Sun" ]; then
NEWER=""
NOW=`date +%d-%b`

# Update full backup date
echo $NOW > $TIMEDIR/$COMPUTER-full-date
FILENAME=$COMPUTER-$DOW.tar.gz
$TAR $NEWER -czf $BACKUPDIR/$COMPUTER-$DOW.tar.gz $DIRECTORIES

# Make incremental backup - overwrite last weeks
else

# Get date of last full backup
NEWER="--newer `cat $TIMEDIR/$COMPUTER-full-date`"
FILENAME=$COMPUTER-$DOW.tar.gz
$TAR $NEWER -czf $BACKUPDIR/$COMPUTER-$DOW.tar.gz $DIRECTORIES
fi

# copy new backup .gz file to directory for upload
cp $BACKUPDIR/$FILENAME $BACKUPDIR/current/$FILENAME
```

However, when I run it, I get this output:
```
rm: cannot remove `/data/backups/current/*.gz': No such file or directory
cat: /data/backups/last-full/domus-full-date: No such file or directory
/bin/tar: Substituting 1901-12-13 21:05 for unknown date format `-czf'
/bin/tar: You must specify one of the `-Acdtrux' options
Try `/bin/tar --help' or `/bin/tar --usage' for more information.
cp: cannot stat `/data/backups/domus-Sat.tar.gz': No such file or directory

```
What is wrong with my script?

Thanks in advance!

Regards,

Dennis

p.s: I would also like the latest backup to be uploaded to a ftp, can anyone offer me a example? Thanks again.

---

### Post by flxfxp on 2008-09-27
Nevermind, I was being stupid. I already fixed it myself plus a ftp uploader using yafc :)

Thanks tho!

---

