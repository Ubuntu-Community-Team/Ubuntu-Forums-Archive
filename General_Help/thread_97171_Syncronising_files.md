---
title: "Syncronising files"
date: 2005-11-30
forum: General Help
---

### Post by Daminator on 2005-11-30
I want to have the files that are in my FAT32 partition synchronised with files on a separate computer running XP. The file structure will be the same.

I'd to be able to just press a button to synchronise the files, and the most recent one will be copied to the other machine (when they are connected) no matter which machine was modified.

So, for example, if I take my laptop (Ubuntu) out and about and write some emails, and my girlfriend writes a word document on the home Machine (currently XP), I'd like the synchronisation to take place both ways and to be told if the same file has been updated on both (I doubt this will ever happen).

Is this possible?

I've been told it's possible with 2 XP machines and found a couple of apps, but what about Linux to Linux and Linux to XP?

This would be SOOO useful if anyone can point me in the right direction

---

### Post by Daminator on 2005-12-02
Is there anything around that can do any part of this???

---

### Post by 23meg on 2005-12-02
The great *nix syncing tool **rsync** was ported to windows as well, so chances are it will do the job for you. ```
man rsync
```

[http://www.gaztronics.net/rsync.php](http://www.gaztronics.net/rsync.php)

---

### Post by Daminator on 2005-12-03
Thanks for that, I'll take a look

---

### Post by adam.skinner on 2005-12-03
I'd look to [Unsion]("http://www.cis.upenn.edu/~bcpierce/unison/").

---

### Post by Daminator on 2005-12-15
Is anyone out there using unison?

I'm having a royal pain in the ass trying to get ssh working and would be very greatful if someone could give me a few pointers!

Tried various different things, but just get 'port 22: connection refused' every single time.

---

### Post by David Valentine on 2006-01-30
I've been using unison, and it is good albeit clunky for what I needed.  You might want to check out [jfilesync]("http://jfilesync.sourceforge.net/"), which is written in Java and is therefore platform independent.  What I like about it is you can set up a profile of directory pairs to synchronize, making updating a snap.

---

### Post by Daminator on 2006-01-31
[QUOTE=David Valentine]I've been using unison, and it is good albeit clunky for what I needed.  You might want to check out [jfilesync]("http://jfilesync.sourceforge.net/"), which is written in Java and is therefore platform independent.  What I like about it is you can set up a profile of directory pairs to synchronize, making updating a snap.[/QUOTE]

I'm still struggling with Unison.
jfilesync could be a simpler alternative. Are you sure it can be used to sync between Linux and XP without any problems? How can I install it on Ubuntu??

---

### Post by David Valentine on 2006-01-31
> Are you sure it can be used to sync between Linux and XP without any problems?When it comes to computers in general and new software in particular, I am most definitely *not* sure. ;)  But I do know that jfilesync can sync network drives, so if you can mount xp or ubuntu as a network drive on the other, you should be set.

As for installation, here's what I did:

1.  Uncompressed the .zip file into a new folder (jfilesync) in my home folder
2.  Made sure the jfilesync.sh script file had appropriate permissions (chmod 755 jfilesync.sh)
3.  Used the Gnome Applications Menu Editor to add a new entry pointing to jfilesync.sh

By the way, I do like Unison for some things.  What exactly is giving you trouble on it?

---

### Post by professor_chaos on 2006-01-31
I use rsync to do a one way sync, but all you have to do is do it twice. Provided your XP machine is mounted.
something like this script... (put it in a cronjob, and you don't even have to click a button)

#!/bin/bash

rs="rsync -vruL" #rsync command

dest=/home/user/directory1 #destination for backup
source=/home/user/directory2 #dir of files to backup

$rs  $source $dest #backup command for first sync

dest=/home/user/directory2 #destination for backup
source=/home/user/directory1 #dir of files to backup

$rs  $source $dest #backup command for first sync

exit

---

### Post by rshel on 2006-01-31
Do any of the above mentioned solutions allow quick synchronization from Linux desktop to USB flash drive?  I use a flash drive to move files back and forth to (non-computer related, heavy word-processing) work.  I don't trust myself to keep track of what I've updated at work, so I don't like to just move all the files over.  At work on my Windows machine I use Second Copy.  Also Unison won't even recognize my USB drive when I plug it into my Unix machine, why?

thanks

---

### Post by David Valentine on 2006-02-01
> Do any of the above mentioned solutions allow quick synchronization from Linux desktop to USB flash drive?  I use a flash drive to move files back and forth to (non-computer related, heavy word-processing) work. I don't trust myself to keep track of what I've updated at work, so I don't like to just move all the files over.That's (almost) exactly what I'm doing, and exactly why I'm doing it.  I have to use a USB hard drive instead of a flash drive 'cause my files have gotten too numerous/large.> Also Unison won't even recognize my USB drive when I plug it into my Unix machine, why?Is your PC mounting your flash drive automatically?  Ubuntu seems to do a good job of that, but I have no idea about Unix.  Assuming yes, and assuming Unix is enough like Ubuntu for this to be valid, then just make sure you have one or more files with a .prf extension in your ~/.unison directory with the following lines in it/them:
```
root = /home/{username}/{DocFolder1}
root = /media/usbdisk/{DocFolder2}
```
Good luck!

---

### Post by rshel on 2006-02-01
I thought there had to be a way to make Unison recognize a usb drive as local directory.  I will give it a shot.  Thanks!

---

### Post by rshel on 2006-02-01
Another question.  I have been unable to start unison in its graphic user interface mode.  I type unison at the command line and it requests more  options on the command line as if it is in text mode.   I thought it was supposed to start up with gui if it was so compiled.  I installed it from synaptic with gtk but still no luck.  Any ideas what I'm doing wrong?

---

### Post by adamonduty on 2006-02-01
You could always try unison -ui gui . That should bring up a gui interface if its installed. 

I use unison to sync between my ubuntu laptop and my SUSE desktop. It works great, very solid. I also occasionally backup to an external hard drive with unison. 

Also, if you make a symlink from your home dir to say, /media/usbdrive (wherever it usually gets mounted), you could make unison sync between a dir in your home directory and your usb drive, although I don't know why you wouldn't just do it from /media/usbdrive.

---

### Post by joselin on 2006-02-01
You must type unison-gtk to start the ui.

---

### Post by Daminator on 2006-02-01
[QUOTE=David Valentine]When it comes to computers in general and new software in particular, I am most definitely *not* sure. ;)  But I do know that jfilesync can sync network drives, so if you can mount xp or ubuntu as a network drive on the other, you should be set.

