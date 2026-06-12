---
title: "Trying to empty trash, but wont delete some files and tells me access denied..."
date: 2008-08-17
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-17
Alright I am trying to empty my trash because it has about 10g worth of stuff I already have copied on my main drive.

For some reason, instead of "moving" files, it only seems to "copy" them.

Any way to change the default to move instead of copy?

Anyways, as I am trying to delete the last few folders out of my trash permanetally, it is giving me this error message....

---

### Post by Shazaam on 2008-08-17
Two places to check (as root so BE CAREFUL!)
Open terminal, type this in...
```
gksudo nautilus
```
Once nautilus opens go to View and check "Show Hidden Files".
1. Go to home>your user name>.local>share>Trash>Files and delete anything in there.
2. Go to root>.local>share>Trash>Files and do the same.
If you find it making copies instead of deleting, highlight the file(s) and click Shift+Delete.

---

### Post by PsychedelicWonders on 2008-08-17
was this tip to perm delete my trash bin?

Or was this to make the move/copy function different?

Why do I have to be careful when check the root file?

---

### Post by Shazaam on 2008-08-17
Just a way to empty the trash. :)
Since I don't know the posters skill level I usually put the warning in there so the user doesn't go wandering around the file system as root causing havok.

---

