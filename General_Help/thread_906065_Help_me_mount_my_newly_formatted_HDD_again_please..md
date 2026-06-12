---
title: "Help me mount my newly formatted HDD again please."
date: 2008-08-31
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-31
I tried looking through all of my threads... I've had so many.

I just formated my 2nd hdd to ntfs so windows can easily read it.

Now I need to re-mount it to move all my media onto it.

Can anyone give me a quick how to?

what code do I run?

---

### Post by Taxman415a on 2008-08-31
There are two links in the community documentation that cover it pretty well.
The first is 
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
which doesn't actually tell you how to manually mount an ntf partition, but if you read ```
man mount
``` you'll notice you can just change the fs type in the given commandline from vfat to ntfs

Next if you want to do it automatically you need to set up your fstab file properly:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by PsychedelicWonders on 2008-08-31
alright I got all the way to the screen shot and not sure what to do because the hdd I am trying to mount isnt listed there.

Only seems hdd #1 shows?

---

### Post by PsychedelicWonders on 2008-08-31
Alright i dont know what I was thinking, but I ran the following code in the terminal:

psychedelicwonders@JohnnyScience:~$ sudo fdisk /dev/sdb
[sudo] password for psychedelicwonders: 

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 

Am I going about it the wrong way since its ntfs?

Do I need to follow the other walkthrough?

---

### Post by PsychedelicWonders on 2008-08-31
bump

---

### Post by Taxman415a on 2008-08-31
Well the basics are ```
sudo fdisk -l
``` to find out what partitions you have then follow the mount command as in the first link such as ```
 sudo mount /dev/sdb1 /media/sdb1
