---
title: "Kubuntu Problem!"
date: 2008-11-19
forum: General Help
---

### Post by iampriteshdesai on 2008-11-19
How can I stop Kubuntu from auto-updating itself?
Also I hate the stupid wallet and dont want to enter my password every time.

---

### Post by dabl on 2008-11-19
I guess you could open KMenu > System > Adept Manager, and on the Sources tab un-check _all_ the software sources.  Or if that doesn't work for some reason, you could use Kate in super-user mode and edit the file /etc/apt/sources.list, and put a "#" in front of every line that doesn't have one there already, then save it.

I'm not sure about disabling kwallet, but I'm sure there's a way.  Go into KMenu > System Settings and there's surely a way to turn it off in there.

---

