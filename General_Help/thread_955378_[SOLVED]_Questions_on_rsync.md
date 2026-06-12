---
title: "[SOLVED] Questions on rsync"
date: 2008-10-22
forum: General Help
---

### Post by djbushido on 2008-10-22
Hello!
I'm not new to this linux stuff, but I am having trouble wrapping my head around the rsync backup engine.
My questions are:

Can i create an event for (ana)chron to backup my data every day when i log in? Also, this should just be a differential backup.

Can i set this to backup to a separate partition on my drive?

How do i restore my backup from an **ALTERNATE** liveCD? (Preferably deleting the content previously on the drive, or removing what has changed)

Thank you for your help, I truly appreciate it since this will now be my third install.

Oh and by the way, I am doing this from a desktop computer, 8.04.

---

### Post by djbushido on 2008-10-23
Bump, please help me, I'm a bit confused

---

### Post by vanadium on 2008-10-23
> Can i create an event for (ana)chron to backup my data every day when i log in? Also, this should just be a differential backup.
Yes

> Can i set this to backup to a separate partition on my drive?
Yes

> How do i restore my backup from an ALTERNATE liveCD? (Preferably deleting the content previously on the drive, or removing what has changed)

I do not understand this question.

* See "man rsync" for a well (and quite newbie friendly) written explanation of rsync.
* Try to be specific in your questions to get specific help.
* Preferably handle one problem in one thread with a descriptive heading.

---

### Post by djbushido on 2008-10-23
I apologize for my questions.
What I meant was that I wasn't sure how to restore a backup if my computer crashed with rsync.

---

### Post by vanadium on 2008-10-23
You use rsync typically for backing up and restoring user data. For example, I have a directory Documents, and I make a backup of the data using the command

```

rsync -av --delete /home/vanadium/Documents /media/usb/Documents

```

The first time, all of the data need to be copied. Subsequently, this goes very fast because only the differences are copied.

In the event of a disaster, I reinstall and I can restore the documents to the harddisk with a very similar command, that just changes source and destination (*I also omit --delete which could be dangerous in case I make a mistake*)

```

rsync -av /media/usb/Documents /home/vanadium/Documents

```

rsync cannot be used to backup and restore an entire system. However, trying to backup your entire system is tedious and is not quite useful. Just reinstalling Ubuntu takes less than an hour.

Obviously, you can use cron to automatically launch rsync at a preset time, but I am not experienced with it.

---

### Post by djbushido on 2008-10-24
Okay, thank you! What I meant was that I had installed the bcm43xx firmware (a task in itself) and needed that to access the internet since i don't have a long enough ethernet cable. I think what i can do is to create the backup in a folder inside the partition, and the extracted driver stuff inside another folder in the same partition. Or, do you know if rsync is included on the installer cd that i can use that?
Also, does rsync allow for compression of backups? Like can I set it to back up my files to a .tar.bz2?

---

### Post by hyper_ch on 2008-10-24
> **djbushido said:**
> Can i create an event for (ana)chron to backup my data every day when i log in? Also, this should just be a differential backup.
Yes, but I'd rather setup a script that runs at boot to do the backup.

> **djbushido said:**
> Can i set this to backup to a separate partition on my drive?
That's simple :) just mount the separate partition into your local filesystem (I have used /backup on my machine) and sync into it.

What I do is to make incremental snapshot-style backups. That means I make hardlink copies of my backed up files so that I have for each backup a "full" backup copy.

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=***************
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
It's very simple that script. First I define a few things (where I want to have backups to, how long I want to keep them, ....)
I also have mysql databases, so I need to back them up also - you probably can just skip that.

Then I also say what shall not be backed up:

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

So basically you just need to create those two files, set path accordingly, setup what you want to backup, setup what you don't want to...

Then make the backup.sh script executable and run it by cron or anacron or make an init.d entry for it...

---

### Post by djbushido on 2008-10-24
Okay, so this looks good, but I'm not sure what i would need to omit, other than path variables, since I don't have databases.
Help appreciated!

---

### Post by hyper_ch on 2008-10-24
That's the mysql part that you could remove from the script (or comment out)
```

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

```

And running the script at start up you would
(1) create a "backup_boot.sh" script at /etc/init.d/ containing
```

#!/bin/bash
sh /backup/backup.sh

```
of course adjust the script path

(2) add it to bootup
```

sudo update-rc.d backup_boot.sh defaults
```

This will only run upon booting and not when you log into your session. However you could also just set cron to run at given intervals or anacron :)

---

### Post by djbushido on 2008-10-24
Thank you!
I will set this up soon!
I appreciate your help!

---

### Post by televisi on 2009-05-07
Hi hyper_ch,
Thanks for this info, your incremental backup script helps me a lot.

Now 1 quick question, if client using Windows XP, how can they see the backup files? (from your example, they are under old/<date> folder)...as they are just links to the same inode in Linux, but when you open it in Windows using Samba connection, they are just bunch of random name directory (ie: 2RNSRZ~7, 2XC1GQ~0, etc)

Should I remove the link beforehand to some temporary directory?

Thanks

> **hyper_ch said:**
> Yes, but I'd rather setup a script that runs at boot to do the backup.


That's simple :) just mount the separate partition into your local filesystem (I have used /backup on my machine) and sync into it.

What I do is to make incremental snapshot-style backups. That means I make hardlink copies of my backed up files so that I have for each backup a "full" backup copy.

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=***************
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
It's very simple that script. First I define a few things (where I want to have backups to, how long I want to keep them, ....)
I also have mysql databases, so I need to back them up also - you probably can just skip that.


---

### Post by televisi on 2009-05-16
Apparently I put way too long directory name in Linux, which confuse XP/Vista.

If I put something like **[COLOR="Red"]2009-05-16_20:48[/COLOR]** directory name, XP/Vista detects it as **[COLOR="Red"]2RNSRZ~7[/COLOR]**.

Once I changed to **backup0 / backup1**, XP/Vista able to read it properly, yay!

> **televisi said:**
> Now 1 quick question, if client using Windows XP, how can they see the backup files? (from your example, they are under old/<date> folder)...as they are just links to the same inode in Linux, but when you open it in Windows using Samba connection, they are just bunch of random name directory (ie: 2RNSRZ~7, 2XC1GQ~0, etc)

---

### Post by scheuref on 2012-09-19
Hello

you can also look at a script that i wrote to backup the  whole disk with rsync here:  [http://blog.pointsoftware.ch/index.php/howto-local-and-remote-snapshot-backup-using-rsync-with-hard-links/](http://blog.pointsoftware.ch/index.php/howto-local-and-remote-snapshot-backup-using-rsync-with-hard-links/)

It  uses file deduplication thanks to hard-links, uses also MD5 integrity  signature, 'chattr' protection, filter rules, disk quota, retention  policy with exponential distribution (backups rotation while saving more  recent backups than older).
It was already used in Disaster Recovery  Plans for banking companies, in order to replicate datacenters, using  only little network bandwidth  and transport encryption tunnel.

Can be used locally on each servers or via network on a central remote backup server.
windows server could also be backuped by using a linux box that mount smb shares from them.

i hope it will be useful to you guys

francois

---

### Post by televisi on 2012-10-20
Hi scheuref,
Thanks for this, will definitely check out your blog :)

---

