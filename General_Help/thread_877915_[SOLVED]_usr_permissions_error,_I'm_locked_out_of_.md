---
title: "[SOLVED] /usr permissions error, I'm locked out of everything!"
date: 2008-08-02
forum: General Help
---

### Post by SphereCat1 on 2008-08-02
Hi everybody! I'm new to the whole command line, and I was trying to create a file in /usr/lib as a link to a library. I know the command for permissions, chmod, but I forgot to add the executable permission, so now all the programs in /usr are locked up, including sudo, and I haven't created a root account login for the command line. How can I change the permissions back???

Help! :(

---

### Post by dexter.deepak on 2008-08-02
can you please post the exact command?

---

### Post by SphereCat1 on 2008-08-02
I typed sudo chmod ugoa+=rw /usr. I forgot the one that lets you execute files from it, causing all applications to fail.

---

### Post by CatKiller on 2008-08-02
Chaging the permissions on everything, as you've noticed, is not really a great idea. What you were trying to achieve could have been done just by using **sudo** to create your link.

Since *chmod* is probably now as non-functional as *sudo*, you can't just boot into single-user (recovery) mode (which automatically makes you root without needing to use *sudo*) to fix it. I'd suggest that you boot up your Live CD, mount your hard drive, and fix your permissions from there.

---

### Post by mike2357 on 2008-08-03
The full path to chmod is /bin/chmod, so it's not in /usr.  Since that's the case, could you solve your problem by booting into single-user (recovery) mode and then using /bin/chmod ?

If so, the command to restore permissions of /usr would be

/bin/chmod 755 /usr

---

### Post by SphereCat1 on 2008-08-03
Thanks much, guys! I was trying to change the permissions so I could use the GUI to move the files more easily, I'll be adding that to my list of things not to do! :)

SphereCat1

---

### Post by CatKiller on 2008-08-03
> **SphereCat1 said:**
> Thanks much, guys! I was trying to change the permissions so I could use the GUI to move the files more easily, I'll be adding that to my list of things not to do! :)

It's generally best to use the minimum permissions that work. You can become root temporarily by using *sudo*, or *gksudo* for graphical applications. So, for example, if you wanted to open a file manager window as root, you could use ```
gksudo nautilus
```

There's more information [here]("https://wiki.ubuntu.com/RootSudo").

---

