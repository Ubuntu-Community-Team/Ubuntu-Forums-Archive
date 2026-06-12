---
title: "dkpg doesn't work"
date: 2008-08-27
forum: General Help
---

### Post by j55intelphil on 2008-08-27
When i try to apply updates that the update manager suggests, i get this error;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i tried running

sudo dpkg --configure -a

, and it asks me in configure acidbase using dbconfig-common. I say YES, and chose mysql as the type of datebase. when prompted, i give it the password. 

I then get the error

ERROR 2002 (HY000): Can't connect to local MySQL server through socket    &#9618; 
 &#9474; '/var/run/mysqld/mysqld.sock'

I think all this trouble is from when i unplugged my computer while it was in the middle of another update session. 

Now, Im stuck, cause i can't get any new updates, or install anything new. (like flash player)

Im kinda a linux newb if you havn't guessed, but am computer savy

can you help me?

---

### Post by iaculallad on 2008-08-27
Try relating to this previous [thread]("http://ubuntuforums.org/showthread.php?t=276470").

---