As for installation, here's what I did:

1.  Uncompressed the .zip file into a new folder (jfilesync) in my home folder
2.  Made sure the jfilesync.sh script file had appropriate permissions (chmod 755 jfilesync.sh)
3.  Used the Gnome Applications Menu Editor to add a new entry pointing to jfilesync.sh

By the way, I do like Unison for some things.  What exactly is giving you trouble on it?[/QUOTE]


Thanks for that David. I'll try that with jfilesync.

As for Unison, I've just struggled getting my head around SSH (what the hell it is and how the hell it works) and getting it set up on my XP system. I think it's set up on XP now (using CYGWIN), but the whole 'home' directory stuff confuses me as someone coming from XP. Do the folders I'm synchronising have to be within 'home' that's now been set up on my XP system? I've not experimented much with it because of these fears.

I've also not been able to get the Unison GUI working. I've tried 'unison-gtk', but that just gives me that same (or similar) to if I'd typed 'unison'.

By the way David, when do you use Unison, and when do you use jfilesync? And why? What are each good and bad at?

Thanks
Damian

---

### Post by David Valentine on 2006-02-01
There are a couple of good resources out there on how to set up Unison for remote synchronization.  I used the one at [http://www.minezone.org/wiki/MVance/FileSyncingHowTo](http://www.minezone.org/wiki/MVance/FileSyncingHowTo) for the basics (I didn't do any of the "putty" stuff); basically, you run unison-gtk on the client machine and unison (text mode) on the server machine after setting both up to use a common port (I actually don't understand ports at all, but the directions were clear enough that I didn't have to).  I found some other potentially good resources by googling "unison howto".> when do you use Unison, and when do you use jfilesync? And why? What are each good and bad at?So far (this is definitely a "work in progress"), I have found Unison to be highly reliable but inconvenient and jfilesync to be convenient but difficult if a whole lot of major differences exist.  Thus I tend to run jfilesync routinely but unison when I've totally redone something (e.g., my directory structure).  As they say, however, your mileage may vary!  I think a great forum could be run on various users' experiences with different types of synchronizing software...

---

### Post by rshel on 2006-02-05
[QUOTE=joselin]You must type unison-gtk to start the ui.[/QUOTE]


Thanks!  I was not typing the "-" between unison-gtk.  Unison seems to work fine, though I'm sure I will have more questions when I have a chance to try to configure it for my needs.

---

### Post by rshel on 2006-02-05
Another Unison question.  I have a SimpleTech Simpleshare hard drive connected to my wireless/ethernet router on my home network.  I can see and access files on it from my Ubuntu machine and even mount the drive permanently on my desktop.  Ubuntu sees this drive as a SMB server on my Windows Network.  I have not been able to figure out how to get Unison to see this for syncing directly to the HD.  Is it possible?  Since the hd is attached to a router rather than a remote machine, I obviously can't run SSH or any other  protocol on it, right?  Or am I just too new at this to know what I'm talking about?   If all else fails I suppose I can just sync to a windows machine (which means I have to power one on) and then backup from there.  Or I can just backup from Linux manually.  But where's the fun in that? Any advice would be most welcome.

---

### Post by joselin on 2006-02-05
Hi,

First of all, i don't know if unison can backup from smb files, but i think that yes. Is better if you check it in their website.

What i do is to create a config file for unison (ex: ~/.unison/backup.pfr):

> # Unison preferences file
auto = true
batch = true
root = /folder_to_backup_to/
root = ssh://other_machine//folder_to_backup/

Then an script with a simple call to unison with this config file:

> #!/bin/bash
unison backup

And i execute this script from the cron every night at 4:20:

> 04 2 * * * /usr/bin/backup.sh

Regards.

---

