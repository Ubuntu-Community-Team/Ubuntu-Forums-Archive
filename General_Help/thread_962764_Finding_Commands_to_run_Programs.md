---
title: "Finding Commands to run Programs?"
date: 2008-10-29
forum: General Help
---

### Post by anotherdisciple on 2008-10-29
I usually find the command for a program the hard way. I will open the gnome menu and right click on the program... make a shortcut to the program... then I will edit the shortcut to see that the command for Firefox is "firefox", or the command for compizconfig-settings-manager is "ccsm".

Is there a simpler way to do this? Can I maybe type in a few keywords in a terminal command that prints out the shortcut command for that program?

I have had no problem doing this, but I ask because my step-dad is aggravated at how hard it is to make a shortcut for avant-window-navigator. He lost his Firefox shortcut on AWN and he couldn't figure out how to put it back on... because he didn't know the command for it. It would be nice to give him a way to figure it out instead of just telling him the answer.

---

### Post by drelyn86 on 2008-10-29
I usually just right click the main menu, go to edit menu, and open up the properties of the shortcut that's on the menu.

---

### Post by scragar on 2008-10-29
hmn, try:
```
cd /var/cache/apt/archives
dpkg -c `ls | grep **ktorrent**` | grep "\/usr\/bin\/" | grep -o "\/[^\/]*\$" | grep -o "[^\/]*\$"
```
which will show the information from the **ktorrent** package(it lists 2 lines like:
```
ktorrent
ktupnptest
```) provided ktorrent is installed and the deb installer is still in the cache.

---

