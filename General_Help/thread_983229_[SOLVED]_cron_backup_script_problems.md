---
title: "[SOLVED] cron backup script problems"
date: 2008-11-15
forum: General Help
---

### Post by BassKozz on 2008-11-15
I am having troubles with a little backup script I created and added to my crontab.
The script simply copies files over to another directory on a nightly basis.  I created this script a while back and this is what is used to look like:
```

#!/bin/bash
#Daily Backup script - daily-backup.sh
cp -au /media/backup-drive/Shares/WORK/ /media/backup-drive/Backups/WORK/Daily/
#
echo "Daily Backup Successful: $(date)" >> /media/backup-drive/Backups/WORK/mybackup.log

```
And here is the crontab entry:
```
# m h  dom mon dow   command

###WORK###
#Daily WORK Backup
01 01 * * * /media/backup-drive/Backups/WORK/Daily/daily-backup.sh
```
And it seems to work fine, but I recently updated this script to copy the verbose output of the **cp** command to another log file so I could keep tabs of what files are being copied over, so the new script looks like this:
```

#!/bin/bash
#Daily Backup script - daily-backup.sh
echo "###########################" >> daily-backup.log
echo "Daily Backup Begin: $(date)" >> daily-backup.log
cp -auv /media/backup-drive/Shares/WORK/ /media/backup-drive/Backups/WORK/Daily/ >> daily-backup.log
echo "Daily Backup End: $(date)" >> daily-backup.log
echo "###########################" >> daily-backup.log
#
echo "Daily Backup Successful: $(date)" >> /media/backup-drive/Backups/WORK/mybackup.log

```
I simply updated the script (same filename) with the new code above, and I didn't make any changes to my crontab entry.

Now when I manually run the script ```
./daily-backup.sh
```
it works fine, but for some reason when it's run by my crontab it is as if it's using the old version of the script because it doesn't output the verbose of **cp** to the ***daily-backup.log*** file like it should. Yet it still does output to the ***mybackup.log*** file so I know it is running.

When you add a script to crontab is a copy of the script sent somewhere so that crontab will continue to run it (older version)?  Is there a way to update crontab so that it runs the newer version of the script?

---

### Post by Kellemora on 2008-11-15
Hi Bk

Do you have a BLANK LINE in your script AFTER the
echo daily backup successful
line?????

MUST HAVE a blank line there!

TTUL
Gary

---

### Post by BassKozz on 2008-11-15
Yes I think I do, when I access the file "nano daily-backup.sh" the cursor is at the line after that "echo "Daily Backup Successful: $(date)" >> /media/backup-drive/Backups/WORK/mybackup.log" line.

Just to be sure I entered another "empty" line after that, and placed it in crontab, and again, the same problem, output is going to ***mybackup.log*** but not to ***daily-backup.log*** unless I manually run the script "./daily-backup.sh".

I also noticed there are two other files in the script's directory that I didn't notice before:
[b]daily-backup.sh~
daily-backup.sh.save[/b]
So I went ahead and deleted (rm) both of them, placed another line in crontab to test, and STILL the same issue :confused:

---

### Post by Kellemora on 2008-11-15
Hi Bk

On the first example you have the PATH to "mybackup.log"

In the second example no PATH to "daily-backup.log" is given!

Try adding the PATH to "daily-backup.log" and see if that fixes it!

TTUL
Gary

---

### Post by BassKozz on 2008-11-15
The reason I didn't have a path for "daily-backup.log" is because it resides in the same directory as the script, whereas "mybackup.log" resides in a different directory. 

But none-the-less, I made the change and added a path for "daily-backup.log" and still the same issue, if I run manually ```
./daily-backup.sh
```
it works fine and outputs to both **daily-backup.log** & **mybackup.log**, but if it's run via crontab it doesn't output to **daily-backup.log**.:confused:

---

### Post by BassKozz on 2008-11-16
:bump:

---

### Post by Kellemora on 2008-11-16
Hi BK

I'm a noob and just learning this crontab stuff myself and hit many of the same snags you are.