``` but change the partition number to the one appropriate for you. You can add all the fancy options to the mount command as well, but it's likely it will autodetect the filesystem for you and set reasonable options. Then follow the fstab guide for how to add that to your fstab file so it mounts automatically for you.

---

### Post by PsychedelicWonders on 2008-08-31
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS


Alright there is the hdd right there after running the 1st code.

Now if I want to rename it to whatever I want... do I do this when I mount it?

sudo mount /dev/sdb1 /Psychedelic Wonders/sdb1

Is that how I write the code if I want to give my 2nd hdd the name of Psychedelic Wonders?

---

### Post by Taxman415a on 2008-08-31
In the mount command the basics are mount <device> <mountpoint> and the mountpoint is just an empty directory normally. So you can create whatever directory you want with ```
sudo mkdir /Psychedelic\ Wonders
``` or similar and use the above to mount it there. If you don't create the mountpoint first, you'll get an error saying it doesn't exist when you try to mount something there. To keep it consistent with other mountpoints that are under /media, you may want to create it as /media/Psychedelic Wonders though the space in the directory name can still screw up some things, so it's better without it. To use the space on the command line you sometimes have to use backslashes like I did above. As for giving the 2nd hardrive that name, I'm not sure what you mean by that. The drive won't show up named that anywhere, but the files on that drive will be listed under wherever you create the mountpoint and mount the drive.

---

### Post by PsychedelicWonders on 2008-08-31
> **Taxman415a said:**
> In the mount command the basics are mount <device> <mountpoint> and the mountpoint is just an empty directory normally. So you can create whatever directory you want with ```
sudo mkdir /Psychedelic\ Wonders
``` or similar and use the above to mount it there. If you don't create the mountpoint first, you'll get an error saying it doesn't exist when you try to mount something there. To keep it consistent with other mountpoints that are under /media, you may want to create it as /media/Psychedelic Wonders though the space in the directory name can still screw up some things, so it's better without it. To use the space on the command line you sometimes have to use backslashes like I did above. As for giving the 2nd hardrive that name, I'm not sure what you mean by that. The drive won't show up named that anywhere, but the files on that drive will be listed under wherever you create the mountpoint and mount the drive.

hmm.  I'm not sure exactly what all of this means.

Let me see if I can re-iderate it.

So I need to mount the drive with the following code:

sudo mount /dev/sdb1 /media/sdb1

Now when I say rename the hdd this is what I mean:

You know in windows you have C:, D: etc and you can right click and easily rename them to whatever you want?

So when you have a shortcut on the desktop and when you look it up in my computer it will be called Psychedelic Wonders instead of C: or D:

Am I making sense?

So after I run the code above to mount it, what do I need to type exactly to make the icon on my desktop and the icon under the home folder to read Psychedelic Wonders instead of how it currently is which is 500.1g?

---

### Post by Taxman415a on 2008-08-31
I'm not sure you can do that. There is a bug in the easy way of doing it [https://bugs.launchpad.net/ubuntu/+bug/231265](https://bugs.launchpad.net/ubuntu/+bug/231265) and the workaround that someone pointed to [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) didn't really do anything when I tried it. I didn't test rebooting or anything though.

---

### Post by PsychedelicWonders on 2008-09-01
You really cant rename a hdd like in windows?

Seems so easy?

---

### Post by Taxman415a on 2008-09-01
Well it's open source, so you always can do it. It's just a question of how easy. And as mentioned, there seems to be a bug in the easy way.

---

### Post by Taxman415a on 2008-09-02
> **Taxman415a said:**
> There is a bug in the easy way of doing it [https://bugs.launchpad.net/ubuntu/+bug/231265](https://bugs.launchpad.net/ubuntu/+bug/231265) and the workaround that someone pointed to [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) didn't really do anything when I tried it. I didn't test rebooting or anything though.

Ok, if you're still watching, after following the steps in that workaround, and rebooting, the partition was renamed in places, on the desktop, etc. So if you want to follow that, you can rename to whatever you want. You may find some new bugs if you have a space in the name though, so not using one would be better.

---

### Post by PsychedelicWonders on 2008-09-02
I need to mount this first correct?

So use the following to mount for now?...

sudo mount /dev/sdb1 /media/sdb1

then run those two walkthrus?

---

### Post by Taxman415a on 2008-09-03
Yes, that will mount it for now, then [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) shows you how to change the partition label. Basically it goes like this:

1. sudo umount /dev/sdb1    (if it was mounted)
2. sudo fdisk -l    to identify the partitions (you've already done this I think
3. sudo aptitude install ntfsprogs
4. sudo ntfslabel /dev/sdb1 whateverlabelyouwanthere

Then you need to set it up in /etc/fstab if you want it to automount, and you may have to do this to get the name to be recognized.

Look at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Create the mountpoint for the partition label you created with say 

sudo mkdir /media/PsychedelicWonders

then change the /dev/sdb1 line in fstab to (or add) something like this:
/dev/sdb1 /media/PsychedelicWonders     ntfs    defaults 0 0

---

### Post by PsychedelicWonders on 2008-09-03
Alright so I need to mount it and then unmount it?

is the following code correct...?

1. sudo **umount** /dev/sdb1 (if it was mounted)

or should it be unmount?

just wanted to make sure.

---

### Post by Taxman415a on 2008-09-04
No you don't need to mount it first. You need to run the ntfslabel command with the partition unmounted, so no need to mount it. I had just said how you could do it manually. And it is umount for some strange reason, and you can always check that type of thing on the command line by trying to read the manpage. ```
man umount
``` would have told you the that was the right command and trying unmount would show that doesn't exist. Manpages are pretty helpful even if you don't understand everything they say.

---

### Post by PsychedelicWonders on 2008-09-06
> 3. sudo aptitude install ntfsprogs
4. sudo ntfslabel /dev/sdb1 whateverlabelyouwanthere

Then you need to set it up in /etc/fstab if you want it to automount, and you may have to do this to get the name to be recognized.

Look at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Create the mountpoint for the partition label you created with say 

sudo mkdir /media/PsychedelicWonders

then change the /dev/sdb1 line in fstab to (or add) something like this:
/dev/sdb1 /media/PsychedelicWonders     ntfs    defaults 0 0

Alright I just ran the ntfsprogs

Now I need to run the following in the terminal:

sudo ntfslabel /dev/sdb1 PsychedelicWonders

Just like that?

I am going to read that walkthru right now thanks...

---

### Post by PsychedelicWonders on 2008-09-07
alright at this point, i need to mount my hdd so I can transfer all data to it so I can access it underwindows to transfer files to my blackberry.

This is what I've done... what am I doing wrong?

psychedelicwonders@JohnnyScience:~$ sudo mount /dev/sdb1 /media/sdb1
[sudo] password for psychedelicwonders: 
fuse: failed to access mountpoint /media/sdb1: No such file or directory
psychedelicwonders@JohnnyScience:~$

---

### Post by PsychedelicWonders on 2008-09-07
alright, I found my old thread and seemed to have mounted properly because it has given me a 500.1gb icon on my desktop and now allowing me to transfer files to this hdd.

So other than renaming it, I guess I'm all set.

Now I just need to go about that situation, so getting back to my last problem with trying to do so...

now that it is mounted, if I unmount it to name it, it wont affect my data at all will it?

what code do I use to unmount so I can edit the name?

Alright I just ran the ntfsprogs

Now I need to run the following in the terminal:

sudo ntfslabel /dev/sdb1 PsychedelicWonders

Just like that?

---

### Post by PsychedelicWonders on 2008-09-07
cool thing, what I renamed this hdd in windows, carried over to Ubuntu.

Its just that easy.

---

