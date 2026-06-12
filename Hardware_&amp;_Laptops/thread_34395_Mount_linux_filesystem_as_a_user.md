---
title: "Mount linux filesystem as a user"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by kingzasz on 2005-05-14
I recently installed kubuntu, and I love it.  I kept my old Mandrake distrobution just in case on another partition though. 

I would like to get at the files on the other linux partition.  I can get at some files, but the rest are locked because I guess only the user can view them.  How can I mount this partition so that no files are locked?  Is there anyway to mount it as my old user with my old password?

Thanks!

---

### Post by Xian on 2005-05-14
It would be much easier to just access those files from Ubuntu w/admin rights.
Open a terminal and input this:

$ sudo nautilus

Then just navigate to the mounted partition you desire and go from there....

---

### Post by kingzasz on 2005-05-15
I don't want to always use admin to normally view files.  I need a long term solution.

---

### Post by ludi on 2005-05-15
[QUOTE=kingzasz]I don't want to always use admin to normally view files.  I need a long term solution.[/QUOTE]
You should change your system setting to do it without any prompts for pass.
Change the sudoers file.
See this thread to details:
[http://www.ubuntuforums.org/showthread.php?t=34229&highlight=sudoers](http://www.ubuntuforums.org/showthread.php?t=34229&highlight=sudoers)

---

### Post by kingzasz on 2005-05-15
[QUOTE=ludi]You should change your system setting to do it without any prompts for pass.
Change the sudoers file.
See this thread to details:
[http://www.ubuntuforums.org/showthread.php?t=34229&highlight=sudoers](http://www.ubuntuforums.org/showthread.php?t=34229&highlight=sudoers)[/QUOTE]
 Is there anyway adding my user to the owner of the files?

---

### Post by ludi on 2005-05-16
[QUOTE=kingzasz]Is there anyway adding my user to the owner of the files?[/QUOTE]
 " Is there anyway adding my user to the owner of the files?"
Well, you have to mount your partition first, right? So you will authorize that user to do it and you won't need to get root permissions. After, you can change the permissions of files...

---

### Post by boilertech on 2005-05-16
I have 2 hard drives with Mandrake on one hdb and Ubuntu one the other hda. I tried to navigate to hdb with nautilis but the drive is not listed.

---

### Post by ludi on 2005-05-17
[QUOTE=boilertech]I have 2 hard drives with Mandrake on one hdb and Ubuntu one the other hda. I tried to navigate to hdb with nautilis but the drive is not listed.[/QUOTE]
Propably because you didn't defined a mount point during the installation.
Whatever, to mount it:
user:~$ sudo (if you didn't authorized yourself to do it without the system privileges) mount dev/hdX /folder/tomount/.
Then, with the sudo privileges, change the files proprieties to match your desire.
This can be done by console's commands too.
Eg: 
> user:~$ cd /folder/XYZ
ls -l
drwxr-xr-x   2 ludi ludi    416 2005-05-15 17:49 Desktop
drwxr-xr-x   4 ludi ludi    160 2005-04-19 18:27 Documento
drwxr-xr-x  22 ludi ludi   3048 2005-05-16 15:31 Download
drwxr-xr-x  11 ludi ludi    352 2005-05-11 17:51 Música
user:~$ chown myuser:mygroup Desktop
user:~$ chmod 640 Desktop 
You may use the option -R or --recursive optionally.

---

### Post by boilertech on 2005-05-17
this is the message i get.
> mike@ubuntu:~$ sudo mount /dev/hdb
 mount: can't find /dev/hdb in /etc/fstab or /etc/mtab 
mike@ubuntu:~$   

hdb is listed in /dev folder.
I did try to edit fstab but it would not save even though i gave write permission to others.

Is there a way to log in with root to make these changes in permissions?

---

### Post by ludi on 2005-05-17
[QUOTE=boilertech]this is the message i get.
 

hdb is listed in /dev folder.
I did try to edit fstab but it would not save even though i gave write permission to others.

Is there a way to log in with root to make these changes in permissions?[/QUOTE]
 I don't know how could I help you now.
Please, post another thread titled "Error when trying to mount second HD".
May be you have to use LVM stuffs but it's unknown for me.

---

### Post by boilertech on 2005-05-18
Thanks for the help. I do appreciate it.

---

