---
title: "how to run applications at startup ???"
date: 2005-11-20
forum: General Help
---

### Post by igmox on 2005-11-20
hi, 

i am using knetstats, showing windows-like network activity in system tray. 
my question is how can i make it (and maybe some other applications) run automatically during startup ?
thanx...

---

### Post by `GooZ´ on 2005-11-20
Goto System -> Preferences -> Sessions and click the Start Programs tab
Just create a new one, and give in the command (probably 'knetstats')

---

### Post by igmox on 2005-11-20
thanx gooz but i think it was for gnome...how about kde ??

---

### Post by tabinin on 2005-11-20
If you put a link in ~/.kde/Autostart (right click, create new -> link to application), the linked app will run at startup.  KDE also remembers (some of) what was running at shudown, so if you get two instances on your next startup, that's the issue.

---

