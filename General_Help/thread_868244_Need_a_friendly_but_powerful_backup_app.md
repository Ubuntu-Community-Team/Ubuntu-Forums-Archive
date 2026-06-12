---
title: "Need a friendly but powerful backup app"
date: 2008-07-23
forum: General Help
---

### Post by MountainX on 2008-07-23
I'm switching a file server from Windows to Ubuntu. I've been using SyncBack SE for backups and I would like something very similar for Ubuntu. (BTW, I installed gnome on my file server because I'm not an admin - just a home user.)

I heard about Flyback, but I didn't try it yet. Is that the best GUI backup app for Ubuntu? 

I want something that supports versioning of files and that stores the backed up files in their original (uncompressed) condition. I also want to be able to select which files are backed up via the GUI.

SyncBack SE has a nice feature that lets you choose whether all new files in a location of included in the backup or excluded. I'd like this functionality in a Ubuntu app too.

Thanks for any suggestions or pointers to other threads.

---

### Post by Amarsingh0793 on 2008-07-23
Try Abakt.

---

### Post by MountainX on 2008-07-23
> **Amarsingh0793 said:**
> Try Abakt.


[http://www.xs4all.nl/~edienske/abakt/](http://www.xs4all.nl/~edienske/abakt/)

Thanks but, it says the project is discontinued. 

EDIT: I see Abuktu is the successor. [http://www.xs4all.nl/~edienske/abaktu/](http://www.xs4all.nl/~edienske/abaktu/)

Any other suggestions anyone? Thanks.

---

### Post by raptor2552 on 2008-07-23
Hello

You might want to try out pybackpack which uses rdiff-backup to do incremental backups of files in there native state (uncompressed).

---

### Post by MountainX on 2008-07-23
> **raptor2552 said:**
> Hello

You might want to try out pybackpack which uses rdiff-backup to do incremental backups of files in there native state (uncompressed).

It looks interesting. Thanks.

---

### Post by mdsharp24 on 2008-07-24
cd /

create a file called exclude, and in this file put

tmp
proc
mnt
lost+found
sys
usr/backup

cd /usr && mkdir backup

cd /

rsync --delete-after -avz --exclude-from=exclude / /usr/backup/

your entire root filesystem EXCLUDING whats in the file exclude will be copied to /usr/backup/

The NEXT time you run this command, ONLY the changed files from / will be copied over, so the process takes a FRACTION of the time. Also, changes in the / filesystem will be deleted in /usr/backup (thats what --delete-after) does. In short, /usr/backup is a mirror of /

I would run this is rescue mode/root shell to minimize changes in the filesystem during the rysnc

then, cd /usr && tar cvpf backup.tar backup/ && gzip -9 backup.tar

Then move the backup.tar.gz to a safe place. Leave /usr/backup so you can run the command above to get only the changes to the system. Then tar and gzip once a week, delete old files, replace the new backup.tar.gz

Also, if you run rsync with the -n flag included it will MIMICK what it is going to do without doing it.

Then, you can play with your system, and run the above rsync command with -n to see what changes were made to the system BEFORE you started playing and reverse engineer everything.

Also, if you ever have to re-install after something horrible, re-install Ubuntu, grab the backup.tar.gz, place it in /usr and untar it. Then in /usr/backup run:

rsync --delete-after -avz --exclude-from=exclude /usr/backup/ /

and the system will be put back in place.

---

### Post by TVC15 on 2009-03-21
Hi there,

Backup utilities seem to be a hot item on the forum.  A lot of people want something that looks and feels similar to the popular Windows tool Syncback.

I have tried and tested a lot of the tools mentioned.  But now, I feel that for Linux, the best backup tool for me (and surely many others) is rsync.
Best of all: rsync now has a GUI called grsync that you can find in the Ubuntu repositories.
Looks and feels a lot like Syncback and also works on Samba shares or mounted network drives or over an ssh, ....

Very much worth giving a try!


Good luck!

---

### Post by rhcm123 on 2009-03-21
> **mdsharp24 said:**
> 
rsync --delete-after -avz --exclude-from=exclude / /usr/backup/

your entire root filesystem EXCLUDING whats in the file exclude will be copied to /usr/backup/

The NEXT time you run this command, ONLY the changed files from / will be copied over, so the process takes a FRACTION of the time. Also, changes in the / filesystem will be deleted in /usr/backup (thats what --delete-after) does. In short, /usr/backup is a mirror of /


i love you
seriosly, i've been running "cp -r / /media/backup" for far to long now

---

### Post by MountainX on 2009-03-21
I just found the perfect backup application: [storeBackup]("http://savannah.nongnu.org/projects/storebackup")

(see documentation here: [http://www.nongnu.org/storebackup/](http://www.nongnu.org/storebackup/))

Previously, I made a [list]("http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware") of all the backup apps I could find:
[http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware](http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware)

After a lot of research, I picked storeBackup a few days ago and I have been making large backups with it already. I have backed up over 1 TB of data. 

storeBackup is awesome!

In my opinion, these are some of its best features:
* restore easily--even without storeBackup! The most important aspect of a backup tool is easy restoring.
* native storage format
* [COLOR=Blue]**recognizes when files have been copied, moved or renamed**[/COLOR] and 
  does not waste time or space to duplicate the backup of such files
* copied, renamed or moved files with identical contents
  are hardlinked (so **each backup set is complete** / full)
* copies / compresses files to another disk and generates
  backups with time stamps
* splits big image files (from eg.\ TrueCrypt, mbox, Xen, KVM,
  VMware, etc.) or complete devices into small pieces and saves only
  differences to existing backups, thereby saving space and time
* sophisticated including / excluding possibilities for files and
  directories
* fast even over slow or high latency network connections

---

### Post by rhcm123 on 2009-03-21
> **MountainX said:**
> I just found the perfect backup application: [storeBackup]("http://savannah.nongnu.org/projects/storebackup")


no offence man, but you sound like an advertisment

---

### Post by rudihawk on 2009-03-21
Maybe you would like to check out grsync?

---

### Post by MountainX on 2009-03-21
> **rhcm123 said:**
> no offence man, but you sound like an advertisment

Look at the date of my original post. I started this thread more than 8 months ago! 

If you had been looking for a good backup solution for 8 months and finally found one, maybe you would sound excited too! :)

---

### Post by rhcm123 on 2009-03-21
> **MountainX said:**
> Look at the date of my original post. I started this thread more than 8 months ago! 

If you had been looking for a good backup solution for 8 months and finally found one, maybe you would sound excited too! :)

oh... wow, this thread has been abandoned for that long?

---

### Post by MountainX on 2009-03-21
> **rhcm123 said:**
> oh... wow, this thread has been abandoned for that long?

Well, not really... I've been researching backup apps almost since I started using Ubuntu about 15 months ago. In my mind, I never abandoned this thread because I was still looking for an answer -- and I was having a hard time finding what I needed. 

It just so happens that I found a really good backup solution recently and today I saw that someone made a new reply to this thread :)

BTW, I do use rsync for a lot of stuff almost every day (and I have looked at grsync too). But [storeBackup]("http://savannah.nongnu.org/projects/storebackup") has some awesome features that all these other backup tools lack. In my post above, I included the feature list because this combination of features is so unique that it deserves special attention.

For example, I often reorganize my photos (and music and videos and documents...). After I dump new pictures from my camera to my computer, I then rename them and sort them (into folders, etc.) out over the next few days or weeks. With all my other backup software (including when I was using Windows), my daily backups would duplicate these photos when they were renamed and moved. That wasted a lot of backup space and increased the time required to do a backup. 

My first backup with storeBackup identified about 65 GB (gigabytes!) of duplicated files on my hard drive. This was stuff like the same picture with more than one name or the same file in more than 1 folder. Other backup software would have just copied that extra 65 GB to the backup, and that sucks.

It was very hard to find a good backup application that would solve this problem while also meeting my requirement that I could restore files with no special tools. [Storebackup]("http://savannah.nongnu.org/projects/storebackup") is in a class by itself, in my opinion. This tool alone would make me move my file server to Linux if I wasn't already on Linux. That's what some people call a "killer app". 

This type of backup is something that is almost impossible to do on Windows in a supported way, so clearly the Ubuntu community should let people know about the existence of storeBackup because it is one of those apps that will make people appreciate the power of Ubuntu and Linux. 

I struggled to find a good personal finance application (and a few other Windows apps I miss) and over the past 15 months, from time to time, I often thought that life was easier on Windows. StoreBackup is one of the Linux open source tools that has no equal -- and because of it, there is no way I could go back to running Windows on my file server now. No way.

---

### Post by rhcm123 on 2009-04-04
> **mdsharp24 said:**
> 
rsync --delete-after -avz --exclude-from=exclude / /usr/backup/


can you use an "include" option? I want to backup /share, /media/floppy, /home, and /etc to /media/backup. Can i do this? Will it automatically re-update or will i need to make this a cron job?

---

### Post by MountainX on 2009-04-04
> **rhcm123 said:**
> can you use an "include" option? I want to backup /share, /media/floppy, /home, and /etc to /media/backup. Can i do this? Will it automatically re-update or will i need to make this a cron job?

For backing up, I like the "P" option as shown below.

rsync [options] /source /destination

rsync -avP /home /media/backup
rsync -avP /share /media/backup
rsync -avP /media/floppy /media/backup
rsync -avP /etc /media/backup

**Before using it, do a "dry run" with "n" option!** For example:
rsync -avP[COLOR=Red]n[/COLOR] /home /media/backup

use with cron for regular backups

---

### Post by rhcm123 on 2009-04-04
> **MountainX said:**
> For backing up, I like the "P" option as shown below.

rsync [options] /source /destination

rsync -avP /home /media/backup
rsync -avP /share /media/backup
rsync -avP /media/floppy /media/backup
rsync -avP /etc /media/backup

**Before using it, do a "dry run" with "n" option!** For example:
rsync -avP[COLOR=Red]n[/COLOR] /home /media/backup

i was just wondering if i could make a file, like, instead of "exclude" (see the post i quoted) having "include", so i can be lazy and not have to do lots of typing :D

---

### Post by petersm2 on 2009-04-04
I too am looking for backup software.

I want something that will run automatically when my external drive is plugged in, or at least with just a click of the notificaion bar, and without compression.

I would use Rsync but I have very limited ability with a command line.

I have tried Grsync but How do I get it to run automatically?, or with one click. I don't want to have to open the app manually and click through the different sessions.

The Conduit Project worked awesome for me except that it won't copy a large amount of files from a folder, it only goes to 15% or so complete.

PyBackPack works good but again, how do I get it to run automatically, and I don't really like how it puts everything in certain file heirarchy (although I could live with it if it was automized).

Could someone please enlightened me? It doesn't seem like it should be this hard to find an app that simply copies files and folders to an external hard drive automatically and without compression.

---

### Post by skillllllz on 2009-04-04
Just wanted to mention FlyBack. It's not for everyone, but I like using it.

[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by MountainX on 2009-04-04
> **rhcm123 said:**
> i was just wondering if i could make a file, like, instead of "exclude" (see the post i quoted) having "include", so i can be lazy and not have to do lots of typing :D

use a text editor and paste this into a file. name it mybackup.sh
```
#!/bin/bash
# backup script
echo "starting..."
rsync -avvP /home /media/backup
rsync -avvP /share /media/backup
rsync -avvP /media/floppy /media/backup
rsync -avvP /etc /media/backup
echo "done"
exit 0
```

make it executable
```
chmod +x mybackup.sh
```

run it
```
./mybackup.sh
```

of course, do the dry run first as I said before

---

### Post by michaelzap on 2009-04-04
I've been using Grsync for years, but storeBackup does indeed look pretty sweet...

---

### Post by MountainX on 2009-04-04
> **michaelzap said:**
> I've been using Grsync for years, but storeBackup does indeed look pretty sweet...

storeBackup is super cool! It is my favorite backup app. But I also use rsync at times too.

---

### Post by rhcm123 on 2009-04-05
> **MountainX said:**
> use a text editor and paste this into a file. name it mybackup.sh
```
#!/bin/bash
# backup script
echo "starting..."
rsync -avvP /home /media/backup
rsync -avvP /share /media/backup
rsync -avvP /media/floppy /media/backup
rsync -avvP /etc /media/backup
echo "done"
exit 0
```

make it executable
```
chmod +x mybackup.sh
```

run it
```
./mybackup.sh
```

of course, do the dry run first as I said before

thank you very much. I made a symbolic link from /bin/backup to /root/backup.sh, thanks!!!!!

---

### Post by callie510 on 2009-04-05
Well I am very glad this thread was resurrected ... I have had some computer emergencies lately (I joined this forum to search for help) and now I was looking for a good, simple way to keep my stuff backed up. Guess I didn't even need to make a new thread :)

I like the rsync command line option best. Thanks so much mdsharp24, I am about to do exactly what you suggested & thanks also for including how to restore from the backup to a blank system :) I am a relatively new ubuntu user and this was so helpful!!

edit: As for compression- the vast majority of my space is taken up by photos, music, and videos, which don't compress well anyways. Why should I compress when I back up? Space isn't an issue since I back up to a huge external drive. Will I be able to navigate through my backups in nautilus if I use the -z option to compress when backing up, or will my backup be like one big gzipped file? (I am pretty new to this stuff, sorry)

---

### Post by MountainX on 2009-04-05
> **callie510 said:**
> 

edit: As for compression- the vast majority of my space is taken up by photos, music, and videos, which don't compress well anyways. Why should I compress when I back up? Space isn't an issue since I back up to a huge external drive. Will I be able to navigate through my backups in nautilus if I use the -z option to compress when backing up, or will my backup be like one big gzipped file? (I am pretty new to this stuff, sorry)

I agree with your thinking. I do not compress any of my photos, music or mpg videos. I also like being able to restore individual files, so I do not put my backups into one big archive. I like my backup to look exactly like a regular file system so I can easily get one or more (or all) files out of my backup with no special tools.

I am able to achieve this with storeBackup and, of course, with rsync too.

---

### Post by MountainX on 2009-05-02
The beta version of storeBackup 3.1 is available for testing now.

For me, the biggest improvement is a huge increase in speed!

---

### Post by MountainX on 2009-05-10
3.1 rc1 is now published.

Get it at [http://storeBackup.org](http://storeBackup.org)

---

### Post by cmost on 2009-05-10
By far, my favorite is grsync (in the repositories.)  It's a very easy, graphical frontend to rsync.  It makes creating various backup profiles easy!  You can also use its command line facility to automate backups on logon / logoff, etc.  Check it out.

---

### Post by richard.scott on 2009-06-15
Have you tried Duplicity:

[http://duplicity.nongnu.org/](http://duplicity.nongnu.org/)

---

### Post by Cheesemill on 2009-06-15
Take a look at Back in Time
[http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by knomaly on 2009-06-15
How well do these backup progs handle filename changes? What about spaces in the filenames? 

For example, regarding how rsync handles both filename changes and spaces in the filenames, see [http://www.samba.org/rsync/FAQ.html](http://www.samba.org/rsync/FAQ.html) : 

For filename changes, click on FAQ link in first column titled "rsync recopies the same files". The fourth paragraph reads as follows[B]: 
[/B]Something else that can trip up rsync is a filesystem changeing the filename behind the scenes.  This can happen when a filesystem changes an all-uppercase name into lowercase, or when it decomposes UTF-8 behind your back.

For spaces in the filenames, click on FAQ link in second column titled "spaces in filenames".

---

### Post by jigs.parekh4u on 2009-06-15
hiii

---

### Post by knomaly on 2009-06-15
[SIZE=2]Search: Google: best linux backup solution
Results: [http://www.google.com/cse?cx=013269018370076798483:gg7jrrhpsy4&cof=FORID:1&q=best+linux+backup+solution&sa=Search](http://www.google.com/cse?cx=013269018370076798483:gg7jrrhpsy4&cof=FORID:1&q=best+linux+backup+solution&sa=Search)

Search: Google: best linux backup solution for beginners
Results: [http://www.google.com/cse?cx=013269018370076798483:gg7jrrhpsy4&cof=FORID:1&q=best+linux+backup+solution+for+beginners&sa=Search](http://www.google.com/cse?cx=013269018370076798483:gg7jrrhpsy4&cof=FORID:1&q=best+linux+backup+solution+for+beginners&sa=Search)

*

[/SIZE][SIZE=2][SIZE=2]Some interesting articles & web sites:

Cooking with Linux - Backing Up to the Clouds
[http://www.linuxjournal.com/article/10409](http://www.linuxjournal.com/article/10409)

The rsync family (IBM)
[http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/](http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/)

Ubuntu Backup Software[URL="http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/"]
[/URL][http://www.tuxguides.com/2009/04/30/ubuntu-backup-software/](http://www.tuxguides.com/2009/04/30/ubuntu-backup-software/)

7 Best Free/Open-source Backup Software for Linux
[http://www.junauza.com/2009/01/7-best-freeopen-source-backup-software.html]("http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/")

10 Things to do After Installing Ubuntu Linux 
[http://ubuntulinuxhelp.com/10-things-to-do-after-installing-ubuntu-linux/](http://ubuntulinuxhelp.com/10-things-to-do-after-installing-ubuntu-linux/)

Back In Time - easy, schedulable backup utility
[http://vadi-blog.com/2009/04/11/back-in-time-easy-schedulable-backup-utility/](http://vadi-blog.com/2009/04/11/back-in-time-easy-schedulable-backup-utility/)

BackupPC
[http://backuppc.sourceforge.net/]("http://backuppc.sourceforge.net/%5C")[/SIZE][/SIZE]

---

### Post by MountainX on 2009-06-17
> **knomaly said:**
> How well do these backup progs handle filename changes? 
For me, this was the key question! (Filename changes include moves or renames, obviously.)

There are only 3 open source apps that will handle filename changes properly. They are:

1. storeBackup
2. BackupPC
3. Link-Backup

(see [http://davestechshop.net/blog/dave/list-of-free-open-source-linux-and-ubuntu-backup-software](http://davestechshop.net/blog/dave/list-of-free-open-source-linux-and-ubuntu-backup-software))

Of these, I liked storeBackup because it is mature and powerful, but also simple and lightweight. BackupPC looks good too, but it was overwhelmingly complex for me.

EDIT: storeBackup 3.1 is released: [http://storebackup.org/](http://storebackup.org/)

---

### Post by VMC on 2009-06-17
> **MountainX said:**
> ...
(see [http://davestechshop.net/blog/dave/list-of-free-open-source-linux-and-ubuntu-backup-software](http://davestechshop.net/blog/dave/list-of-free-open-source-linux-and-ubuntu-backup-software))
...
Thanks for the link to your site. The first page on this topic has broken links.

On your link you left out one backup program [[COLOR="Lime"]**FSArchiver**[/COLOR]]("http://www.fsarchiver.org/Main_Page").

---

### Post by MountainX on 2009-06-17
> **VMC said:**
> Thanks for the link to your site. The first page on this topic has broken links.

On your link you left out one backup program [[COLOR=Lime]**FSArchiver**[/COLOR]]("http://www.fsarchiver.org/Main_Page").

I added FSArchiver, but I didn't find the broken links.

---

### Post by asphixmx on 2009-06-17
Have you heard UNISON? ([http://www.cis.upenn.edu/~bcpierce/unison/download.html](http://www.cis.upenn.edu/~bcpierce/unison/download.html)) It is wonderful. I have a laptop and a desktop computer. With unison, I sync both computers. Changes are mantained, the hard disks are like mirrors, exactly the same. No matter if I change a file in the Desktop, create (or delete) a folder in the laptop.. when I sync with unison, it makes the proper changes in both computers. It is very useful if you have a laptop & desktop, because you can work on both and your files are always updated on both... forget about the "mmm...where the heck is that file I downloaded? in the laptop? or in the desktop?mmm...". It works on Linux, Windows & MacOS, syncing between different OS. Besides, since I have all my info in two different hard disks, it is also a backup ;)

---

### Post by MountainX on 2009-06-17
> **asphixmx said:**
> Besides, since I have all my info in two different hard disks, it is also a backup ;)

You may want to rethink that. If you, or some errant software on your computer, mistakenly corrupts a file on one hard disk, the corrupted file could get sync'd with your other drive. Then you will need a real backup to restore a non-corrupted version of the file.

People sometimes also mistakenly think RAID provides backup. 

(FYI, Unison doesn't handle file renames or moves.)

---

### Post by VMC on 2009-06-18
> **MountainX said:**
> I added FSArchiver, but I didn't find the broken links.

Post#9, third link. It starts with "Previously, I made a list of all the backup apps I could find:" [http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware](http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware)

---

### Post by asphixmx on 2009-06-20
> **MountainX said:**
> You may want to rethink that. If you, or some errant software on your computer, mistakenly corrupts a file on one hard disk, the corrupted file could get sync'd with your other drive. Then you will need a real backup to restore a non-corrupted version of the file.

People sometimes also mistakenly think RAID provides backup. 

(FYI, Unison doesn't handle file renames or moves.)

The same thing could happen with a backup program. If I notice there is a corrupted file in my computer... then it was also backed up :P Unless I have more than one version of the backup. It is not handy because I backup near 500GB.
Yes, you are right, Unison doesn't handle file renames or moves, but it detects the changes and copy the whole files in the new directory (I know, it is time-consuming); but at the end, the two hard disk are the same.
Cheers.

---

### Post by MountainX on 2009-06-20
> **asphixmx said:**
> The same thing could happen with a backup program. If I notice there is a corrupted file in my computer... then it was also backed up :P Unless I have more than one version of the backup. It is not handy because I backup near 500GB.
Yes, you are right, Unison doesn't handle file renames or moves, but it detects the changes and copy the whole files in the new directory (I know, it is time-consuming); but at the end, the two hard disk are the same.
Cheers.

Well, I think your point about the space requirements for multiple full backups and your point the time-consuming nature of copying files again that already exist in the backup (under a different name or path) get right to the central point of this thread! I started off with the same concerns and it took me 8 months of searching to find a solution I liked.

In my opinion, a good backup solution should solve the issues you mentioned. It should allow you to keep multiple backup versions in minimal space. And it should not waste the time and space to copy (again and again) files that have already been backed up and that have not changed (even if the file is moved).

Using storeBackup I currently have multiple versions of my backup going back to the first backup. And the whole series of backups takes up little more space than a single backup. If your situation is typical, you could probably keep multiple versions of a 500GB backup in a total of not much more than 500GB -- and less if you want to use compression. (The space efficiency of storeBackup is amazing thanks to smart use of hard links and "pooling". It is quite possible to have TWO full backups, *each* 500GB, stored in a total of, say, 500.5 GB *without compression*.)

The ability to do backups with space efficient versioning directly solves the problem of what happens if a file becomes corrupted and you don't find out about it until several backups have been performed. 

I started this thread by saying "I want something that supports versioning of files." I came to realize the importance of versioned backups after learning -- via a very painful and costly lesson -- that even the best hardware RAID suffers from the problem of replicating mistakes (corrupted files, accidental deletes, etc.) into the mirror. So I was just trying to share my experience to help others avoid the pitfalls that got me when I didn't take the time to understand how I should do a backup. Your statement that "it is also a backup" reminded me of the painful lesson I learned when I thought RAID was also a backup.

---

### Post by asphixmx on 2009-06-21
> **MountainX said:**
> And the whole series of backups takes up little more space than a single backup. If your situation is typical, you could probably keep multiple versions of a 500GB backup in a total of not much more than 500GB .....

Wow, I didn't thought about that, I thought different versions of a 500GB backup was = (500GB x #OfVersions). Thanks for the reply, I will give a try to the storeBackup program.
Greetings.

---

### Post by knomaly on 2009-06-22
> Have you heard UNISON?See page 3 of the IBM paper by Federico Kereki titled "The rsync family" (2009-04-14). Examine the section titled "Unison: rsync alternative". Mr. Kereki provides a nice, albeit brief, perspective on the utility of this program. . .

---

### Post by asphixmx on 2009-06-23
I red the article. He conludes: 
"You might do well by studying Unison, and considering it as a valid alternative to rsync. Features and concepts are similar enough, so you can feel at home with any of them. Though it might be said that rsync is more prevalent --and easier to use across different machines-- for a simple setup of your own, Unison can be simple to install, configure, and use in a frequent basis, so give it a go."
By the way, the article describes some programs like RSYNC, including it. Interesting article for the one who wants to sync or backup. The link is : [http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/](http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/)

---

### Post by samosamo on 2009-08-29
I'm bumping this thread.  I'm not happy with any of these solutions.  BackupPC, which I currently use, comes closest but still isn't perfect.  I feel there is something better.

---

### Post by MountainX on 2009-08-29
> **samosamo said:**
> I'm bumping this thread.  I'm not happy with any of these solutions.  BackupPC, which I currently use, comes closest but still isn't perfect.  I feel there is something better.

Better in what way? What's wrong with storeBackup? I like it better than BackupPC.

---

### Post by samosamo on 2009-08-31
> **MountainX said:**
> Better in what way? What's wrong with storeBackup? I like it better than BackupPC.

I can tell you love it and it's great and all but it's not an entire solution.  It has nothing built in for remote/secure transfers.  It needs scripting.  It has no conf files.  It has no web GUI.  I'll admit, You don't really need a GUI if you share out the backup store. That's pretty cool.

There is rsync, rdiff-backup, storeBackup, etc etc etc.  Then there is the full solutions like AMANDA, BackupPC, Bacula, etc

---

### Post by MountainX on 2009-08-31
> **samosamo said:**
>  It has nothing built in for remote/secure transfers.  It needs scripting.  It has no conf files.

 It has no web GUI.  I'll admit, You don't really need a GUI if you share out the backup store. That's pretty cool.


storeBackup does have powerful config files that make using it very easy. Why did you think it doesn't have this? (It also supports scripting in several ways, although those are all optional.)

In regard to security, storeBackup does support secure remote transfers in the best way -- by using the security mechanisms built into Linux remote file systems. 

I would like to see a little better support for using some of the Linux file systems, but I have been doing secure remote transfers (pulling down backups from my website) on a daily basis for a while now, and it works fine. It just took me a little trial and error to initially get it set up in the non-standard way I wanted it set up.

---

### Post by samosamo on 2009-08-31
You're right it does support config files.  I must have missed that.  

I'm very impressed by it after reading the examples ([http://www.nongnu.org/storebackup/node43.html](http://www.nongnu.org/storebackup/node43.html)).  I'm glad it works for you.  Really I am.  It just isn't the end-all-be-all solution that I wish we had.

---

### Post by MountainX on 2009-08-31
> **samosamo said:**
> You're right it does support config files.  I must have missed that.  

I'm very impressed by it after reading the examples ([http://www.nongnu.org/storebackup/node43.html](http://www.nongnu.org/storebackup/node43.html)).  I'm glad it works for you.  Really I am.  It just isn't the end-all-be-all solution that I wish we had.

Why don't you get in touch with Heinz-Josef Claes, the author of storeBackup? He is always interested in feedback that would improve the application. He has made several changes based on my feedback. I believe, with greater community involvement, storeBackup could grow into the end-all-be-all solution that you and I both wish we had. There is no such solution now. I believe storeBackup is the closest thing there is. And, it is our unbelievable good luck that the author of the application is actively engaged in improving it! So let's help him make it better.

UPDATE: I just wrote an email to Heinz and he told me about an exciting new feature he is working on. He is amazingly motivated to keep improving storeBackup! I would really encourage everyone to explore, here on the forum, and in communication with Heinz, how we can make storeBackup the perfect tool for the average home (or even business) Ubuntu user.

UPDATE 2: There is at least a nice beginning of a GUI for storeBackup:

Have a look at mabumbi:

[http://www.schwann.at/mabumbi/](http://www.schwann.at/mabumbi/)

It's very early in development - I haven't tried it.

---

### Post by grappler on 2009-08-31
I'd like to add my vote for  storebackup. One feature that I believe has not been mentioned here but which I find very useful is the following. 

I have two synced laptops - using unison (which I see as a syncing program rather than a backup solution) - and I'd like to back them both up to the same (remote - note) hard disk. storebackup does this in such a way that the same file from the two laptops is not duplicated. In this way it significantly reduces the space requirement on the remote hard drive.

---

### Post by samosamo on 2009-08-31
i appreciate the simplicity of how it operates.  but this is also why i can't use it.  i can use it for only SOME things. not everything.

BackupPC uses rsync, and rsync uses ssh. This allows me to securely transfer data over the internet without a VPN and since most modern UNIXs include rsync I don't have to install anything on machine being backed up.

If I migrate to storeBackup I would have to install sshfs+autofs on every machine.  Or, I could configure a VPN for securing the connection and install nfs+autofs on every machine.

See my problem?

---

### Post by rmeske on 2009-09-02
I came across this thread looking for a way of backing up a Windows server to an ubuntu server securely over the internet.  The advice so far is to use rsync over ssh.  With all the backup solutions mentioned here, is this really the best choice?

Currently I have a Windows application that does the backup over ftp but it takes a while to check all the files for changes.  It has been reliable over an unreliable connection but it can not handle files larger than 200MB and it is not secure.

Any other suggestions?

---

### Post by cheway on 2009-09-02
Is there a decent "storeBackup for dummies" guide anywhere? I've installed it, blindly typed "storeBackup" into terminal, and thought it looked a bit overwhelming! However, I really want to give it a go as there are a lot of good things being said about it.

Is it possible to run specific backup scenarios on startup?

---

### Post by HermanAB on 2009-09-02
Rsync over SSH is best even for MS Windows.  Rsync only transfers blocks of data that changed.  FTP always transfers complete files.

---

### Post by MountainX on 2009-09-05
> **cheway said:**
> Is there a decent "storeBackup for dummies" guide anywhere? I've installed it, blindly typed "storeBackup" into terminal, and thought it looked a bit overwhelming! However, I really want to give it a go as there are a lot of good things being said about it.

Is it possible to run specific backup scenarios on startup?

You will need to read the documentation that comes with storeBackup. The docs include a getting started section which is like a "storeBackup for dummies" guide.

I know we generally don't like to read the docs, but in this case (and for any app that doesn't have a GUI) you do have to read the docs. You'll be glad you did.

---

### Post by MountainX on 2009-09-05
> **HermanAB said:**
> Rsync only transfers blocks of data that changed.

Unless you move the file...
or unless you rename the file...
or unless you rename the directory...
or unless you rename a parent directory...
etc.

And those issues are why I use storeBackup.

---

### Post by rmeske on 2009-09-09
> **MountainX said:**
> Unless you move the file...
or unless you rename the file...
or unless you rename the directory...
or unless you rename a parent directory...
etc.

And those issues are why I use storeBackup.

I have read through the storeBackup documentation and it does look like an excellent backup solution.  In my case I want not only backup but replication for fail-over purposes.  It looks like storeBackup can handle this.

My problem is that the main server is a Windows 2003 server which is housing all the files to be backed up and the Ubunto server is housed off-site at my home.  This obviously limits my choices.

It appears that in my case the best (only?) choice is to use either rsync or Rdiff-backup.  True?

---

### Post by MountainX on 2009-09-09
> **rmeske said:**
> I have read through the storeBackup documentation and it does look like an excellent backup solution.  In my case I want not only backup but replication for fail-over purposes.  It looks like storeBackup can handle this.

My problem is that the main server is a Windows 2003 server which is housing all the files to be backed up and the Ubunto server is housed off-site at my home.  This obviously limits my choices.

It appears that in my case the best (only?) choice is to use either rsync or Rdiff-backup.  True?

I can't say what the best choice is when your data is on a Windows server. When I was backing up a Windows server, before I switch it over to Ubuntu, I used SyncBack SE on the Windows server (the destination was a Ubuntu server). SyncBack SE is good and inexpensive.

At one point I also used the Unix services for Windows (or whatever it is called). It was OK, but not great. But it did allow me to access the Windows server via NFS when I wanted.

Other options (maybe not the best) include Cygwin.

But again, I really can't say what would be best for you with your data on a Windows server. I'm just throwing out some ideas.

---

### Post by madman100 on 2009-09-09
Hi you might want to give luckybackup a try very easy to use and quite fast 


Madman100

---

### Post by rmeske on 2009-09-09
> **MountainX said:**
> I can't say what the best choice is when your data is on a Windows server. When I was backing up a Windows server, before I switch it over to Ubuntu, I used SyncBack SE on the Windows server (the destination was a Ubuntu server). SyncBack SE is good and inexpensive.

At one point I also used the Unix services for Windows (or whatever it is called). It was OK, but not great. But it did allow me to access the Windows server via NFS when I wanted.

Other options (maybe not the best) include Cygwin.

But again, I really can't say what would be best for you with your data on a Windows server. I'm just throwing out some ideas.

I appreciate your suggestions and will look into them.  Thanks!

---

### Post by kung fu buntu on 2009-09-14
I've read this thread (and some others) and it seems I can't find what I'm looking for.

I want to be able to do an **incremental backup to dvds**.

Suppose I have my "audio" directory, with several dozens of gigabytes.
I would like to be able to either do a complete backup OR do an incremental/differential backup since the last one.
Is there a tool that allows this?

But besides that, I would like to be able to run a script before files are written to DVD.
The script would basically run par2 and add forward error redundancy.
dar and baras do this, but they use they own image format, which is bad IMO. I would like a system where files are encoded natively.

---

### Post by urlwolf on 2009-11-26
MountainX, thanks for sharihg your efforts. Very detailed work. I'm reading the pdf for storeBackup... and it makes me think... Isn't this exactly what distributed vcs do? i.e. git.

It seems that flyback is now using git. Btw, the dev is active adain, see thi commit logs.

I'm not saying one is superior to the other... just started testing.

Can you ellaborate on how storebackup is different from say git backups? 

thanks!

---

### Post by rubinstein on 2009-12-03
Wow, thanks for mentioning storeBackup! It is really the everyday program I was looking for to back up my data to an external hard drive.

Before, I was using rsync - with all the problems it can bring with it (I also like to clean/reorder my folder structure every few months).

The last few days I was evaluating Déjà Dup ([https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)) which is nice on the surface, but I had a lot of problems with it. I think I have too much data (~ 500 GB), and Déjà Dup still has a lot of bugs. But for newbies it will be a nice and easy solution.

I have two backups (I know, I'm paranoid) - one at the same location as my computer, and one off-site.

For the external hard drive next to my computer I will use storeBackup.

I think I still have to use dar ([http://dar.linux.free.fr/](http://dar.linux.free.fr/)) for incremental off-site backups, though. I have a hard disk with a full backup at another location, and I make incremental backups every other week, which I burn on DVD and then also get the DVDs to this other distant location.

Maybe someone has even better suggestions for my use case?

Thanks again for pointing me to storeBackup!

---

