---
title: "Strange Bug - Home Folder List Pulling from Calendar?"
date: 2008-11-21
forum: General Help
---

### Post by Bob535 on 2008-11-21
I'm not even sure how to properly explain this bug, so I took a screen shot. It just started happening about a week ago, and I'm not sure why, I haven't been messing with settings recently.

If you have any ideas or need more information, just ask.

Ubuntu 8.10
Netbook remix installed

---

### Post by taurus on 2008-11-21
What does your Desktop look like?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by Bob535 on 2008-11-21
chris@AspireOne:~$ ls -la ~/Desktop
total 8
drwxr-xr-x  2 chris chris 4096 2008-11-13 10:48 .
drwxr-xr-x 68 chris chris 4096 2008-11-21 10:11 ..


I don't actually have anything on my desktop because I'm using netbook remix, the folder is completely empty when I open it in nautilus

 I ran that command for ~/Documents folder (the one that is messing up) and it returned properly all the files and folders in the directory.

---

### Post by Bob535 on 2008-11-24
bump for strangeness continuing

---

