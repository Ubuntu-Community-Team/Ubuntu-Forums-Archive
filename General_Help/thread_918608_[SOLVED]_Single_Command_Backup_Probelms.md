---
title: "[SOLVED] Single Command Backup Probelms"
date: 2008-09-13
forum: General Help
---

### Post by c1rcu17 on 2008-09-13
I am trying to follow these directions here,
[http://siriusgeek.com/?p=5]("http://siriusgeek.com/?p=5")
to set up the one line backup to my USB external hard drive. I'm only using 4.1GB out of 750GB on the external drive, and 30GB out of 140GB used on the main drive. I'm just trying to backup my home folder every night to my usb drive. 

But when I start the backup command,
```
sudo tar -cvf /media/disk/backup.tar ~
```
it starts copying files and stop at,
```
/home/user/.VirtualBox/Temp XP.vdi
tar: /media/disk/backup.tar: Wrote only 4095 of 10240 bytes
tar: Error is not recoverable: exiting now
```
The file "Temp XP.vdi" is a pretty big virtual disk image. I don't know even where to look for help to this. Thanks guys.

---

### Post by Herman on 2008-09-13
:) Hello c1rcu17,
Nice link, thanks for sharing it. 
Looking down around the bottom of the web page you linked to, it says we can exclude dierctories from the backup by typing '--exclude=' after the command, and the file path to any directories we don't want included in the backup.
In your case you probably don't really need to include VirtualBox/Temp XP.vdi if it's a big file and it's causing problems. 

I hope I guessed right, but here is my try at making the command do that,
```
sudo tar -cvf /media/disk/backup.tar ~ --exclude=~/.VirtualBox/Temp XP.vdi
```Try that and see if it helps. 
Regards, Herman :)

---

### Post by c1rcu17 on 2008-09-13
Your solution works, but my problem is that I have many files and .iso's that are quite large. Is there a way to increase the file size limit so that I don't get this error?

---

### Post by Herman on 2008-09-14
I didn't know there was any file size limit.

:) Have you checked file ownership and permissions with the ls -l command?

---

