---
title: "nautilus doesn't start / ubuntu going crazy on me"
date: 2008-08-20
forum: General Help
---

### Post by Comandos on 2008-08-20
hey,
I don't really know how to describe my problem, but I think ubuntu has it for me. Recently, completely out of the blue, when i log into ubuntu my startup programs (skype and gaim for example) just won't start. Everything's slow, firefox doesn't remember my cookies, and when I try to manually shut down using the big shiny red button both of the menu bars disappear. I think nautilus doesn't start either because of what ubuntu calls "a serious error". Can someone please, please help me?

---

### Post by prince_niceguy on 2008-08-20
try logging in fail safe gnome. If the problem persist then rename your home directory to something else and then login again. if it has something to do with your settings then that would be rectified.

to rename your home dir, do the following, restart computer, select failsafe mode, drop to a root shell then issue the following commands

```
cd /home
mv [directoryname] [directoryname].old
```

---

