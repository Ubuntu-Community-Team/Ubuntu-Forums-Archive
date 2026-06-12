---
title: "Got Locks"
date: 2008-08-03
forum: General Help
---

### Post by kf4tqj on 2008-08-03
I'm having trouble saving jpegs to a folder. All the folders have locks on them. Some will save to a sample folder I have, but I try to drag and drop to a folder under art/qsl and it won't go.
Got any suggestions? Just about the time I think I'm ready for Linux  totally, I hit a stumbling block.
Woody / KF4TQJ

---

### Post by tamoneya on 2008-08-03
this is a simple permissions/ownership problem.  If you can open up terminal and navigate to the directory that you are trying to work in the run this command:```
ls -l
```
Post the output here if you could.

---

### Post by kf4tqj on 2008-08-03
How do I navigate to home? home gets bash command not found and /home gets /home is a directory, as does /home ls -l
I'm getting lost.

---

### Post by tamoneya on 2008-08-03
what directory are you trying to get to.  I can tell you the commands.

---

### Post by kf4tqj on 2008-08-03
Thanks for the help. I went to terminal and did sudo nautilus and changed the permissions for the home directory. That seems to have fixed it for now.
Woody

---

### Post by tamoneya on 2008-08-03
you should always use gksudo nautilus.  Calling a graphical application with sudo can cause permissions errors.

---

