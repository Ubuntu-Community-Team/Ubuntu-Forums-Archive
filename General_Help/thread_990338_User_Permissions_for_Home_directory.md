---
title: "User Permissions for Home directory"
date: 2008-11-22
forum: General Help
---

### Post by jlook on 2008-11-22
I'm a newbie! oops!

Somehow I managed to set my home directory permissions to be shared by others ... now whenever I boot, I get a message saying that "User's $home/.dmrc file is being ignored ... file should be owned by user and ... not writable by other users"

Anyone know how I fix this?  It seems to be causing other miscellaneous problems for me too

Thanks!

---

### Post by geirha on 2008-11-22
Do you remember how you altered the permissions on ~ or ~/.dmrc?

Anyway, the following two commands in a terminal should set agreeable permissions. ```
chmod 755 ~
chmod 600 ~/.dmrc
```

---

### Post by drs305 on 2008-11-22
If geihra's solution doesn't seem to work, or if you just want more info on the error, I just wrote a tutorial about this:
[http://ubuntuforums.org/showthread.php?p=6161267]("http://ubuntuforums.org/showthread.php?p=6161267")

---

