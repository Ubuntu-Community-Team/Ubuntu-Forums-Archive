---
title: "The most recommended opensource disk backup software software for Linux."
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by zfranciscus on 2009-10-26
Hi,

I found 2 good open source back up software for Linux. I would like to know whether anyone has used them before and how was your experience with them. 

[FSArchiver]("http://www.fsarchiver.org/Main_Page")
[Partimage]("http://www.partimage.org/Main_Page")

Is there other back up software for Linux that is better than the above 2 ?

Cheers ;)

---

### Post by macaholic on 2009-10-26
You would look into SBackup, I can't really find a good page for it other than the sourceforge page: [http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)
I personally haven't used either of the programs you mentioned, I've used SBackup and command line/scripting solutions mainly.

---

### Post by Mark Phelps on 2009-10-27
> **zfranciscus said:**
> Is there other back up software for Linux that is better than the above 2 ? Cheers ;)

Don't know what "better" means other than subjective terms.

But, I've been using P.I.N.G (Partimage Is Not Ghost) -- a front-end to Partimage, that comes on a bootable ISO format, and can be installed to the hard drive, for years.

It's a quick and easy app for doing disk imaging/restoring with little fuss.

Details are at windowsdream.com

---

### Post by phillw on 2009-10-27
> **zfranciscus said:**
> Hi,

I found 2 good open source back up software for Linux. I would like to know whether anyone has used them before and how was your experience with them. 

[FSArchiver]("http://www.fsarchiver.org/Main_Page")
[Partimage]("http://www.partimage.org/Main_Page")

Is there other back up software for Linux that is better than the above 2 ?

Cheers ;)

When you're ready to dip your toe into script, this thread is excellent ...

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Explains what is happening.

Only thing to note is ...

don't 

sudo su
to gain root user..

Instead ...

cd /
then 

sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
sudo'ing to root is not the way to do most things, issue the sudo before the command you wish to execute as 'root user'.

The above thread, tho' long & involved, will introduce you to the lay out of files in your machine.

Have fun.

Phill.

---

### Post by Ron_ on 2009-11-30
I am grateful to find phillw's note.  I had seen the forum thread that he mentions, but even as a newbie I was extremely wary of sudo su.  Too many tales of woe around that one.

Can anyone provide a "safe" command line that I can use by rote (with deeper understanding later) to transfer sbackup output to dvd?

---

### Post by presence1960 on 2009-11-30
> **Mark Phelps said:**
> Don't know what "better" means other than subjective terms.

But, I've been using P.I.N.G (Partimage Is Not Ghost) -- a front-end to Partimage, that comes on a bootable ISO format, and can be installed to the hard drive, for years.

It's a quick and easy app for doing disk imaging/restoring with little fuss.

Details are at windowsdream.com