I could only offer what I've learned so far!

Sorry, but whatever is keeping it from working is above what I have thus far learned.

Maybe if you make a new post over in the more advanced areas of the web site, one of the Guru's can figure it out!

Sorry

TTUL
Gary

---

### Post by snova on 2008-11-16
I don't know much about cron, but is it possible that your script is being run in a directory that you don't have permission to create files in?

---

### Post by BassKozz on 2008-11-16
> **Kellemora said:**
> Hi BK

I'm a noob and just learning this crontab stuff myself and hit many of the same snags you are.

I could only offer what I've learned so far!

Sorry, but whatever is keeping it from working is above what I have thus far learned.

Maybe if you make a new post over in the more advanced areas of the web site, one of the Guru's can figure it out!

Sorry

TTUL
Gary
Thats alright Gary, I appreciate all your effort in helping me.
If I don't find a solution soon I might open up a new thread in the "General Help" Forum.
Thanks again,
-BassKozz

> **snova said:**
> I don't know much about cron, but is it possible that your script is being run in a directory that you don't have permission to create files in?
Thanks for the comment snova, but I think we already disproved that back in [post #5]("http://ubuntuforums.org/showpost.php?p=6188093&postcount=5") by adding a full-path to the ***daily-backup.log***.

So the script now looks like this:
```
#!/bin/bash
#Daily Backup script - daily-backup.sh
echo "###########################" >> daily-backup.log
echo "Daily Backup Begin: $(date)" >> daily-backup.log
cp -auv /media/backup-drive/Shares/WORK/ /media/backup-drive/Backups/WORK/Daily/ >> /media/backup-drive/Backups/WORK/Daily/daily-backup.log
echo "Daily Backup End: $(date)" >> daily-backup.log
echo "###########################" >> daily-backup.log
#
echo "Daily Backup Successful: $(date)" >> /media/backup-drive/Backups/WORK/mybackup.log
```
Notice the full-path for ***daily-backup.log***

---

### Post by bapoumba on 2008-11-17
Moved to General Help.

---

### Post by geirha on 2008-11-17
Check your mail to see if cron has sent you messages about the script. If it is run in root's cron do ```
sudo mail
``` to read such mails, and just mail if it's run in your cron.

Commands run by cron is run from / by default, so if you don't specify a full path to files, they'll be relative to /. Do you perhaps have a /daily-backup.log now?

---

### Post by psusi on 2008-11-17
> **BassKozz said:**
> 
Thanks for the comment snova, but I think we already disproved that back in [post #5]("http://ubuntuforums.org/showpost.php?p=6188093&postcount=5") by adding a full-path to the ***daily-backup.log***.


The updated script you posted still does NOT have the full path for daily-backup.log, only for mybackup.log.

cron runs the script in your home directory so that's where daily-backup.log should be.

---

### Post by BassKozz on 2008-11-17
> **psusi said:**
> The updated script you posted still does NOT have the full path for daily-backup.log, only for mybackup.log.

cron runs the script in your home directory so that's where daily-backup.log should be.

: DOH :
Your right... I forgot to put the full path for the other lines of the script (besides the verbose output of the 'cp' command)
Thanks psusi !!! :)

Script now looks like this:
```
#!/bin/bash
#Daily Backup script - daily-backup.sh
echo "###########################" >> /media/backup-drive/Backups/WORK/Daily/daily-backup.log
echo "Daily Backup Begin: $(date)" >> /media/backup-drive/Backups/WORK/Daily/daily-backup.log
cp -auv /media/backup-drive/Shares/WORK/ /media/backup-drive/Backups/WORK/Daily/ >> /media/backup-drive/Backups/WORK/Daily/daily-backup.log
echo "Daily Backup End: $(date)" >> /media/backup-drive/Backups/WORK/Daily/daily-backup.log
echo "###########################" >> /media/backup-drive/Backups/WORK/Daily/daily-backup.log
#
echo "Daily Backup Successful: $(date)" >> /media/backup-drive/Backups/WORK/mybackup.log
```

---

