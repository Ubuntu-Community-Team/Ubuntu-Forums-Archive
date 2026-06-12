---
title: "TIP: recovering from corrupt archive"
date: 2008-07-25
forum: General Help
---

### Post by dave37 on 2008-07-25
I am posting this in case it helps anyone else.  I recently had to do a reinstall to a bare machine that had become inaccesible and when I tried restoring my home directory archives created with, and using sbackup to my horror sbackup would not recognize the backups, and an attempt to extract the .tgz resulted in an EOF error, archive corrupted.  It wasn't sbackup or many other backup methods fault, it seems it's the compression of the archive.

So, if it happens to you, and you are unable to extract the archive (I tried for a day to no avail) here are some tips:
Create a user, any user, say test.  The test user is just to access the system and perform the repair.  Not a bad idea though in my mind to keep it just in case of need in the future.  Also create users for the users you wish to recover.  Delete the home directories of all but your test user

Log in to the test user and create a directory to put your corrupted archive in to.  Having done that navigate to the sbackup (in this case) archive, issue the following:
```
tar xvf filename.tgz
```

You may have to do this across several archives to piece together your data but it will create a directory inside the directory you issue the command from.  This will take some time.  If it halts with an error, you will have recovered the data to the point of the error.  Once you have pieced together your data, in this case my home directories, execute 
```
gksudo nautilus
```

**OR**

```
sudo dbus-launch nautilus
```
whichever works on your system, I had to use the latter for some reason. You can now pick out your data and put it in to one place (for example, folder named recovery) for the next step.

Once your data is assembled, again in the root version of Nautilus copy it over to the home directory (eg copy user Tom into the home directory of your working installation)  This may also take some time.

Once it is done copying, and many thanks to [http://ubuntuforums.org/showthread.php?t=866120&highlight=.dmrc+file]("http://ubuntuforums.org/showthread.php?t=866120&highlight=.dmrc+file") but I found one problem, that of group access which prevented logging in.

So now issue the following commands from terminal:
```

dave1@userpc:~$ sudo chmod 644 /home/username/.dmrc
dave1@userpc:~$ sudo chmod 755 /home/username
dave1@userpc:~$ sudo chown -R username /home/username
dave1@userpc:~$ sudo chgrp -R username /home/username

```

Where **username** is the name of the user home directory you are attempting to recover.  The first line restores the file permissions on .dmrc, needed to logon

The second line restores access to the user home to the user

The third line recursively changes ownership of the files in the directory to the user

The last line changes group association recursively to the user that you are recovering.

It is a bit of work but as I have struggled with this for a day now, and I now have virtually all of my data back by working over several archives and performing this process. I hope this helps if you find yourself in a similar situation.

---

### Post by tgyorgyi on 2008-08-14
> **dave37 said:**
> Delete the home directories of all but your test user.


Is it not dangerous to simply delete the existing home directory? What happens, if for whatever reason the process gets stuck half way through and I need to reboot? Recently I tried to move my home folder to a new partition, followed all the instructions, and ended up with a non-functioning OS (and the repair suggestions did not work either), so I am a bit now on the careful side...

---

### Post by dave37 on 2008-08-15
That is the reason for creating the Test user account.  As you are not messing with the Test user account at all you *should* be able to always log in using the Test account.  

This tip was meant more for someone who was trying to desperately recover data, not foolproof but it worked for me and I performed it 3 times to make sure, and it worked...for me, I was able to restore my home workstation and data almost completely on the first try, second and third went fine to a bare machine.  I even deleted my home directory (with root access--don't ask, I won't print the commands) while in an X-session, and was still able to login using user Test after a reboot.

I was able to again restore from a corrupt backup archive, in this case a .tgz which readers may have backed up to. 

For backups I now use the simple rsync command with the appropriate switches, and it works beautifully for backing up.  There is little chance of a corrupt archive because it doesn't archive but rather syncs the workstation with the remote back up file and can be set to work various switches to get it to do what you want, even use cron (or in my case, gnome-schedule)to check and sync files, folders or directories  And has a simple restore procedure that can be done in an X-session or terminal.

Thanks **tgyorgyi** and I hope someone else can comment on your concern.

---

