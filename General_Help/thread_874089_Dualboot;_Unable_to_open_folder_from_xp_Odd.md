---
title: "Dualboot; Unable to open folder from xp: Odd"
date: 2008-07-29
forum: General Help
---

### Post by Dieseler on 2008-07-29
I have set up a dual boot machine with Ubuntu master drive,
Win Xp on secondary drive
and another drive as slave for data only behind my cd rom on the ide cable.
Three drives total.

I edited grub sucessfully and now have the option to boot to either OS from Grub. YAY.
I can see the Ide hard drive and all of the folders it contains from either Win Xp or Ubuntu just like I wanted except for one minor problem.

Two of the folders on the data drive say I do not have permission to open them from inside Xp. I can open all of the others and move or copy files any way I want except for those two folders.
They also say that they are empty from Win Xp. 
I have double checked and the data is there and accessible from Ubuntu.
I also checked all of the permissions on all of the folders on the data drive, They are all set the same so I do not think that is it.
I'm new to Ubuntu by the way but I'm learning a lot. I spent a good deal of time searching for a situation like this through Google and here and couldn't find a solution.
Any ideas?
One more thing, I do not see the Ubuntu drive from Win Xp but that is fine. I prefer it that way. I do see the Win Xp drive from Ubuntu though and I am able to grab stuff from it for editing when I need to.
Data drive is the only one I need to see from both.

---

### Post by Dieseler on 2008-07-29
One more thing.
Both the Ubuntu and the Win Xp installs are new.
No permissions have been changed for any folders on any of the drives.

---

### Post by Dieseler on 2008-07-29
Ok, I didn't exactly fix it but I did find a way around it.
From Ubuntu I accessed the storage only drive.
I renamed the two folders inaccessible from WinXp.
Then I made two new folders with the old names.
Then I transferred my files from the renamed folders to the newly created folders with the old names.
Then I rebooted back to Win Xp and I was able to access the newly created folders and still unable to access the old renamed, however no matter as the data was in the new ones.

Now if I could find out what caused the problem to start with I would feel better.
or Call it solved I guess.
Thanks.

---

### Post by Dieseler on 2008-07-29
Bah, I thought I had it worked out.
I can now see and open the two new folders.
I can see all 30 of the folders contained in the first new folder and I can access the first two folders in it but I get the same message access denied on all the others.
Basically the same deal with the other new folder.
Weird.
I'm starting to think it has something to do with the last update but I don't want to jump to conclusions cause I'm a newb to Linux and I don't even know what was in the update.

Is this the right place for this thread?

---

### Post by R Clemons on 2008-07-29
I'm guessing the data partition is ntfs correct? what kind of files are you unable to open?

---

### Post by Dieseler on 2008-07-29
> **R Clemons said:**
> I'm guessing the data partition is ntfs correct? what kind of files are you unable to open?

Yes that is correct.
The drive was formatted ntfs and I use it exclusively for data.
The files are really just folders created from Ubuntu.
The files inside range from Pdf to mpeg video.
It looks as if I am going to have to rebuild the entire directory with new folders to replace the ones I can't access in Windows.
From the bottom up.
I guess my question is why can windows see, open and allow access to one folder created from Ubuntu and then not be able to on the next one?
I would almost swear that I was able to access these same folders the day before yesterday but that is almost at best because I just recently set this box up like this to dualboot with three hard drives.

---

### Post by R Clemons on 2008-07-29
I know you didn't purposefully change the file permissions, but open up your file manager in linux and make sure that the folders you can open have the same permissions as the ones you can't.

---

### Post by Dieseler on 2008-07-29
> **R Clemons said:**
> I know you didn't purposefully change the file permissions, but open up your file manager in linux and make sure that the folders you can open have the same permissions as the ones you can't.

Yeah that was the first thing I checked.
They are all identical and haven't been monkeyed with.
Hey I appreciate the idea though.
I'm sort of lost on this and I'm thinking I better just move my Data back to Windoze before I really get :popcorn:ed.
:lolflag:

They (WinXp and Ubuntu) just don't seem to want to play nice together.

---

### Post by R Clemons on 2008-07-29
ubuntu just plays out of Window's league.  You'll never have a problem accessing anything from windows in Ubuntu, it's only when you attempt to access Ubuntu files from Windows.  Anything I want to be secure I leave in Ubuntu or have fully encrypted.  Otherwise leave it in Windows and you can access it from either.

---

### Post by 3rods on 2008-07-29
Sounds like the problem is either Windows not accepting the folder UNIX permissions (possible) or the folder has permission "residue" from another install (more likely since you said it was new install - guessing the 'data' drive is from old install).

