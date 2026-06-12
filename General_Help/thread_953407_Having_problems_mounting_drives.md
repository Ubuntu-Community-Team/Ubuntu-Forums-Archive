---
title: "Having problems mounting drives"
date: 2008-10-20
forum: General Help
---

### Post by ragnarokeve on 2008-10-20
I try and mount 2 of my harddrives (both are .ext3) to their folders in /media and everytime i try the computer says that I do not have the privilages to mount the drive. I am able to sudo mount but i should be able to mount the harddrive without needing to use the command line or sudo.

---

### Post by Afkpuz on 2008-10-20
sudo mount the drives, then, in another terminal, type this. 


```
sudo chown user:user /media/disk
```


replace "user" with your user name and "disk" with whatever drive you've mounted.

Then, you should be able to change permissions through nautilus.  So, right click on your mounted folder, click properties  and change permissions.  


I think that will work

---

