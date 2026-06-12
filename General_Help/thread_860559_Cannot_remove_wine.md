---
title: "Cannot remove wine"
date: 2008-07-15
forum: General Help
---

### Post by paddy1 on 2008-07-15
I installed Wine on my computer to try to run some windows educational games for a little girl. Since the game wouldn't run, I removed wine through add/remove, then did a restart, only to find wine still there. Any suggestions for removal please?:confused:

---

### Post by Vivaldi Gloria on 2008-07-15
> **paddy1 said:**
> I installed Wine on my computer to try to run some windows educational games for a little girl. Since the game wouldn't run, I removed wine through add/remove, then did a restart, only to find wine still there. Any suggestions for removal please?:confused:

Try this. Start synaptic from the top panel:

sytem menu > admin. > synaptic

Search wine. Right click on it and choose complete removal.

---

### Post by chrisccoulson on 2008-07-15
It's likely that the Wine menu category is still stored in your personal preferences. Try doing the following in a terminal:
```
rm ~/.config/menus/applications-merged/wine-*
```

---

### Post by paddy1 on 2008-07-15
Tried to remove bthrough synaptic manager, and shows that it is not installed, and 0 to remove

---

### Post by paddy1 on 2008-07-15
I tried the code, (with Sudo)and it says no such file or directory

---

### Post by clinux on 2008-07-15
I don't know on edubuntu but on ubuntu to uninstall wine you'd do this.
System >preferences>main menu then enable the Wine item, then go to Applications > Wine> uninstall Wine software.

---

### Post by Vivaldi Gloria on 2008-07-15
> **paddy1 said:**
> Tried to remove bthrough synaptic manager, and shows that it is not installed, and 0 to remove

It seems that wine is uninstalled but didn't delete the menu items. Right click the menu (ubuntu symbol) and choose edit menus. Then uncheck wine.

---

### Post by paddy1 on 2008-07-15
Thank you. Problem solved.

---

