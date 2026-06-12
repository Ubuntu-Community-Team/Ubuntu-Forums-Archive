---
title: "Hidden Trash in Home Directory?"
date: 2008-09-06
forum: General Help
---

### Post by klausner on 2008-09-06
While running a grep through all the files under my home directory, I got messages suggesting that there is a large accumulation of dead links, bad files, and/or invalid sockets. For example:

> 
grep: .adobe/Acrobat/8.0/Synchronizer/Commands: No such device or address
grep: .adobe/Acrobat/8.0/Synchronizer/Notification: No such device or address
grep: .amaya-check-instance: No such device or address
grep: .google/desktop/a2_sock: No such device or address
grep: .google/desktop/a1_sock: No such device or address
grep: .googleearth/instance-running-lock: No such file or directory
grep: .liferea_1.4/mozilla/liferea/lock: No such file or directory


Is there an easy way to prevent/clean this sort of thing up, or do I just need to build a script to search and destroy?

---

### Post by Shazaam on 2008-09-06
Hardy trash....
/home/username/local/share/trash/files
/root/local/share/trash/files

---

### Post by klausner on 2008-09-06
> **Shazaam said:**
> Hardy trash....
/home/username/local/share/trash/files
/root/local/share/trash/files

I don't understand. I don't have a /home/username/local tree.

---

### Post by Shazaam on 2008-09-06
/home/YOURusername/
You probably need to show hidden files. CTRL+H will do that.

---

### Post by klausner on 2008-09-06
> **Shazaam said:**
> /home/YOURusername/
You probably need to show hidden files. CTRL+H will do that.

I still don't get your point. I have lots of hidden files. But $HOME/local is neither a hidden file, nor does it exist at all.

---

### Post by Shazaam on 2008-09-06
Running Ubuntu Hardy, yours may differ but mine (default) is...
/home/shazaam/.local/share/trash/files.

---

### Post by drs305 on 2008-09-06
If you are interested in finding all your system's trash, take a look at the tutorial in my signature link. Note that it is only about files in various Trash bins and not about finding other files scattered around your machine.

---

### Post by Vivaldi Gloria on 2008-09-06
> **klausner said:**
> I still don't get your point. I have lots of hidden files. But $HOME/local is neither a hidden file, nor does it exist at all.

Shazaam is trying to tell that the trash bin is kept in ./.local/share/trash in your home folder (EDIT: He beat me to it). But I have no idea why he's telling this.

Back to your original question. I never had such a problem with a program installed from repos. If you're having such a dead link from a package in an ubuntu repo then file a bug report in ubuntu launchpad. More likely, it's a third party app you installed from somewhere else. Then this is completely their mistake and ubuntu cannot do anything about it. I suggest you install packages from the repos to get a clean and safe system. At least try to keep non-repo apps at minimum.

---

### Post by Shazaam on 2008-09-06
Sorry, misread your request klausner. Chalk it up to me being distracted by my wife :)

---

### Post by klausner on 2008-09-06
OK. The lack of a "." in ".local" confused me as to what he was talking about. But it's besides the point. I'm not having trouble with links in trash. See the examples cited. None are in trash.

---