+1 for PING. I use it to make an image of my OSs and data partition. I also use rsync (grsync if you aren't comfortable with command line). I have both images (PING) and regular directories/files (rsync) as backups. I feel pretty secure because not only do I have both of those, but they are both on an internal disk and an external disk. I learned many years ago the pain of not having a backup plan in place and running it on a regular basis.

---

### Post by Mark Phelps on 2009-12-01
Sorry to change my tune, but apparently, PartImage does NOT support Ext4 filesystems, and according to rumours, is not going to be enhanced to do so.

I only discovered this myself when I tried to use PING to backup my newly-installed 9.10 system and saw the error log where it failed.

I've posted on the PING forum about this, but to date, have received no responses from the devs.

So, until PartImage is "enhanced", or PING is changed to use something else, I can't recommend PING for Ext4-based filesystems.

Like others now, I'm looking into FSArchiver as a replacement.

---

### Post by darkod on 2009-12-01
I am also new to Ubuntu so I didn't need any linux backup solution before, but what do more experienced users think about CloneZilla? I see it's not mentioned here and it sounds interesting. Bootable, with ntfs/ext3/ext4 support, at least according to their website.

---

### Post by presence1960 on 2009-12-01
> **Mark Phelps said:**
> Sorry to change my tune, but apparently, PartImage does NOT support Ext4 filesystems, and according to rumours, is not going to be enhanced to do so.

I only discovered this myself when I tried to use PING to backup my newly-installed 9.10 system and saw the error log where it failed.

I've posted on the PING forum about this, but to date, have received no responses from the devs.

So, until PartImage is "enhanced", or PING is changed to use something else, I can't recommend PING for Ext4-based filesystems.

Like others now, I'm looking into FSArchiver as a replacement.

Mark, I backed up my 64 bit ext4 9.04 with PING and had no problem. After reading your post I went to my backup disk and indeed everything is there. Here is a pic of Jaunty's PING backup files. I will try in a little to use PING to backup my karmic which is also ext4. Will report back.

---

### Post by presence1960 on 2009-12-01
I experienced the problem with Karmic & PING. It went to the backup screen but then blue screened and rebooted. But as you can see from my previous post I have used PING to back up ext 4 Jaunty sdc6 partition. This is strange I have to say.

---

### Post by newb85 on 2009-12-02
> **Ron_ said:**
> I am grateful to find phillw's note.  I had seen the forum thread that he mentions, but even as a newbie I was extremely wary of sudo su.  Too many tales of woe around that one.

Can anyone provide a "safe" command line that I can use by rote (with deeper understanding later) to transfer sbackup output to dvd?

                                       &#65279;[FONT=Verdana][SIZE=1]Are you trying to create a DVD you can restore from directly, or do you plan to copy the contents of the DVD to the hard drive before restoring?  If you're not trying to restore directly, then all you need to do is copy the destination file (set in the Destination tab of SBackup) to the DVD as data.  You have a plethora of ways you can do this.  First example that comes to mind: Brasero comes stock on Ubuntu (Applications->Accessories->CD/DVD Creator in Jaunty), and is a simple drag-and-drop interface.  

*Of course, I've assumed that the size of your backup file will fit onto the DVD.  If not, I don't know whether compressing it into something like a .gzip or a .bzip will help.  I don't have any experience with SBackup, so I don't know anything about the backup file's format.

Out of curiosity, are you scheduling routine backups in SBackup, or doing them manually?  The scheduling features look really nice, but only halfway useful if you want to back up to removable media.[/SIZE][/FONT]

---

### Post by Ron_ on 2009-12-02
From what I read, SBackup may be essentially a front-end for tar.  It's configuration opens with sudo-to-root, and by default it backs up /var, /home, /usr/local and /etc, while excluding a bunch of other direcories.  In so doing, it produces output owned by root, so Brasero's drag-and-drop interface does not work.  I tried gksudo brasero, but I still couldn't see the size of the output file, so I am still a little gun-shy.

Ideally, SBackup would write and restore directly to/from DVD (size permitting.)  I understand that the developers considered this but ran out of time.  (Of course, the developers also ought to find a way to split an arbitrarily large backup file across multiple DVD's.)  For now, it's not too much trouble for me to copy a whole DVD to disk if/when I need to restore.

My backup schedule reflects the idiosyncrocies of my own habits.  I save all of my business e-mails forever.  This creates a pretty large database that is constantly being modified.  (Actually, I do use Thunderbird's Local Folders to hold the really old stuff.)  For that reason, I set SBackup to run an incremental backup only weekly.   I have set SBackup to run a full backup monthly, but my system is only 1 month old, so I have seen only one full backup.  All of these go to disk, so there is no need to mount media and they can run at night. I usually copy a full backup to removeable media every 3 months.

---

### Post by phillw on 2009-12-02
> **Ron_ said:**
> I am grateful to find phillw's note.  I had seen the forum thread that he mentions, but even as a newbie I was extremely wary of sudo su.  Too many tales of woe around that one.

Can anyone provide a "safe" command line that I can use by rote (with deeper understanding later) to transfer sbackup output to dvd?

Youll be pleased / horrified to know that I've just sent my 1st draft copy of the tar backup script building off to be proof read & nit-picked for any horrors !! - It'll be a couple / few more days before I will post it as a how-to.

In researching for it, i found a gui backup called pybackpack  [http://andrewprice.me.uk/projects/pybackpack/](http://andrewprice.me.uk/projects/pybackpack/)

You may want to have a look at that one.
 If you PM me, I'll let you dry-run the how-to in a 1-2-1 IM environment once it has got past the proof-reading stage.

Regards,

Phill.

---

### Post by phillw on 2009-12-02
> **Ron_ said:**
> From what I read, SBackup may be essentially a front-end for tar.  It's configuration opens with sudo-to-root, and by default it backs up /var, /home, /usr/local and /etc, while excluding a bunch of other direcories.  In so doing, it produces output owned by root, so Brasero's drag-and-drop interface does not work.  I tried gksudo brasero, but I still couldn't see the size of the output file, so I am still a little gun-shy.

Ideally, SBackup would write and restore directly to/from DVD (size permitting.)  I understand that the developers considered this but ran out of time.  (Of course, the developers also ought to find a way to split an arbitrarily large backup file across multiple DVD's.)  For now, it's not too much trouble for me to copy a whole DVD to disk if/when I need to restore.

My backup schedule reflects the idiosyncrocies of my own habits.  I save all of my business e-mails forever.  This creates a pretty large database that is constantly being modified.  (Actually, I do use Thunderbird's Local Folders to hold the really old stuff.)  For that reason, I set SBackup to run an incremental backup only weekly.   I have set SBackup to run a full backup monthly, but my system is only 1 month old, so I have seen only one full backup.  All of these go to disk, so there is no need to mount media and they can run at night. I usually copy a full backup to removeable media every 3 months.

Thanks, I'll add that option into the Script How-To that I'm developing - it won't look too pretty (says change to volume 2, or something like that - from memeory - but I can get it to split the output into DVD sized chunks)

I'm not sure if I can over-ride the 'press enter to continue' tho' for a cron based backup :-\

Regards,

Phill.

---

### Post by Ron_ on 2009-12-02
Phill,

While you were writing, I continued my research.  I also came across pybackpack in one of the forums, but here's what I am thinking....

It's hard to beat SBackup for set-it-and-forget-it simplicity.  For my manual quarterly copies of SBackup output to DVDs, I might try sudo FSArchive savedir, which seems to have most/all of the features that I mentioned, using one command line.

Any red flags on this approach?

I look forward to reading your how-to.  Your offer of a dry-run is much appreciated.  I feel that I am too inexperienced to be one of the first users, though, even 1-2-1.

Thanks again.

---

### Post by phillw on 2009-12-02
> **Ron_ said:**
> Phill,

While you were writing, I continued my research.  I also came across pybackpack in one of the forums, but here's what I am thinking....

It's hard to beat SBackup for set-it-and-forget-it simplicity.  For my manual quarterly copies of SBackup output to DVDs, I might try sudo FSArchive savedir, which seems to have most/all of the features that I mentioned, using one command line.

Any red flags on this approach?

I look forward to reading your how-to.  Your offer of a dry-run is much appreciated.  I feel that I am too inexperienced to be one of the first users, though, even 1-2-1.

Thanks again.

I haven't used SBackup, but between clonezilla and pybackpack you have decent gui backup programmes. My script building is for those of us with non-standard installations (links to mount-points on our desktops etc.)  Pretty much each script will be unique to that machine. I've added some idiot (oops, user) proofing to it. It's also a how-to understand your storage devices and areas. - Quite a head-ache to write :-)

Phill.

---

### Post by newb85 on 2009-12-03
> **Ron_ said:**
> In so doing, it produces output owned by root, so Brasero's drag-and-drop interface does not work.  I tried gksudo brasero, but I still couldn't see the size of the output file, so I am still a little gun-shy.

Can't you simply sudo chmod the output file so that you *can* drag-and-drop the file?  (I suppose SBackup restricts reading privileges to root for privacy on multi-user systems...)

---

### Post by Ron_ on 2009-12-03
Maybe chmod or chown, but I am reluctant to expose my stuff till I know what I am doing.  (On these files, I frequently get an "error while getting sharing information.")  More to the point, I don't know whether changing ownership of the backup will affect ownership of restored files.  For example, I don't think I want files in /etc to have any owner other than root.

I will eventually get around to trying FSArchive (as described above), and I will report back my results.

---

### Post by phillw on 2009-12-03
When I'm helping out 1-2-1 for people about to embark on re-slicing, merging etc of their partitions, I write a quick backup script for them. The idea behind the 'how-to' is to allow people to learn how to write, and tune, their own scripts. One of the reasons I'm doing this is that I also run a server environment on my computer for Designing & programming dynamic web-sites & I also wanted a nice easy command line one for backing up my databases, that has been done - the next task was to have a backup that would backup what i wanted, when I wanted and to where i wanted. 

The actual running of the backups is along the lines of
```
sudo fullbackup.sh
sudo homebackup.sh
sudo fullbackup-nomusic-vids.sh
```etc. 
It was when I started it, I quickly realised I was going to have to a section on fdisk, df etc..

I've seen some quite wonderful setups of partitions, and, tbh - giving someone a script and a quick why I've done it that way has always been received well - So, I've had a go at writing down the path I follow to get them the script to do the job that they need.

As you can see by my Sig - the area I'd normally pop it onto for people to have a look & check it is down & I don't want to pop it onto general area until I've had a couple of people check my logic & see if I've missed any steps out.

Oh, and the NOT messing up of ownerships, permissions etc., was a #1 priority and works !!!

Phill.

---

### Post by wkulecz on 2009-12-04
I use rsync from a cron job to an second drive.  Keep a live cd handy and know how to re-install grub or grub2 and you can be up again in minutes should the boot drive fail.

after sudo -i I do crontab -e and enter a line like:

5 1 * * * rsync -ax / /media/disk1 > /root/backup.log.txt 2>&1

This assumes the backup drive is alwyas mounted.  To make it more fancy I make a shell script that mounts the exteranl drive, does the rsync command and unmounts the drive.  The *.gvfs errors you can ignore.

Learn about rsync and cron. It'll serve you well.  With hard drives so large and cheap these days, unless you are an enterprise class site, its just not worth screwing around with backup solutions more complicated than just cloning things to another drive.

Occasionally I do: sudo rsync -ax --delete / /media/disk1 to clean out stuff I've deleted on the main system that remains on the cloned system from the daily rsync backup command.

I've been doing this since RedHat 3 and have never lost any data despite several hard drive failures over the years.

--wally.

---

### Post by Ron_ on 2009-12-16
> My backup schedule reflects the idiosyncrocies of my own work habits. I save all of my business e-mails forever. This creates a pretty large database that is constantly being modified. (Actually, I do use Thunderbird's Local Folders to hold the really old stuff.) For that reason, I use SBackup *[SimpleBackup]* to run an incremental backup only weekly. I set SBackup to run a full backup monthly.  All of these go to disk, so there is no need to mount media, and they can run overnight. *[Actually, the process is fast enough that it could be run during the day.]  *I usually copy a full monthly backup to removeable media every 3 months.> It's hard to beat SBackup for set-it-and-forget-it simplicity. For my manual quarterly copies of SBackup output to DVDs, I might try sudo FSArchiver savedir, which seems to have most/all of the features that I mentioned, using one command line.
Today I gave FSArchiver a shot.  I had some trouble copying directly to unformatted DVDs, but I had success by doing the following:
1) create a disk directory (*e.g., *FSArchiver_temp)  *[Don't forget to exclude this directory from being backed up in the future.]*
2) sudo fsarchiver -z 1 -s 4600 savedir /FSArchiver_temp/2009-12-15_xxxxxxx_ful.fsa 2009-12-15_xxxxxxx.ful

This segmented the SimpleBackup subdirectory (containing one full backup) into 4.5GB files in FSArchiver_temp that I plan to burn directly to DVD using Nautilus or Brasero.

Using this scheme, I expect to be able to restore 1 or many files by reversing the 2-step process:  use "FSArchiver restdir ..." to copy the backup files from DVD to disk; then use SimpleBackup to restore the individual files.  This is more steps than I might like, but I hope never to have to do it.  It protects me from 2 kinds of failures:  stupid user behavior (*i.e., *by yours truly) that causes the loss of limited assets; and, catastrophic loss of the PC (*e.g.,* due to tornado or theft.)   (The DVDs are stored, of course, offsite.)  In the former case, restoring from my incremental backups on disk should be enough.   In the latter case, I would expect to have to purchase new equipment, build new partitions and install a new OS anyway.

---

### Post by phillw on 2009-12-16
> **Ron_ said:**
> I am grateful to find phillw's note.  I had seen the forum thread that he mentions, but even as a newbie I was extremely wary of sudo su.  Too many tales of woe around that one.

Can anyone provide a "safe" command line that I can use by rote (with deeper understanding later) to transfer sbackup output to dvd?

Hi, there is a How-To based on the tar script - It lives over at [http://www.vpolink.com/showthread.php?t=170](http://www.vpolink.com/showthread.php?t=170)  It does cover quite a lot - And I'd be grateful of any feed-back.

Regards,

Phill.

---

### Post by Ron_ on 2009-12-16
Thanks, Phill.  I think your postings around #16 might be helpful to other readers' understanding of where this best applies.

---

### Post by Ron_ on 2009-12-17
Just an update on work in progress, because things have not gone smoothly.

FSArchiver ran nicely with size set to 4300MB rather than 4600MB.  One of my DVD burning utilities complained that that was too large, too.  Setting size to 4000MB got me over that hump.

1) create a disk directory (*e.g., *FSArchiver_temp)  *[Don't forget to exclude this directory from being backed up in the future.]*
2) sudo fsarchiver -z 1 -s 4000 savedir /FSArchiver_temp/2009-12-15_xxxxxxx_ful.fsa 2009-12-15_xxxxxxx.ful

Now my full backup from SBackup is ready to be copied to multiple DVDs.

Burning data DVDs in Karmic is a challenge, though.  It may be a Gnome bug.  I trashed a stack of media trying to use up-to-date versions of both Brasero and GnomeBaker. I have a new low-end HP desktop with a 16x DVD-/+RW drive, and I am using DVD-R media. I have tried 16x and 4x. The message I get from both apps is:
 :-[ WRITE@LBA=e0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
:-[ write failed: Invalid argument

This seems to be a widespread problem.  See related threads at:
[https://answers.launchpad.net/ubuntu...question/94334]("https://answers.launchpad.net/ubuntu/+source/brasero/+question/94334")
[https://bugs.launchpad.net/ubuntu/+s...ro/+bug/405544]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544")
[http://swiss.ubuntuforums.org/showth...1327809&page=2]("http://swiss.ubuntuforums.org/showthread.php?t=1327809&page=2")

---

### Post by litmus1111 on 2009-12-19
Have you thought about removing the hassle of backing up to removable media and using opensource online backups like [http://www.boxbackup.org/](http://www.boxbackup.org/) or [http://www.diffingo.com/oss/fwbackups ]("http://www.diffingo.com/oss/fwbackups.")?
There are even some hosted solutions for boxbackup if you do not want the hassle of creating your own server  [http://www.boxbackup.org/trac/wiki/Marketplace](http://www.boxbackup.org/trac/wiki/Marketplace) like [http://www.remotebackupzone.com]("http://www.remotebackupzone.com/") who offer boxbackup at 25 G  per month for under $5. Which is about the same price as using DVD's but may be less hassle, because everything is automated with out human interaction. Box backup uses AES encryption using a key which only you hold, this means a third party provider can't read your data. 

If you have access to an offsite server that runs ssh, then fwbackup has some nice features although you may want to encrypt your data first if you do not trust the offsite server. 

Alex

---

### Post by Ron_ on 2009-12-20
Thanks, Alex.  That's good advice and certainly a viable solution.

Backup to DVD should have been dirt-simple, except for three issues: (1) I am new to Ubuntu, so I have a steep learning curve on the capabilities and limitations of the available software; (2) there seemed to be no readers of this thread who had made it work this way before; and (3) I was recently told that burning to DVD-R under 9.10 does not work because of a regression in the 2.6.31 kernel.

Actually, when it gets working, this setup will be very low maintenance and as far as I can tell, it will meet all of my needs.  SBackup (*i.e.*, Simple Backup) produces and retains incremental and full backups on a flexible schedule.  From these, I can restore an individual file or whole directories.  When my retention strategy calls for making an offsite copy, FSArchiver does a nice job of packaging the SBackup output into 4GB segments.  At my own convenience, I can burn these files to removeable media.  

As I said earlier, everyone's backup schedule reflects the demands and idiosyncracies of their own work habits.  My steps are:
(1) SBackup -- set it and forget it -- for weekly incrementals and monthly full backups.  Retain these on disk for 120 days.
(2) Every few months -- about every 3rd full backup -- run FSArchiver (one command line) against the latest SBackup output to prepare for step (3). *[Some people might prefer to use tar with multi-volume output at this step, but SBackup has a nice GUI and FSARchiver is pretty straight-forward, so that is my choice.   Another alternative might be to write a cron script to run FSArchiver or tar** for both steps (1) and (2). ]*
(3) Burn the FSArchiver output onto (currently 2) DVDs.

Incidentally, SBackup output itself can be directed to an offsite, networked disk drive, if you have one available to you.

Last thought:  on this schedule, I will produce two full backups before each new release of Ubuntu.  Every other full backup is a good time to upgrade.

---

### Post by jimpr13 on 2009-12-20
Yes,you have right but there may be problem with sudo archiver

---

### Post by phillw on 2009-12-20
> **litmus1111 said:**
> Have you thought about removing the hassle of backing up to removable media and using opensource online backups like [http://www.boxbackup.org/](http://www.boxbackup.org/) or [http://www.diffingo.com/oss/fwbackups ]("http://www.diffingo.com/oss/fwbackups.")?
There are even some hosted solutions for boxbackup if you do not want the hassle of creating your own server  [http://www.boxbackup.org/trac/wiki/Marketplace](http://www.boxbackup.org/trac/wiki/Marketplace) like [http://www.remotebackupzone.com]("http://www.remotebackupzone.com/") who offer boxbackup at 25 G  per month for under $5. Which is about the same price as using DVD's but may be less hassle, because everything is automated with out human interaction. Box backup uses AES encryption using a key which only you hold, this means a third party provider can't read your data. 

If you have access to an offsite server that runs ssh, then fwbackup has some nice features although you may want to encrypt your data first if you do not trust the offsite server. 

Alex

On the topic of off-site storage, humyo give you 10GB for free. upto 5GB of media the remainder for everything else. I pop iso's on there for rescuing Win stuff (Don't tell anyone !!) [http://www.humyo.com/HOME](http://www.humyo.com/HOME)  It, too, uses https for access & I like the ability to 'e-mail an invite' to someone to be able to download something from my little archive area of iso's - you can pay for more storage room if you need.

(On a different note, and honest - it's NOT an advert, just somewhere I use. VPOLink offer a hosting service with the usual MySQL dbases (note the plural - the default is 10, but you can have more) At my last check, it was 1GB hard disk space default, but as he has several TB drives kicking their heels doing nothing I'm sure storage space would not be a problem - It's at 15USD / Year - PM me if you'd like any other info. The guy in charge of VPOLink is a real nice bloke & runs his system on Linux).

Phill.

---

### Post by mmncs on 2011-04-28
I would recommend Tartarus which is a flexible yet simple backup solution.

Description: Tartarus is a software that provides a nice wrapper around basic Unix tools such as tar, find and curl (well, that's not that basic) to provide a seamless backup solution, aimed at automatic gathering and backup. It has the ability to do full as well as incremental backups and is published by Stefan Tomanek under the rules of the GPL.

You can check you my complete guide here: [http://www.mmncs.com/2011/04/how-to-install-and-setup-a-backup-system-on-linux-debian-based-systems-using-tartarus/](http://www.mmncs.com/2011/04/how-to-install-and-setup-a-backup-system-on-linux-debian-based-systems-using-tartarus/)

Chris
[www.mmncs.com](www.mmncs.com)

---

