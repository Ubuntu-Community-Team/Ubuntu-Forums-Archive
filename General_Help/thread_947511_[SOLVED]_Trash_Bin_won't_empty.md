---
title: "[SOLVED] Trash Bin won't empty"
date: 2008-10-14
forum: General Help
---

### Post by postafflatus on 2008-10-14
I have a folder with 332.4 MB of MP3s, which originated from Windows native External Hard Drive (FAT32), it appears that I cannot delete it because of its permissions not allowing me to wipe it out. I tried to change permissions graphical way, but it just won't apply the settings - ''Operation not supported by backend'' and it won't ''CUT'' its way out of the Trash Bin either, only makes it self as a copy (of coarse then I am able to change the permissions and permanently delete the folder). So one copy is always being left out in Trash Bin of that damn folder and I have no idea why it won't let me to delete it, could anyone help me with this?

Regards, and thanks in advance

---

### Post by ddarsow on 2008-10-14
Enter in a terminal:

```
cd ~/.local/share/Trash/files/
sudo rm -rf ~/.local/share/Trash/files/*
```

This will delete all of the files in your trash.

---

### Post by drs305 on 2008-10-14
If you want to know more about finding and deleting root trash, here's a tutorial I made up a while back:
[Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

Section 7 deals with deleting trash created by 'root'.

---

### Post by postafflatus on 2008-10-14
chown: cannot access `/root/.local/share/Trash/*': No such file or directory

thats what happens when I am trying to delete the root trash with your directions, just doesn't happen :S

---

### Post by drs305 on 2008-10-14
> **postafflatus said:**
> chown: cannot access `/root/.local/share/Trash/*': No such file or directory

thats what happens when I am trying to delete the root trash with your directions, just doesn't happen :S

Try it without the *. If you still get nothing, that just means there IS no root trash at that location at this time.

If you run the following you should be able to find any trash folders on your system:
```
sudo find / -type d -iname *Trash* | grep Trash
```

In your case, I think you know where your trash files are. If you open nautilus with the following you should be able to navigate to them and delete any files there:
```
gksudo nautilus
```

---

### Post by postafflatus on 2008-10-14
Ive got:
/media/disk-1/.Trash-1000
/media/disk/.Trash-1000
/media/MY BOOK/.Trashes
/media/MY BOOK/.Trash-1000

so it means that I would need to empty those trash bins right? And what command would do it best? I think the folder which I am about to get rid of originated from /media/disk-1/.Trash-1000

---

### Post by drs305 on 2008-10-14
You could use a sudo command with 'rm' but I would advise you to use your file browser to look at the files and delete them that way.

You open nautilus with 'gksudo', which will give you the temporary power to delete files not owned by you. You would navigate to each folder and delete the 'files' and 'info' folders inside 'Trash'. ***In some cases it is necessary to hold down the SHIFT key so the deleted folders/files don't reappear in the same Trash bin.***

As a shortcut, you can put the address in the open command to go directly to the folder. I will use the first one you listed:
```
gksudo nautilus /media/disk-1/.Trash-1000
```

You only have to use sudo or gksudo to remove 'root' trash that ended up in your trash bins. You don't need it to delete your normal trash files, which should be possible by simply right clicking on the Trash icon on your Desktop or in your browser and selecting 'Empty Trash'.

---

### Post by postafflatus on 2008-10-14
YAY! Thanks! That helped! Now I see why you have been thanked so many times ^^

---

