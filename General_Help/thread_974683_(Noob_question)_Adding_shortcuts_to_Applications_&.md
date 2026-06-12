---
title: "(Noob question) Adding shortcuts to Applications &gt; Games"
date: 2008-11-07
forum: General Help
---

### Post by Selphy on 2008-11-07
Hi!
I've been playing around with Xubuntu and I recently got Hexen 2 to run. I want to add a shortcut to the launcher to my Applications> Games but I can't seem to quiet figure out how to do it. After looking some recommended right clicking on applications and doing edit but that appears to only add it within the menu drop down and not under Games. Can anyone give me a hand on how to go about doing this. I appreciate it!

---

### Post by drs305 on 2008-11-07
I booted up xubuntu and initially it didn't act like ubuntu's menu system. However, if you install 'alacarte' you can add items to your games menu.
```
sudo aptitude install alacarte
```

Run 'alacarte' in a terminal.
Highlight the 'Games' folder in the left column.
On the right side, select 'Add Item'.
Enter the name, run command, and add an icon if you wish.
If the program runs in terminal, in the 'Type', change to 'Run in Terminal'.

If you installed the package via apt/aptitude/dpkg/synaptic, there should be a file in the /usr/share/menu folder with the name of the program. Inside that file is the run command and the location of its icon. This information may be helpful in creating the launcher.

---

