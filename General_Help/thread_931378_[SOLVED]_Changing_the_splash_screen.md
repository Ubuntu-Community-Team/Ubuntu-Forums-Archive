---
title: "[SOLVED] Changing the splash screen"
date: 2008-09-27
forum: General Help
---

### Post by mwx10 on 2008-09-27
Recently I installed the kubuntu-desktop package on my ubuntu installation (installed with wubi). I decided I wanted to use my GNOME desktop again, so I changed the default desktop manager to GDM. I also set GNOME as the default session on the login screen.  However, when I boot the computer, I still have the Kubuntu splash screen. How can I change that back to the ubuntu splash screen.

---

### Post by momalle1 on 2008-09-27
[http://ubuntuforums.org/showthread.php?t=896993]("http://ubuntuforums.org/showthread.php?t=896993")

---

### Post by mwx10 on 2008-09-28
Alright, nobody here seemed to help me but I was able to fix it on my own. Here are the commands that I used, incase anyone else wants to try them.

```
sudo apt-get install startupmanager
sudo su
startupmanager
```

Then under the usplash theme, I selected ```
usplash-theme-ubuntu
```

Ok, I will mark this as resolved now.

---

