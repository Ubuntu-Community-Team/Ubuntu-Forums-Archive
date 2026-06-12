---
title: "How Do I Change Permissions So I Can Write on a New HD?"
date: 2009-12-03
forum: Hardware
---

### Post by mulluysavage on 2009-12-03
I'm following the InstallingaNewHardDrive How-to, and I'm soooo close. I've got it mounted, and can see the drive and get properties at /media/mydrive. I just can't create a new folder at all. I can see that the owner is root(root). When I open a terminal and run

sudo chown -R user /media/mydrive

it returns 

"Operation not permitted"

what to do?

---

### Post by Anonymousable on 2009-12-03
```
sudo -i
cd /media/mydrive
mkdir folder
chown -R user:user folder
```
You should then be able to create files in folder. Just replace folder with a preferred name ;)

---

### Post by mulluysavage on 2009-12-07
The Chown command returned "Operation not permitted."

---

### Post by Dennis N on 2009-12-08
> **mulluysavage said:**
> I'm following the InstallingaNewHardDrive How-to, and I'm soooo close. I've got it mounted, and can see the drive and get properties at /media/mydrive. I just can't create a new folder at all. I can see that the owner is root(root)...

Is it formatted in ext3/ext4? The method described here (in post #4) has worked for me:

[http://ubuntuforums.org/showthread.php?t=1329975](http://ubuntuforums.org/showthread.php?t=1329975)

---

