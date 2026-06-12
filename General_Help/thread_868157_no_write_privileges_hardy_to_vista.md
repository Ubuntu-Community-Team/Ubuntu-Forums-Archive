---
title: "no write privileges hardy to vista"
date: 2008-07-23
forum: General Help
---

### Post by derrick991 on 2008-07-23
I dual-boot Hardy and Vista Business. when i get into the Windows files from Hardy i don't have write privileges. how can i get around this?

---

### Post by estyles on 2008-07-23
Can you write to your Windows partition as root?  I.e. ```
sudo nautilus
``` then browse to your files, open them and save?

If so, you can use root privileges to give your user write access to the whole drive or to individual directories.  The easiest way I can think of would be to use sudo nautilus to browse to the windows drive, then select all of the folders, right-click->Properties, and modify the Permissions tab.  You can also use chmod, but I'm a little hazy on the exact syntax of that.

---

### Post by derrick991 on 2008-07-28
> **estyles said:**
> Can you write to your Windows partition as root?  I.e. ```
sudo nautilus
``` then browse to your files, open them and save?

If so, you can use root privileges to give your user write access to the whole drive or to individual directories.  The easiest way I can think of would be to use sudo nautilus to browse to the windows drive, then select all of the folders, right-click->Properties, and modify the Permissions tab.  You can also use chmod, but I'm a little hazy on the exact syntax of that.

thanks, this worked perfectly

---

### Post by dexter.deepak on 2008-07-28
a better (and permanent) solution would be to edit the /etc/fstab file and give read/write permissions to vista partition.
if you dont know how to do this...post this o/p:
```
sudo gedit /etc/fstab
```

---

### Post by estyles on 2008-07-28
> **dexter.deepak said:**
> a better (and permanent) solution would be to edit the /etc/fstab file and give read/write permissions to vista partition.


He's right.  That is a better way to do it.  Didn't realize it was possible until you posted that, dex.  I need to use that for my mounted drives, because chmodding the folder that the drive mounts to, while it may work, isn't as elegant a solution.  I know how to edit my fstab file, but how do you make the mounted drives r/w?  If it's simple and stated in the comments of the file, then I apologize - I'll check that when I get home, but I'm on Windows right now.

---

