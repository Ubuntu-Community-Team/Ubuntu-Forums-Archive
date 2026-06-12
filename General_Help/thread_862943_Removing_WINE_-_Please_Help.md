---
title: "Removing WINE - Please Help"
date: 2008-07-18
forum: General Help
---

### Post by mm23-justice on 2008-07-18
I can't seem to Completely Remove WINE off my computer.
I uninstalled it with Synaptic Package Manager and tried removing the .wine folder from my home folder but nothing worked....

I still have the bar on the Applications Menu...

Any Help Please. Thanks.

---

### Post by jimv on 2008-07-18
to get rid of the menus, type this command:

rm ~/.config/menus/applications-merged/wine*

---

### Post by kpkeerthi on 2008-07-18
To look for files/folder left over by wine, run these commands
```
sudo updatedb
```
```
locate wine
```
You may then manually delete the ones you don't need.

---

