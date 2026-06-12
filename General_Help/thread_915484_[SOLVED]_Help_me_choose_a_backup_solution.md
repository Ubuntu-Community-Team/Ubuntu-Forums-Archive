---
title: "[SOLVED] Help me choose a backup solution"
date: 2008-09-09
forum: General Help
---

### Post by mwsherman on 2008-09-09
Hi community,

I've spent my free time over the last few days searching for a suitable Ubuntu backup solution, but with no success. I've found tons of options, but none of them will meet my basic criteria:

1) Allow me to specify what folders to backup.
2) Will backup to an external hard drive.
3) Will report an error if something goes wrong with the backup (and not require me to manually view a log file everyday)
4) Will compress the backup.
5) Allows for incremental backups.
6) Will warn me when I am running low on space on my backup drive.

I would prefer GUI, but I'll use the terminal if I have to.

I almost went with sbackup, but the critical issues it has (writing to the local hard drive when the external is not mounted, not informing the user if a backup does not complete successfully) make me extremely wary of it. I've looked into other options as well, but nothing has fit these 6 very basic criteria.

I'd rather not learn scripting just to do this task, and I'm not sure I could realistically do something that fit these 5 criteria (for example, if I have a script archiving backups from rdiff-backup, I either lose the incremental backup feature or I have to uncompress and recompress everything everyday, eliminating the usefulness of compression. Right?)

So....any ideas? I'm admittedly getting a bit frustrated with this search...I feel like I'm missing something extremely obvious--or is Ubuntu just really lacking in this specific area?

Thanks.

---

### Post by quibbler on 2008-09-10
> **mwsherman said:**
> Hi community,

I've spent my free time over the last few days searching for a suitable Ubuntu backup solution, but with no success. I've found tons of options, but none of them will meet my basic criteria:

1) Allow me to specify what folders to backup.
2) Will backup to an external hard drive.
3) Will report an error if something goes wrong with the backup (and not require me to manually view a log file everyday)
4) Will compress the backup.
5) Allows for incremental backups.
6) Will warn me when I am running low on space on my backup drive.

I would prefer GUI, but I'll use the terminal if I have to.

I almost went with sbackup, but the critical issues it has (writing to the local hard drive when the external is not mounted, not informing the user if a backup does not complete successfully) make me extremely wary of it. I've looked into other options as well, but nothing has fit these 6 very basic criteria.

I'd rather not learn scripting just to do this task, and I'm not sure I could realistically do something that fit these 5 criteria (for example, if I have a script archiving backups from rdiff-backup, I either lose the incremental backup feature or I have to uncompress and recompress everything everyday, eliminating the usefulness of compression. Right?)

So....any ideas? I'm admittedly getting a bit frustrated with this search...I feel like I'm missing something extremely obvious--or is Ubuntu just really lacking in this specific area?

