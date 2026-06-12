---
title: "trash corrupted in hardy"
date: 2008-11-11
forum: General Help
---

### Post by zvilikestv on 2008-11-11
I moved some files to Trash and then opened Trash so I could empty it.

All of the files and folders except 1 have meaningless file names (punctuation/numberstrings, with the occasional letter), the dates for them are 90% not in this year (either future or pre-computing), and most of them don't have a filetype when I have a list view (some show up as mp3s.)

When I try to empty the trash, I get a progress bar which shows no progress being made and I eventually cancel the operation as useless.

Any suggestions?

---

### Post by LoneWolfJack on 2008-11-11
on the shell, type

```
gksu nautilus ~/.Trash
```

this will open nautilus as root and should allow you to delete the files.

---

### Post by zvilikestv on 2008-11-11
I don't have a .Trash or a .trash directory in my home folder. I exposed hidden files, and the only hidden directory I don't recognize as belonging to a program is .fr-pCsqXM , which contains one MP3 file I thought I deleted a while ago, but nothing else.

I attempted to move that directory to Trash (as root). It is now gone from my normal user home folder, but I cannot open root Trash and finally delete it either.

---

### Post by sisco311 on 2008-11-11
the trash in hardy is in ~/.local/share/Trash/
```
gksu nautilus ~/.local/share/Trash/
```

---

### Post by zvilikestv on 2008-11-11
When I opened ~/.local/share/Trash there was no empty trash button. I moved to trash the files I found there. [I don't have a 'delete' option when I right click in nautilus. And hitting the delete button only has the effect of moving to trash.] 

I opened /root/.local/share/Trash and and did not have an empty trash button. I tried moving the files to Trash, but they ended up in the same folder, or in a subfolder of the same folder.

I then tried to cd to the directory, but permission was denied. I tried to sudo cd and gksudo cd into the directory, but the shell said that directory cd was not recognized.

I'm really at a loss.

---

### Post by -Zeus- on 2008-11-11
press shift+del to immediately delete.  As far as completely emptying them, this should do it:
```
sudo rm -rf ~/.local/share/Trash/* ~root/.local/share/Trash/*
```

---

### Post by hansdown on 2008-11-11
Hi zvilikestv.

I recently had a similar experience with the delete trash.

I loaded up a 2gig thumbdrive with "stuff" for a buddy, and my buddy loaded it onto a ps3. My buddy asked if I could delete it, as I had more "stuff" to put on it. I said sure, that's easy, but when I moved it to trash, and tried to delete the 2gig, I got the same bar that makes you think it's going to do something. 
Dum da de de Dum da de de...Perhaps it's time for a cool, refreshing beverage.... One hour later, it's still not filling the progress bar.
It may be a bug, but without an error message, I'm not sure what to do.
I will try the suggestions from our members, but I'm not sure where to go from there.

---

### Post by sisco311 on 2008-11-11
also try to check the file system for errors:

open a terminal and type:
```
sudo touch /forcefsck
```

if you have a separate /home partition:
```
sudo touch /home/forcefsck
```


then reboot to perform the check:
```
sudo reboot
```

---

