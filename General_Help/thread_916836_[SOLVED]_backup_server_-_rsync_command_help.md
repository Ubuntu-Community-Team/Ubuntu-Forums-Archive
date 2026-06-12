---
title: "[SOLVED] backup server - rsync command help"
date: 2008-09-11
forum: General Help
---

### Post by elj4176 on 2008-09-11
I have a 2 TB Terastation that I need to backup. It has roughly 700GB of data on it and a small portion of the data changes on a weekly basis. I cannot install anything on the terastation (closed OS) such as a bacula client.
My thoughts are to build an ubuntu server with hot swappable 1 TB sata drives for the storage and use rsync to write just the changes to the sata drives once the initial copy is made. I'll take the drives offsite and rotate 2 or 3 drives for the backups. The Tera and the backup server will be moved to their own GB switch for better throughput.
I've used rsync before but I'm not sure of the command syntax I would need. I'll mount the Terastations drives to the filesystem on the backup server to say "/mnt/tera". The other thing to mention is that most of the data that needs to be backed up was created on Macs and they have some odd names and extensions that a windows backup solution had trouble with.

Something like this:

sudo rsync -avri --log-file=/var/log/bu.log /mnt/tera/ /mnt/sata/

tera is source
sata is dest

This would be run as an entry in the crontab. I'm not sure what parameter to use for just changes. Thanks for any input here.

---

### Post by HalPomeranz on 2008-09-11
You may find the following useful:

[http://ubuntuforums.org/showpost.php?p=4980160&postcount=4](http://ubuntuforums.org/showpost.php?p=4980160&postcount=4)

---

### Post by Titan8990 on 2008-09-11
Here is what I use:

```
jordan@einstein:/scripts$ cat rsync.sh
#!/bin/sh

# %Y     year
# %m     month (01..12)
# %d     day of month (e.g, 01)
# %s     seconds since 1970-01-01 00:00:00 UTC

# Variable for the Program
BACKUPDIR=/
THEDATE=`date '+%Y%m%d-%s'`
LOGDIR=/var/log/backup
EXCLUDEFILE=/scripts/exclude
LOGFILE=/var/log/backup/rsync-$THEDATE.log
GZFILE=/var/log/backup/rsync-$THEDATE.gz
DESTINATION=/media/backup/backup0
LAST=/media/backup/backup5
MNTPOINT=/media/backup/
BACKUPD=/dev/sda1

#Check to make sure that our backup drive is mounted - To be included later


#If the log directory does not exist then create it

if [ ! -d $LOGDIR ]; then
    mkdir -p $LOGDIR
fi

#If the destination directory does not exist then create it

if [ ! -d $DESTINATION ]; then
        mkdir -p $DESTINATION
fi

#Rotate the backups

rm -rf $LAST
mv /media/backup/backup4 $LAST
mv /media/backup/backup3 /media/backup/backup4
mv /media/backup/backup2 /media/backup/backup3
mv /media/backup/backup1 /media/backup/backup2
cp -al $DESTINATION /media/backup/backup1

#Now run rsync to backup the filesystem

rsync -avr --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE $BACKUPDIR $DESTINATION

# gunzip the logfile
gzip -c $LOGFILE > $GZFILE

# delete the original, uncompressed logfile
rm $LOGFILE
```

It was based on a tutorial in the howto section.

Here is my exclude:

```
jordan@einstein:/scripts$ cat exclude 
/proc/
/sys/
/tmp/
/media/

```

The most important part of the exclude IMO is the /media directory. Without exlcuding this your backups will multiply and take much longer to do (assuming that your backup media is mounted to /media).

---

### Post by elj4176 on 2008-09-11
Thanks for the replies! I think I have what I need.

---

