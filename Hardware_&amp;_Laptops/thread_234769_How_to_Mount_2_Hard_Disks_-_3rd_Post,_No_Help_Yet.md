---
title: "How to Mount 2 Hard Disks - 3rd Post, No Help Yet"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by joeinazyes on 2006-08-12
I have posted this same problem in BOTH Beginner Talk and 64-Bit Users.  Some well intentioned souls have responded in manners that had nothing to do with the issue and others directed me to the Thread below which got me PART of the way to what I want:

[www.ubuntuforums.org/showthread.php?t=230141](www.ubuntuforums.org/showthread.php?t=230141)

I just installed DD 6.06 64-bit version on my system, which contains two (2) 80GB hard disks. Both disks are fomatted with Ext3. The OS files are fine and run well on hda1. I followed the thread above and now the second drive (hdb1) mounts on startup and has an icon on the desktop.

However, I don't understand why I can't use the second drive (hdb1) normally and add folders and files as I do with an external USB FAT32 HD.  The menu item "Create Folder" is grayed out and I cannot add folders to the 2nd disk (hdb1).  One folder exists on the drive, labeled "lost+found".  I don't have permission to access it by double clicking.

I would like to add files and folders to the entire drive using windows in the same way that I do in my /home directory.  Is this possible without having to go into the shell?

---

### Post by futz on 2006-08-12
Probably you need to set the owner, group and permissions properly on your /media/hdb1 directory.

You don't wanna do it in a terminal? Well lets see... You'll have to start a terminal for one thing. Start one and type
```
gksudo nautilus
```
Now you have a Nautilus running in superuser (root) mode, so be careful what you do with it. 

Navigate to your /media/hdb1 (or wherever the 2nd drive's mount directory is) and right-click on hdb1. 

Select properties. Select the Permissions tab. Change file owner and group to your user name and set the permissions to 755 like in this pic:
[ATTACH]14183[/ATTACH]

That should do the trick.

Oh ya, now shut off that superuser Nautilus before you forget it's got root privileges and accidentally mess something up with it.

EDIT:
> I would like to add files and folders to the entire drive using windows in the same way that I do in my /home directory. Is this possible without having to go into the shell?
I misread your original message before posting the above info, but it's still valid. If you want to share a drive with both Linux and Windows, it should probably be FAT32. Both OS's read & write FAT32 just fine, I think.

---

### Post by seiferkai on 2006-08-12
hmm i have kinda the same problem except i never wanna go back to windows
the fact that my media/hdb1 permissions is set to 755 i cannot write or add anything in there....how can i change it to 777

the way you described didnt work for me all i get is this error message


The permissions could not be changed.
Couldn't change the permissions of "hdb1" because it is on a read-only disk

---

### Post by futz on 2006-08-12
> **seiferkai said:**
> The permissions could not be changed.
Couldn't change the permissions of "hdb1" because it is on a read-only disk
Is this a NTFS disk? If so, you will almost certainly have to back up any important files that are on it, repartition and reformat to something Linux is happier writing to.

I know some people are writing to NTFS disks in Linux, but it's not recommended. The drivers are not really 100% yet, they say.

---

### Post by seiferkai on 2006-08-12
i just recently reformatted this drive to linux...the only folder in there is the lost+found folder which i dont have permission to either

---

### Post by joeinazyes on 2006-08-12
Hey Futz,
Your directions were right on.  I'm able to do what I requested in the initial thread statement.  I'm not averse to using the shell, I used to work in DOS 6.11 all the time.  I just don't feel inspired right now with a busy life to learn a new set of shell commands.  It is on my list of things that I eventually want to enjoy doing.

Sincere Thanks Futz for your courteous help...

joeinazyes

---

