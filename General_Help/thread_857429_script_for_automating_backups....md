---
title: "script for automating backups..."
date: 2008-07-12
forum: General Help
---

### Post by Mia_tech on 2008-07-12
could anyone help with a script for automating backups of my home directory, I want to be able to run a compressed backup of my home dir like 
```
tar -cvzf /media/share/backup/file.bkp.gz /home/username
```
let's say once a week, but I would like that the backups reflect the date on the file name and also delete previous backup and only leave the previous one....I would like to put the command in the ```
/etc/crontab
``` directory.....so the get done by themself and only check the logs...

thanks in advance

---

### Post by civillian on 2008-07-12
What you really want is a shell script which you can put into your /etc/crontab. I'm no expert on setting up tasks in cron, but the script itself should be easy enough

```

#!/bin/bash
#compress home directory
tar -cvzf /media/share/backup/file.bkp.gz /home/username
echo "backup created"

```

just copy that into a text file and save it as backup.sh or something (as long as it ends in .sh), then right click the .sh file and make it executable. 

This script will compress your /home/username to wherever you specify in the tar command (but I guess you knew that, having already written that bit).

To make it a cron job, you can add it to the /etc/crontab file by running 
```
sudo gedit /etc/crontab
``` 

and then, appending this line to the end
```
sh /pathto/backup.sh
```

you can choose when it runs using the syntax as it is described here [http://www.adminschoice.com/docs/crontab.htm#Crontab%20file]("http://www.adminschoice.com/docs/crontab.htm#Crontab%20file")

For example 
```

