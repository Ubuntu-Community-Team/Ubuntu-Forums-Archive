---
title: "Can't execute own file!"
date: 2008-07-22
forum: General Help
---

### Post by TuckLive on 2008-07-22
I have a user on my server that can't execute files that are under his home directory.  The file permissions are even set to 755.  I also set the files ownership and group to the user. The file is executable, but only to root.  How can I make the file executable for my user?

---

### Post by scragar on 2008-07-22
```
chmod u+x **file**
```

although by the sounds of it the file is already executable, I'd check how it's being run, may be that the file calls for something else that only root has access to.

---

### Post by TuckLive on 2008-07-22
It is already executable.  For some reason this user can't execute anything anywhere

---

### Post by TuckLive on 2008-07-22
Found the problem.  Had to add the following lines

groupadd user 
usermod -g user user 
chown root.user ~user/bin/user 
chmod 4750 ~user/bin/user

---

