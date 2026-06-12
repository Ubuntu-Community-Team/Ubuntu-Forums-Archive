---
title: "[SOLVED] active backup script help"
date: 2008-09-01
forum: General Help
---

### Post by Stargazer989 on 2008-09-01
i know this is a bit sad, but could someone write a script that runs in the background and copy/pastes files from /home/* to /media/disk-1/BACKUP/* ?

(this is probably in the wrong section)

---

### Post by ~LoKe on 2008-09-01
How often?  But this sounds like a cronjob...

Are you trying to copy all files from the home folder?

---

### Post by -Zeus- on 2008-09-01
```
sudo rm -rf /media/disk-1/BACKUP/
sudo mkdir /media/disk-1/BACKUP/
sudo cp -r /home/* /media/disk-1/BACKUP &
```

This will remove the folder if it exists, recreate the folder (empty), then copy the files over.  The script will exit as soon as it starts the copy

---

### Post by ~LoKe on 2008-09-01
In a terminal, type...
> export EDITOR=gedit && crontab -e
Paste this:
```
* 03 * * * rm -rf /media/disk-1/BACKUP/* && cp -R /home/* /media/disk-1/BACKUP/
```
Save and exit.  This will remove all the files from BACKUP and then copy all the files from /home/ to BACKUP at 3AM every day.

---

### Post by Stargazer989 on 2008-09-01
hmm, i was hoping an always-active script of some sort... like it would actively scan and copy over new files/folders.

** EDIT: my computer isn't on 24hrs

---

### Post by ~LoKe on 2008-09-01
I'm no pro at this, but perhaps rsync could be what you want.

rsync -avzt /home/ClientUser /backup/destination

> * 03 * * * rsync -avzt /home/* /media/disk-1/BACKUP/

**EDIT**: Then when and how often do you want the script run?  You could have it every time the computer is booted, or when you log in, etc.

---

### Post by Stargazer989 on 2008-09-01
so i can't have it constantly active like Avast in windows scanning files..?
...and in this case copy/pasting them.

---

### Post by ~LoKe on 2008-09-01
> **Stargazer989 said:**
> so i can't have it constantly active like Avast in windows scanning files..?
...and in this case copy/pasting them.

That sounds...kind of pointless?  If you edit a file and screw it up, it would be backed up...

---

### Post by Stargazer989 on 2008-09-01
> **~LoKe said:**
> That sounds...kind of pointless?  If you edit a file and screw it up, it would be backed up...

never thought of that :P
so how could i automate this all into a launcher ?
maybe i should just use that Rsync one.

---

