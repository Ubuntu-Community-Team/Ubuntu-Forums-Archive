---
title: "Small Thunderbird Problem"
date: 2005-11-24
forum: General Help
---

### Post by Sebby on 2005-11-24
I have just imported my mail from Thunderbird in Windows to Thunderbird in Ubuntu. I simply copied all the folders from the Windows 'Local Folders' directory to /home/sebby/.mozilla-thunderbird/xxxxxxxx.default/Mail/Local Folders/. All my mail is there, but when I try to download new mail, I get the error "Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disk space to copy the mailbox." So clearly the permissions are wrongly set by copying straight from Windows. How can I rectify this?

Many thanks in anticipation. :)

---

### Post by aysiu on 2005-11-24
Try right-clicking on the folder and selecting Properties and Permissions. What shows up?

---

### Post by Sebby on 2005-11-24
[QUOTE=aysiu]Try right-clicking on the folder and selecting Properties and Permissions. What shows up?[/QUOTE]
I've got 2 folders: Local Folders and pop.dsl.pipex.com. Both say drwxr-xr-x 755.

---

### Post by aysiu on 2005-11-24
[QUOTE=Sebby]I've got 2 folders: Local Folders and pop.dsl.pipex.com. Both say drwxr-xr-x 755.[/QUOTE] 755 is good. Does that include all the folders and files inside of those, too? And who's the owner? You or root?

---

### Post by Sebby on 2005-11-24
[QUOTE=aysiu]755 is good. Does that include all the folders and files inside of those, too? And who's the owner? You or root?[/QUOTE]
Inside Local Folders is a different story. The files that I copied in are 555. I am the owner of all of the files.

---

### Post by aysiu on 2005-11-24
[QUOTE=Sebby]Inside Local Folders is a different story. The files that I copied in are 555. I am the owner of all of the files.[/QUOTE] Try typing this in the terminal (assuming your username is sebby): ```
cp /home/sebby/.mozilla-thunderbird /home/sebby/.mozilla-thunderbird_backup
chmod -R 755 /home/sebby/.mozilla-thunderbird
``` Any difference?

---

### Post by Sebby on 2005-11-24
[QUOTE=aysiu]Try typing this in the terminal (assuming your username is sebby): ```
cp /home/sebby/.mozilla-thunderbird /home/sebby/.mozilla-thunderbird_backup
chmod -R 755 /home/sebby/.mozilla-thunderbird
``` Any difference?[/QUOTE]
Yep that's sorted it. Many thanks. :D

---