30 13   * * 1   root   sh /pathto/backup.sh
```

then save and that should set up your script to back up your home directory every monday at half past one. Of course you can set it to any time, day, month interval you like (all documented in the above link).

And /pathto/backup.sh is just wherever you saved your script to. On my computer /pathto/backup.sh would be substituded to ```
/home/civint/scripts/backup.sh
``` 

Heres how my /etc/crontab looks with that script added to it

> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
30 13   * * 1   root   sh /pathto/backup.sh
#


Hope this helps!

---

### Post by Mia_tech on 2008-07-12
not to take anything away from your explanation, but that the easy part I kind of wanted to append the date to the backup and delete the the old ones.....I know it is possible, I'm have to do some research...anyway thanks

---

### Post by Dr Small on 2008-07-12
Here should be a few pointer for your backup script:
```
date=$(date +%F)
tar -cvzf /media/share/backup/$date.bkp.gz /home/username
```

But as for deleteing the previous backup, that may take a little bit more thought and possibly some math behind it.

---

### Post by ladr0n on 2008-07-12
An alternative would be to save each file under the same name, overwriting the previous file.  The backup file's timestamp will reflect the time and date of its creation.  
If you really want the date in the filename, use dr small's method to insert the date.  In your backup script itself, include ```
rm -f /path/to/backupfile/directory/*
```
Make sure the backupfile will always be the only file in that directory, and you're all set.

--edit--
better idea: make backup first, then clear out old backups (in case of failure).
The whole script, still assuming that this is only file in the backup folder:
```

#!/bin/bash
#compress home directory
date=$(date +%F)
tar -cvzf /media/share/backup/$date.bkp.gz.new /home/username
echo "backup created"

rm -f /media/share/backup/*.bkp.gz
mv /media/share/backup/$date.bkp.gz.new /media/share/backup/$date.bkp.gz
echo "old backups removed"

```

---

### Post by Mia_tech on 2008-07-21
I came up with this...keep in mind that I'm not an experienced programmer...I would like to substitute the "new" and "old" for dates... if someone can improve on this.. you're welcome 
```
#!/bin/bash
#Backing up/compressing home directory
if [ -f "/media/winshare/backup/old.ubuntu.bkp.gz" ];

	then rm /media/winshare/backup/old.ubuntu.bkp.gz 
echo "old backup deleted!"
fi

if [ -f "/media/winshare/backup/new.ubuntu.bkp.gz" ];

	then mv -T /media/winshare/backup/new.ubuntu.bkp.gz /media/winshare/backup/old.ubuntu.bkp.gz
echo "new backup moved!"
fi

tar -czf /media/winshare/backup/new.ubuntu.bkp.gz /home/jorge
echo "backup finished!"
exit

```

---

### Post by Levander on 2008-07-24
> **Mia_tech said:**
> not to take anything away from your explanation, but that the easy part I kind of wanted to append the date to the backup and delete the the old ones.....I know it is possible, I'm have to do some research...anyway thanks

Like they've said, get the data with the 'date' command.

Then, to delete the old one, 'find' has some options that let you find files that are older than a specified date.  Pipe the results of the find command to 'xargs rm'.

---

### Post by ladr0n on 2008-07-25
Okay.  I think this should do basically what you want.  You get all of your backup files named by date, and only the old backup file(s) are removed.  The new backup is made before the old one is erased, so there's no chance of your system asploding during the backup and losing everything.  This is currently set to delete backups older than two weeks old.  Change the -atime argument in find to the number of days - 1 since your last backup (i.e. 13 for 2 weeks, 20 for 3 weeks, etc).

```
#!/bin/bash
#compress home directory
date=$(date +%F)
tar -cvzf /media/share/backup/$date.ubuntu.bkp.gz /home/username
echo "backup created"

find *.ubuntu.bkp.gz -atime +13 | xargs rm
echo "old backups removed"
```

---

### Post by Potatoj316 on 2008-07-25
crontab it easy, to edit the crontab type this command
```
crontab -e
```you can then add lines, 1 line per task to run, if you want to run every saturday@ noon than this works
```
00 12 * * 6 /path/to/script
```

also I believe rsync now has incremental backup.  You can create multiple backups and tell it to increment the previous and it will make hard links to any unchange file, so you can instantly restore any previous version of your system without using a lot of disk space

---

### Post by Mia_tech on 2008-07-25
ladr0n nicely done!..yet simple; just a question: is xargs used to pass the "rm" argument to the find command or vise versa?

thanks

---

### Post by Potatoj316 on 2008-07-25
it brakes up the list so rm can handle it

---

### Post by ladr0n on 2008-07-25
> **Potatoj316 said:**
> 
also I believe rsync now has incremental backup.  You can create multiple backups and tell it to increment the previous and it will make hard links to any unchange file, so you can instantly restore any previous version of your system without using a lot of disk space

That's really cool, but what if you have to restore from a backup because something got corrupted or deleted?  Just a thought...

---

### Post by Potatoj316 on 2008-07-25
To restore you just copy the backup from whichever version you want.  when copying hard links you will get the actual file, not a link.  Hard links take up negligable space so you can make many of them instead of many copies of the same file.  

Hardlinks are different from symbolic links.  In the world of Microsoft shortcuts are the same thing as unix symbolic links.  Hard links do not exist in Bill's Microsoft world.  Hard links are like another instance of the file but just pointing to the same disk space.  If you delete the original file and you had a hard link pointing to it, you get the effect of moving the file from the original place to where the hard link is.  If you deleted a file that a symlink pointed to you would just get a broken link.

---

### Post by Mia_tech on 2008-07-25
I will try rsync next...


thanks

---

### Post by Levander on 2008-07-26
> **Mia_tech said:**
> ladr0n nicely done!..yet simple; just a question: is xargs used to pass the "rm" argument to the find command or vise versa?

thanks

Very generally, xargs takes the output of 'find', and feeds it to the input of 'rm'. It's like running 'find' first, and then running 'rm' second.  And, the "| xargs" part in the middle is the magic that takes the output of 'find' and feeds it to the input of 'rm'.

ladr0n got the idea right.  You probably want to add the "-f" option to 'rm' so that you don't get errors reported when there are no old backups to be found by 'find'.

Also, in that script, you're gonna get a warning from 'tar' saying it's stripping leading slashes from filenames.  You could 'cd /' and then 'tar cjf home' instead of 'tar cjf /home' to get rid of that warning message.

In general, shell scripts you run from cron should have no output when they are successful.  This is because the output of cron jobs get mailed to you.  If it's successful, most people prefer just to be left alone.  Only if there's a problem do they want to be notified.  

But, I usually put a "--debug" command line option on my shell scripts so that I can see status output for successful runs when I deem it so desired.

---

### Post by Mia_tech on 2008-07-26
guys here's the final works... I modified the "find" command because actually there's no need to pass the argument to "rm" with "xargs"... the find command can do the work it supports "-delete" option
```

#!/bin/bash
#compress home directory
date=$(date +%F)
tar -cvzf /media/share/backup/$date.ubuntu.bkp.gz /home/user
echo "backup created"

find /media/share/backup -name *.ubuntu.bkp.gz -atime +21 -delete
echo "old backups removed"

```

it will delete any backup that were accessed 21 days from the start of today

---

### Post by Levander on 2008-07-26
Ah, I didn't know about the -delete option.  I'm gonna be modifying a couple of scripts I wrote to use that.

Personally though, I'd change the tar command.  v is going to list every single file that you backup.  A lot of unneeded output.  And, for archiving, size of the tarball is going to be important.  So, I'd use bzip2 instead of gzip compression, e.g., using the 'j' option instead of the 'z' option.  And, you're using absolute path names still, tar is going to have annoying output saying it's removing them.  Take the leading '/' off "/home/user" and use the '--directory /' which tells tar to archive relative pathnames from the '/' directory.

My suggestion for the tar command in that script:

```

tar cjf /media/share/backup/$host-$date.bkp.tar.bz2 --directory / home/user

```

---

### Post by jerome1232 on 2008-07-31
One thing I like to do when I make backups (mostly becuase one of them is a 24.7 GB behmoth bziped) is this:
```
tar cvvjf mytar.tar.bz2 /whatever > mytar.list
```

I like it for big archives because it makes it easy to figure out if a certain file is in that archive without spending ALOT of time to run tar with -t to list out it's contents.

---