Thanks.
Have a look at QuickStart and see if that means most of your needs.
[http://quickstartdownload.pbwiki.com/QuickStart+Help](http://quickstartdownload.pbwiki.com/QuickStart+Help)

Regards quibbler

---

### Post by hyper_ch on 2008-09-10
I'd use rsync as incremental updates are simple.
Also with the power of hardlinks you can easily make snapshot-stlye backups.

When running the rsync script in a cron you can have sent you the whole thing by email. At the end of the script you can also run a df -l and it will then also tell you how much space you used.

but compression is a problem. Either you compress it all and do a full backup or you do not compress it and make an incremental backup.

---

### Post by mwsherman on 2008-09-11
Thanks for the feedback.

Quickstart doesn't do incremental. It also seems to place the backups on your desktop--I see nothing in the documentation regarding a target location for the backups, except a question about backup files on the desktop. It also apparently does not tell you when the backup fails : [http://quickstart.phpbb.net/viewtopic.php?f=8&t=97](http://quickstart.phpbb.net/viewtopic.php?f=8&t=97)

Rsync is a no-go because of lack of compression/incrimenting. And I still have to manually view the log file everyday to check it for errors, right? Can I get an email of just errors (can I even do that without running a mail server on my computer?)? It also wont warn me if I'm running low on space unless I write a script to check for space or something, right?

I'm not intimately familiar with all the features of rsync, so maybe I'm wrong about some of my assumptions. But I'm not completely naive--I have played with it. And I'd have to learn a bunch of stuff to do this...not that I have a problem with that, but it still seems really bad that the Ubuntu community has yet to create a fully functional backup tool that is usable by elementary users.

Any other ideas out there?

---

### Post by john_markh on 2008-09-11
Well.. I have achived this using a simple Bash script (I will see if I still have it).

Basically, the idea is simple:
[LIST=1]
[*]Generate a list of files to backup (using ```
ls -RA
``` and external configuration file with list of directories you are interested in backing up).
[*]If previous backup exist, compare generated file list (as in 1) against the same file list (which was generated before). The result of this step is a diff file which contains only the files needed to be updated in the backup.
[*]Create an archive using the file list (from step 2) using ```
tar -cz --list $update_list
```.
[*]Update file list (with the one generated in step 2). It will be used with next iteration.
[*]Run ```
df
``` to check for disk space
[/LIST]
In addition, you can add your own reporting into the script.

And one last thing. Bash script is really EASY, even if you are not a developer. I found this reference manual an excellent source of information and examples: [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/").
Done! :KS

---

### Post by kokkus on 2008-09-11
I use remastersys to create an ISO of my installation, then I extract the iso file, add folders and pack it again in a compressed format. then I have a costum backup with boot live cd and installation options if I need it.

---

### Post by hyper_ch on 2008-09-11
there are functional backup tools that do elementary bacups... the problem is you have specific needs and

incremental & compression

usually does not work togethre. You need to decide what you want.

---

### Post by mwsherman on 2008-09-11
> **john_markh said:**
> 
Well.. I have achived this using a simple Bash script (I will see if I still have it).

...

And one last thing. Bash script is really EASY, even if you are not a developer. I found this reference manual an excellent source of information and examples: [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/").
Done! :KS

I would be interested in checking that script out. But I'm curious how you then would restore the backups, since you now have one big tar, and then other tars with the changed files. What if the files you want are spread across 30 tars? And how does the script handle killing old backups over time?

I know bash isn't hard. I've played with it a bit. And I have previous programming experience. However, I don't feel comfortable writing my first bash script to do something as sensitive as backup and restore. It maybe isn't difficult, but the damage of an error is immense. If I had a year of bash experience already, I'd probably just have written something myself.


> **kokkus said:**
> I use remastersys to create an ISO of my installation, then I extract the iso file, add folders and pack it again in a compressed format. then I have a costum backup with boot live cd and installation options if I need it.

Not only is this script heavy, but it sounds like you have to backup everything. Honestly, this seems way more roundabout than necessary, and doesn't do incremental, right?



> **hyper_ch said:**
> there are functional backup tools that do elementary bacups... the problem is you have specific needs and

incremental & compression

usually does not work togethre. You need to decide what you want.

Not that I'm a Windows fan, but there are dozens of Windows programs that do all of this stuff and lots of other things. 


I am willing to pay for a program if necessary, by the way.

So...any other ideas out there? Why isn't this higher priority among Ubuntu developers...seems that this is a little more vital than making Ubuntu prettier than MacOS :).

Thanks for your ideas everyone.

---

### Post by skullmunky on 2008-09-11
I can see why it would be challenging to have both incremental AND compression ... 

there are a couple kinds of "incremental" backup - when i think of incremental, i think of "only backing up new files and files that have changed", rather than coping everything over every time.

or it might be that you mean "backup only new and changed files, and also keep all the different versions of those files".

rsync does the first, but i don't think it automatically does the latter.


Have you tried some of the KDE apps?  I don't know any of these well, but you might look at some of the ones on kde-apps.org:

[http://www.kde-apps.org/?xcontentmode=272](http://www.kde-apps.org/?xcontentmode=272)

all will allow backup to an external drive.  most will also support network backup.

Keep: lets you select directories, does incremental, scheduling
KDailyMirror: GUI front-end for rsync with cron scheduling

KBackup: saves to compressed tarballs

RetrospeKt : saves incremental versioned backups with diff's, a la time machine.

there's a bunch more but those sounded the most promising ... 

if you find something that works well for you, please do share :)

---

### Post by hyper_ch on 2008-09-11
skullmunky: rsync cannot do the later, but you can hardlink it all and hence do the later yourself.

---

### Post by mwsherman on 2008-09-14
> **skullmunky said:**
> 
I can see why it would be challenging to have both incremental AND compression ...

there are a couple kinds of "incremental" backup - when i think of incremental, i think of "only backing up new files and files that have changed", rather than coping everything over every time.

or it might be that you mean "backup only new and changed files, and also keep all the different versions of those files".

rsync does the first, but i don't think it automatically does the latter.


For the sake of clarification, I'm talking about the second. 

Also, the reason I want incremental is because I've deleted files accidentally in the past, and then don't notice it for awhile. Tends to happen when I organize photos :).

> **skullmunky said:**
> 

Have you tried some of the KDE apps?  I don't know any of these well, but you might look at some of the ones on kde-apps.org:

[http://www.kde-apps.org/?xcontentmode=272](http://www.kde-apps.org/?xcontentmode=272)

all will allow backup to an external drive. most will also support network backup.

Keep: lets you select directories, does incremental, scheduling
KDailyMirror: GUI front-end for rsync with cron scheduling

KBackup: saves to compressed tarballs

RetrospeKt : saves incremental versioned backups with diff's, a la time machine.



I took a look at those. Kdar fulfills all of the requirements. However, it has been removed from the Ubuntu repositories. It wasn't updated for a few years and was no longer building according to my internet searching. But it was updated earlier this year, and now builds OK. However, I'm too much of a newb to figure out how to get it going if its not in the repositories. Not to mention terrified of learning something new with an application as sensitive as backup.

Internet searching on Keep reveals it has problems, specifically backing up to / when the target external hard drive is unavailable. Maybe this has been fixed by now, maybe not. It also seems to have some problems with the daemon becoming possessed and changing the backup frequency. Scary stuff.

KDailyMirror is not incremental. 

Retrospekt doesn't compress. However, it looked interesting enough I started investigating installing it. However, I cannot find it in the repositories and cannot find any instructions for getting it going in Ubuntu Hardy.

KBackup will not backup files over 4GB. I don't have any files over 4GB right now, but it does give me the heeby-jeebies a bit. Aside from that, it isn't incremental.


Anyone know where I can find some help installing kDar on Ubuntu Hardy?

Anyone have any other suggestions? At this point, I'm willing to deal without compression, but I want to make sure that the backup program lets me know when something goes wrong, and doesn't require me to open a log file everyday to see if things went wrong. It should "just work", and tell me when it doesn't. I think I'm making reasonable demands :).

Thanks everyone for your help. I'm glad to see I'm not the only person having this problem. If you want to pump this up in Ubuntu Brainstorm: [http://brainstorm.ubuntu.com/idea/1/](http://brainstorm.ubuntu.com/idea/1/). There were some ideas posted in the forum there, and I'm going to look into those. If I find anything interesting I'll share it here.

Note the Brainstorm idea number...

---

### Post by skullmunky on 2008-09-16
Ok, I'll put my compiler where my mouth is. Let's see what you have to do to install KDar.  Disclaimer: I should mention i don't know anything about this program and have never used it, and only saw it on the kde-apps site.  


Don't see it in the repositories, so we'll have to compile it from source.  

While that might seem scary, particularly for something critical, it actually should not be, and from one point of view, is actually MORE secure and reliable than installing a binary.  If you haven't done this before though take a quick read through the introductory tutorials.

1. download kdar from [http://kdar.sourceforge.net/](http://kdar.sourceforge.net/)
2. uncompress it.
3. read the README on the site, or in the source folder.  also note the slackware desc files in there, that's encouraging that it's written by someone who means business. :)

4. aha, it needs something called "dar" which does the real work in the background.  maybe that's in the repositories?  
5. aha!  yes, there are several things.  there's "dar", which is a command-line program to do disk archiving.  there's also "libdar64" and "libdar64-dev" which are what you need to compile other programs that use dar.  install all of those.
```

sudo apt-get install dar libdar64 libdar64-dev

```

6. in the kdar-2.1.0 directory,
```

./configure --enable-mode=64
make
sudo make install

```

you have to include the --enable-mode flag for it to configure correctly, otherwise it complains it can't find libdar even though you just installed it.  that's because apparently there are 2 versions of libdar - one that uses 32 bit integers, and one that uses 64 bit integers, so is faster.  the 64 bit version is the one we just installed, so you have to tell configure to use it.

At this point, KDar should be installed in the Utilities menu.

---

### Post by mwsherman on 2008-09-16
> **skullmunky said:**
>   that's because apparently there are 2 versions of libdar - one that uses 32 bit integers, and one that uses 64 bit integers, so is faster.  the 64 bit version is the one we just installed, so you have to tell configure to use it.
.

Thanks for posting that step-by-step. I'm going to try it later. 

But I have a quick question (and maybe a stupid question).

Will this run on 32 bit versions of Ubuntu? I have a 32 bit processor, and am most certainly running 32 bit Ubuntu.

I'm guessing I'll be fine. But better safe than FUBARed...

---

### Post by stinger30au on 2008-09-16
you can install wine and use a freeware program i use to do exactly this

[its called syncback freeware]("http://www.2brightsparks.com/freeware/freeware-hub.html")


or you can install wine and install willow creek backup. this is another windows program and oyu need to buy it but it will also allow you to span your data to dvd/cd with incremental backup as well
[URL="http://www.willowsoft.com/backup/index.html"]
magic little program from here[/URL]

---

### Post by mwsherman on 2008-09-16
> **stinger30au said:**
> you can install wine and use a freeware program i use to do exactly this


How's that working for you?

The idea of using Wine for backup scares the you-know-what out of me...am I being overly paranoid?

---

### Post by mwsherman on 2008-09-17
> **skullmunky said:**
> 
Ok, I'll put my compiler where my mouth is. Let's see what you have to do to install KDar. Disclaimer: I should mention i don't know anything about this program and have never used it, and only saw it on the kde-apps site.


It was bumpy but I managed to get Kdar running.

I had to pick up a lot of packages, including different versions of the libdar packages and about 100 dev packages. I probably should have kept a list. I kept getting errors, googling them, finding someone with the same problem on a different application build, and installing the packages. I actually got kdar working. Yay. I never appeared in any "Utilities" menu (I don't think Ubuntu has one by default...I certainly don't), but it ran from the command line.

Unfortunately, it has no features for scheduling backups. HAHAHAHAHAHA. I'm sure there's a way to get it working with cron and dar, but I'm done with this for now. Maybe I'll play with it some tomorrow.


Anyone have any other programs I should try?

Anyone have expertise in kdar/dar they'd like to share, specifically scheduling it?

---

### Post by anderswestrup on 2008-09-17
Hi,

If you still are interested in a command-line backup solution, I would recommend the script rsync-current, found on [https://secure.hoij.net/rsync-current/](https://secure.hoij.net/rsync-current/)

It is a script around rsync that does incremental backups using hard-links, and removes old backup versions according to retention times.

If you run it from cron it will generate a daily report mail of about 10 lines, and the subject will indicate if any errors where found. I prefer to get a mail even if the backups are running correctly - this way I'll notice if they suddenly stop running..

(rsync-current is actually two bash scripts, one called rsync-current, and one called run_backups that includes the configuration on what to back up)

/Anders

---

### Post by mwsherman on 2008-09-17
> **anderswestrup said:**
> Hi,

If you still are interested in a command-line backup solution, I would recommend the script rsync-current, found on [https://secure.hoij.net/rsync-current/](https://secure.hoij.net/rsync-current/)



That link isn't working...

---

### Post by hyper_ch on 2008-09-17
rsyncing with hardlinks is quite simple... use something like this

backup
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=*****************
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
/var/opt/
/var/run/
/var/spool/
/var/tmp/
/vmlinuz
/vmlinuz.old

```

And rsync could also be used to sync over a network from another computer ("from" is recommended, not "to").... modify the above script to this:
```

KEY=/root/rsync/server_key                   # Mirror key

# RUN RSYNC INTO CURRENT
$RSYNC                                                  \
        -apvz --delete --delete-excluded               \
        -e "$SSH -i $KEY"                                       \
        $FROM                                           \
        $CURRENT;

```

Keybased ssh logins: [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

### Post by mwsherman on 2008-09-25
I have a solution now.

In kDar, I discovered that I could create an output script that would run dar with all the parameters I was using in kDar.

Using these parameters I created some bash scripts. 

One bash script does full backups, and one does incremental backups.

Using gnome scheduler, the full one is running on the 1st and the 15th of the month, and the incremental one runs every day.

Both scripts create the archive, test the archive, and display a message on the screen with the exit codes of the archiving and the tests, as well as how much space is free on the backup drive and how much space recent backups are taking...this is so I can purge my backups, which I plan to do manually. I also know if a backup didn't fire (no daily message) or if it failed and why.

The daily script checks to see if it is the first or fifteenth, and if so displays a message that it will not run with an explanation why.

I'm quite happy with this solution...it has fulfilled all my criteria, and gives me enough information so that i always know if things are working. on the other hand, it's in cron so I better hope I have my compy up overnight on the 1st and the 15th...but even if i don't the daily backups will pick up the following day. the dailies are always based on the most recently created archive (either full or daily).

I'll be happy to share my bash scripts with anyone who wants. They aren't pretty but they can get the job done. 

Thanks to everyone for their help.

I'm marking this thread as solved, even though the underlying issue of Ubuntu lacking an "it just works" backup.

---

### Post by mdpalow on 2008-10-25
Not sure why you would think QuickStart doesn't allow you to backup your files to anywhere but the Desktop. Before actual backup, you're provided with a graphical window to select the location for your back-up.

---

### Post by mwsherman on 2008-12-08
Ok, here are the scripts.

/BACKUPPATH/BACKUPNAME is the path of where the backup should go and the name of it. I put the date on!


This one runs on the 1st and 15th of every month. It does a full backup:


I'm backing up my home, my /var, my /usr/loc, and my /etc



```

#!/bin/bash

# This script performs a full backup in dar of my selected directories, checks the exit code of dar, reports the result of the exit code, tests the archive, reports the result of the test, reports the freespace on the backup drive, and reports the size of the archive that was just created.

#full backup. this needs the dar docs to make sense.
dar -v -c "/BACKUPPATH/BACKUPNAME$(date +%Y%m%d)" -R "/" -D -y -m 150 -Z "*.avi" -Z "*.bz2" -Z "*.gif" -Z "*.gz" -Z "*.jpg" -Z "*.mov" -Z "*.mp3" -Z "*.mpg" -Z "*.pbm" -Z "*.pdf" -Z "*.png" -Z "*.pnm" -Z "*.Z" -Z "*.zip" -Z "*.AVI" -Z "*.BZ2" -Z "*.GIF" -Z "*.GZ" -Z "*.JPG" -Z "*.MOV" -Z "*.MP3" -Z "*.MPG" -Z "*.PBM" -Z "*.PDF" -Z "*.PNG" -Z "*.PNM" -Z "*.z" -Z "*.ZIP" -P "/BACKUPPATH" -g "etc" -g "home" -g "usr/local" -g "var"

exitCodeBackup=$?

#test the backup
dar -t "/BACKUPPATH/BACKUPNAME$(date +%Y%m%d)"
exitCodeTest=$?

xhost +LOCAL: #allows zenity to work

#checks for abnormal exit code
if test $exitCodeBackup -eq 0
then
zenity --info --text "Full Backup Created Successfully $(date +%Y%m%d)"
else
zenity --info --text "Full Backup Failed $(date +%Y%m%d), Exit Code $exitCodeBackup "
fi

#checks for abnormal exit code of the backup test
if test $exitCodeTest -eq 0
then
zenity --info --text "Full Backup Test Passed Successfully $(date +%Y%m%d)"
else
zenity --info --text "Full Backup Test Failed $(date +%Y%m%d), Exit Code $exitCodeTest "
fi

#display last 3 backups and free space
zenity --info --text " $(df /media/backup -h) $(ls /media/backup -lrtgoh |tail -3 |awk '{print $7 " " $3}') "

```


This runs everyday, but doesn't on the 1st and 15th. it creates a differential backup:



```

#!/bin/bash

# This script performs a differential dar backup of selectect directories based on the most recent dar backup (either full or differential), tests the archive, then reports the success/failure of the backups. then shwos free space and how much space the most recent backups consumed



currentDay=$(date +%d)


#we don't want to run a differential on the 1st or 15th, since that is when the full runs
if test $currentDay -eq 1
then
zenity --info --text "Differential Backup Not Performed, it is the $currentDay of the month "
elif test $currentDay -eq 15
then
zenity --info --text "Differential Backup Not Performed, it is the $currentDay of the month "
else

#whatever file in the backup directory was modified last is what we are basing this backup on. so it could either be a full backup or a differential

lastBackup=$(ls /media/backup/*.dar -1rtgo |tail -1 |awk '{print $7}' | sed 's/\(.*\)\..*/\1/' | sed 's/\(.*\)\..*/\1/')


dar -v -c "/media/backup/diff_backup$(date +%Y%m%d)_basedonprevious" -R "/" -A "$lastBackup" -D -y -m 150 -Z "*.avi" -Z "*.bz2" -Z "*.gif" -Z "*.gz" -Z "*.jpg" -Z "*.mov" -Z "*.mp3" -Z "*.mpg" -Z "*.pbm" -Z "*.pdf" -Z "*.png" -Z "*.pnm" -Z "*.Z" -Z "*.zip" -Z "*.AVI" -Z "*.BZ2" -Z "*.GIF" -Z "*.GZ" -Z "*.JPG" -Z "*.MOV" -Z "*.MP3" -Z "*.MPG" -Z "*.PBM" -Z "*.PDF" -Z "*.PNG" -Z "*.PNM" -Z "*.z" -Z "*.ZIP" "var/cache" -P "var/tmp"  -g "etc" -g "home" -g "usr/local" -g "var"

#same exit code stuff as seen in the other script
exitCodeBackup=$?

dar -t "/media/backup/diff_backup$(date +%Y%m%d)_basedonprevious"
exitCodeTest=$?



xhost +LOCAL: #allows zenity to work

#same as in other script
if test $exitCodeBackup -eq 0
then
zenity --info --text "Differential Backup Created Successfully $(date +%Y%m%d) based on $lastBackup"
else
zenity --info --text "Differential Backup Failed $(date +%Y%m%d), based on $lastBackup Exit Code $exitCodeBackup"
fi

if test $exitCodeTest -eq 0
then
zenity --info --text "Differential Backup Test Passed Successfully $(date +%Y%m%d)"
else
zenity --info --text "Differential Backup Test Failed $(date +%Y%m%d), Exit Code $exitCodeTest "
fi

#display last 3 backups and free space
zenity --info --text " $(df /media/backup -h) $(ls /media/backup -lrtgoh |tail -3  |awk '{print $7 " " $3}') "
fi 
```

if someone is actually using this, i can try to explain more. it's messy!

---

### Post by doggyworld on 2008-12-09
Thnx for the script.. I might actually use this as I've just started looking for a backup solution.  How hard was it to get kdar working?

---

