---
title: "root directory (sda2) full"
date: 2008-08-21
forum: General Help
---

### Post by MeanStreak on 2008-08-21
Hi,

I seem to have run out of space on my sda2 / directory (see attached snapshot). I have a dual partition with Windows/Ubuntu. My Windows partition has free memory - can I use Gparted to resize the partition and allocate more space to Ubuntu? 

Another thing I don't understand - / is at 100% capacity according to this System Monitor, however /home is at 57% and 'home' is inside /. How can / be 100% full if it contains directories that are not full? Can someone explain the file structure here.

---

### Post by amo-ej1 on 2008-08-21
That's because home is a separate partition mounted somewhere in your / partition. The usage is reported on a partition basis.

(Everything is tied on / while in other operating systems the partitions are separate roots like c: and d: )

But since you have a 43 gigabyte / partition, how did it get that filled ? Do you perform cleanups like apt-get clean ?

---

### Post by qstraza on 2008-08-21
You can resize partitions with gparted, its preferable to use livecd, and not from repos, cuz u need to umount the partition before resizing, so just boot up the gparted live cd ;)

---

### Post by drs305 on 2008-08-21
If you delete a large file, you can check the space available and it won't have changed. The reason is that the available space does not include the contents of Trash folders. That space is essentially unavailable until the trash bin is emptied.

You can explore and delete the contents of root's Trash bin by opening a file browser with root privileges. Delete the entire Trash folder (including the 'files' and 'info' subfolders) and it will regenerate itself the next time something is deleted. Alternatively, you can go into Trash/files and individually remove files. If you do this, use SHFT-delete or the file will be deleted and returned to the same Trash/files folder!
```
gksu nautilus /root/.local/share/
```

To find all the mounted Trash folders on your system:
```
sudo find / -type d -iname *Trash* | grep Trash 
```

---

### Post by MeanStreak on 2008-08-23
> **amo-ej1 said:**
> That's because home is a separate partition mounted somewhere in your / partition. The usage is reported on a partition basis.

(Everything is tied on / while in other operating systems the partitions are separate roots like c: and d: )

But since you have a 43 gigabyte / partition, how did it get that filled ? Do you perform cleanups like apt-get clean ?

Thanks for the reply. I've never used apt-get clean, and in fact I wasn't aware there was such a thing. Of course, with my / root directory now full I cannot install it. 

A dialog box explaining "your root directory is nearly full, would you like to run apt-get clean" would be appropriate here surely.

---

### Post by MeanStreak on 2008-08-23
> **drs305 said:**
> If you delete a large file, you can check the space available and it won't have changed. The reason is that the available space does not include the contents of Trash folders. That space is essentially unavailable until the trash bin is emptied.

You can explore and delete the contents of root's Trash bin by opening a file browser with root privileges. Delete the entire Trash folder (including the 'files' and 'info' subfolders) and it will regenerate itself the next time something is deleted. Alternatively, you can go into Trash/files and individually remove files. If you do this, use SHFT-delete or the file will be deleted and returned to the same Trash/files folder!
```
gksu nautilus /root/.local/share/
```

To find all the mounted Trash folders on your system:
```
sudo find / -type d -iname *Trash* | grep Trash 
```

I empty the trash bin via the GUI (Right click on icon > Empty Garbage Bin). Are you describing another bin that exists on the root directory? How do I find this?

---

### Post by drs305 on 2008-08-24
> **MeanStreak said:**
> I empty the trash bin via the GUI (Right click on icon > Empty Garbage Bin). Are you describing another bin that exists on the root directory? How do I find this?

Yes, there is a trash bin in /root/.local/share/Trash that may contain trash that can be deleted to free up disk space. 

You can open up nautilus as root - Click on the Trash folder and look at the contents of the '*files*' folder. You can delete all of it by deleting the Trash folder. If you want to delete individual files, use Shift-Delete. 

```
gksudo nautilus /root/.local/share/
```

Because of posts like yours, I've just written a tutorial about the Trash bin. Sounds exciting, doesn't it ;-)  

The link is in my signature if you want to look at it.

---

