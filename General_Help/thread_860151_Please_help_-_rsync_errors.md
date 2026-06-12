---
title: "Please help - rsync errors"
date: 2008-07-15
forum: General Help
---

### Post by linuxted on 2008-07-15
I have used rsync as a backup mechanism for some time now.   Recently I've been getting errors that I cannot resolve.
Here is the command I run:
[COLOR="Navy"]
rsync -av --delete /source /destination[/COLOR]
Here are the messages:

***
[COLOR="Navy"]building file list ... rsync: readlink "/source/user1/.gvfs" failed: Permission denied (13)
done
IO error encountered -- skipping file deletion

rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9][/COLOR]
****

The symptom is any files that I delete in /source don't seem to get deleted in /destination.

When I do a "[COLOR="Navy"]ls /source/user1/.gvfs[/COLOR] " I get:
[COLOR="Navy"]ls: cannot access /source/user1/.gvfs: Permission denied[/COLOR]


I am stumped :confused:

Thank you for your help,
linuxted

---

### Post by rbmorse on 2008-07-15
Couple of things to check:

a). Who owns the folder ~/.gvfs ? Should be user.

b)  Is there by any chance both a folder and a regular file named .gvfs?

---

### Post by bilbrey on 2008-09-15
Add "--exclude /home/{username}/.gvfs" to your rsync command line and the errors will disappear. I found the hint in another thread here, when I encountered the same thing after upgrading to 64 bit Hardy Heron two weeks ago.

best,

.brian

---

### Post by rbmorse on 2008-09-15
Another thing you can do to make rsync happy is to set permissions of the .gvfs folder to allow "group" and "others" to have read and write permissions:

sudo chmod -R 0666 /home/*username/*.gvfs

you may need to use sudo because the .gvfs folder may have been created with root as the owner...that's what broke rsync for me.

---