In Windows, forcefully take ownership of the folders. You may have to turn of "Simple File Sharing" (My Computer>Tools>Folder Options  || View Tab|| Scroll down, uncheck last option called "Use Simple File Sharing".

Find the folder(s) in question or it's parent folder (or better, the entire drive), Right Click > Properties > Sharing & Security  || Security Tab || Advanced  Button (on bottom)|| Owner Tab || Choose Administrators (if you are one) or your user as the owner in the box, check "Replace owner on subcontainer and objects".

If you are not in the box, go back to properties > security tab and make sure your user is in the box with full rights. If you see a bunch of junk users klgfd900fa9335-fgsd-ss-36223 (or similar) you can delete them, they are old owners from prior installs. 

**If this does not solve the issue,** you may have data corruption or the NTFS file table could be damaged. Ubuntu and NTFS/3g is a lot less strict than Windows is on NTFS. You may get less space, and you lose the ability to have files larger than 4GB, but I would use FAT32 for the swap drive. I still don't trust NTFS-3G in Linux. It's not that I don't trust Linux, it's that I don't trust Windows after Linux is done.  Windows always wants to touch, touch, touch everything. 

I'd be suprised if ownership wasn't your problem. Either way, let us know.

---

### Post by Dieseler on 2008-07-30
Hey 3rods,
I just got that post and will be looking into it immediately. You are correct to assume that the Drive in question is in fact saved from both a previous Windows and Ubuntu install and what you are saying makes perfect sense.
I will most definitely get back here and repost my findings.
Thanks a bunch.

---

### Post by Dieseler on 2008-07-30
Maybe it wasn't permissions. I went through what you explained but in a slightly different manner.
In Xp Home Edition you have to log into safe mode.
From there I right clicked the drive, then properties and finally to security.
I saw that the permissions were checked properly then I went to advanced and checked the box, Replace permission entries on child folders.
Windows went through a settings fit and when it finished I rebooted.
Got the same result.
What I am noticing now after rebuilding one of the directories completely from the bottom up is that now I can access my CHM. files yet I still cannot access any PDF. or TXT. files and that makes me wonder.
I'm considering backing up the files to my Ubuntu disk and reformatting that entire drive to FAT32 like you suggested earlier.
I'm gonna wait and see if anyone else posts a clue before I go that far with it.
I can access all of my files from Ubuntu until I make that decision.

---

### Post by 3rods on 2008-07-30
What do you mean you can't access your PDF and TXT files in XP? They just don't open or you don't see them in the directory? Were you able to open that directory you couldn't open?

---

### Post by Dieseler on 2008-07-30
> **3rods said:**
> What do you mean you can't access your PDF and TXT files in XP? They just don't open or you don't see them in the directory? Were you able to open that directory you couldn't open?

I can open the directories now that I rebuilt them and I can open and view CHM files but PDF and txt files that I know are there( I checked from Ubuntu) are saying that they aren't there with an error, I wish I could remember what exactly it said. I can see them and click on them but they won't open.

---

### Post by Dieseler on 2008-07-30
Foxit Reader error,

E:\Folder\Folder\filename.pdf
Couldnot open file.
File not found.

Adobe Reader error,

There was an error opening this document.
Access denied.


Those are the errors I'm getting on the pdf files.
That directory contains only pdf, chm. and txt. files.
The chm. files are now operating while the others are not.
Earlier I could not even access the folders they were in.
Its getting better.

---

### Post by 3rods on 2008-07-31
Just for fun, if you were to copy one of said files (PDF or TXT) to your desktop, what happens? Can you open it? Can you rename it? 

If you can open them from your desktop, I would suspect a folder or drive issue. If you can't, then it's definitely permissions.

---

### Post by Dieseler on 2008-07-31
> **3rods said:**
> Just for fun, if you were to copy one of said files (PDF or TXT) to your desktop, what happens? Can you open it? Can you rename it? 

If you can open them from your desktop, I would suspect a folder or drive issue. If you can't, then it's definitely permissions.

No, it definitely won't let me copy or manipulate those files in any kind of way from Xp. 
It will tell me the file does not exist.
I tried the permissions route and just rebuilding the directory with some success but now I think I'm going to format the drive as FAT then rebuild the directory again and see how Xp likes it then.

To be totally honest 3rod, if I find a good working cronable backup script
I won't even care that windoze can't access those files. I have run across a few threads here with some but I have to be careful because those threads are a bit dated, I'm new to Linux and the Bash script is still over my head.
I'm already ahead of the game though by being able to dual boot to windoze for whatever I can't do in Ubuntu which is very little, and in my opinion Ubuntu is far superior to Windoze anyway.
My mind is made, Ubuntu stays and Windoze can learn to deal with it.
Now to find that working backup script.

---

### Post by 3rods on 2008-07-31
I was working on a backup script to gzip and tar files to a network share. 

I'll have to look around for it, it was almost complete. Basically, it used tar to and gzip the files and folders I wanted, I used a time stamp in the file name so it would always create unique files. I made it mount the network share, copy over the tar, and then unmount the share when it was done. I'm sure you could do something like that if you google it a little. 

Check this out to look at the date function [http://www.computerhope.com/unix/udate.htm]("http://www.computerhope.com/unix/udate.htm")

Then you can just do a ```
tar -czvf /home/user/mynewtarfile-2008-07-03.tar.gz /var/www/* 
```


```
mount -t auto -o username=foo,password=bar,rw /media/mountfolder //192.168.1.100/shareddrive 
``` You can use the PC name if you don't have a static IP for the remote computer.


Now all you need to do is make a bash script:

Start off with a text file, chmod 700 so you can write to it and execute it as a script.

```
chmod 700 mynewscript
vim mynewscript 
```

press **i** to edit, then start off with #/bin/bash

There you go. Start putting commands in it and see if it works. 

Another good idea is to use a txt file as input for tar; read the man page on how to do that. 


Good luck, welcome to Ubuntu Linux.


Forgot, use ./mynewscript to run it.

---

### Post by Dieseler on 2008-07-31
You've been a great help 3rods, I really appreciate the input.
I'm reading [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php) right now. Just learning about Linux has been fun in itself.
I have been looking at this thread by Heliode,
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Which contains the commands,

> tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /
and this thread by Lunde,
[http://ubuntuforums.org/showthread.php?t=47999&highlight=backup+script](http://ubuntuforums.org/showthread.php?t=47999&highlight=backup+script)
which contains this rather large script,

> 
#!/bin/bash
#
# A very simple backup script created by: 
# Fredrik Lunde
# [http://www.wine-bank.com/profile](http://www.wine-bank.com/profile)
#
# This script is related to the article:
# Howto: Backup & Restore script. Part 1
# Published at: [http://ubuntuforums.org/showthread.php?p=249408](http://ubuntuforums.org/showthread.php?p=249408)
#
# Instructions: 
# Change the values of "STORAGE_MEDIA" and "ROOT_EXCLUDE_DIRS"
# Name this file "restore", make it "executable" and put it in "/bin"
# Invoke by: "sudo backup"
#
# Feel free to modify however you want. If you make something better, 
# please post it at the ubuntuforum.org thread above :-)
#
#------------------------------------------------------------------------------------
#    CHANGE THE VALUES BELOW TO SUIT YOUR CONFIGURATION 
#------------------------------------------------------------------------------------

ROOT="/*"
ROOT_EXCLUDE_DIRS="--exclude=/lost+found --exclude=/proc --exclude=/mnt --exclude=/sys --exclude=/backup.tgz"

#------------------------------------------------------------------------------------
#             DO NOT CHANGE ANYTHING BELOW THIS LINE           
#------------------------------------------------------------------------------------
if [ "$USER" != "root" ]; then 
    echo "You are not root user, use: sudo backup"
    exit
fi
clear
echo "|-------------------------------------------------------------" 
echo "|  IT'S RECOMMENDED TO RUN THIS SCRIPT BEFORE GNOME LOGIN  "
echo "|-------------------- Press CTRL+ALT+F1 at the GDM login"
echo "|-------------------------------------------------------------"
echo "|  BACKUP YOUR SYSTEM: "
OPTIONS="Backup Exit"
LIST="1) Backup 2) Exit" 

select opt in $OPTIONS; do
if [ "$opt" = "Exit" ]; then
    clear
    exit

elif [ "$opt" = "Backup" ]; then
    tar cvpfz /backup.tgz $ROOT $ROOT_EXCLUDE_DIRS
    echo "BACKUP COMPLETE"
    exit
else
    clear
    echo "| BAD OPTION! Select 1 or 2"
    echo "|--------------------------------------------------------------"
    echo "|  BACKUP YOUR SYSTEM: "
    echo $LIST
fi
done

That is a really nice looking script.
I believe that between the two of those and the example above that you provided that I will be able to configure a hybrid that will work like I want.
Thanks again, 
Now I'm gonna see if I can figure out how to call this thread solved because its original intention seems to be more of a Windows issue than Linux anyway.

---

