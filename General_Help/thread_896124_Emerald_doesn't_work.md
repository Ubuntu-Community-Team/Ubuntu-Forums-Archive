---
title: "Emerald doesn't work"
date: 2008-08-20
forum: General Help
---

### Post by david sousa on 2008-08-20
Hey!

I have compiz working at 100% and have emerald instaled too.

When i run the command "emerald --replace" to change to the theme that i have installed at emerald manager, i have it working. But after closing all the windows and load them again, the windows borders just disapear.

Does someone have a clue?

---

### Post by Unanimated on 2008-08-20
Go to Add/Remove, and type in Compiz Fusion, then install Compiz Fusion Icon. It will install under Applications-->System Tools. When you open it, be sure to right-click the icon, scroll down to Select Window Decorator, then choose Emerald. Then you can use Emerald Theme Manager to install and use your themes. If you don't want Emerald as the theme manager again, change the window decorator to GTK. Then, you might either have to logout and log back in or reboot your computer.

---

### Post by mb_webguy on 2008-08-20
If you haven't already, install the compizconfig-settings-manager package, then go to System->Preferences->Advanced Desktop Effects Settings.  Go to Window Decoration, and for the "command" line type "/usr/bin/emerald --replace".

Hit Ctrl-Alt-Backspace to restart X, and Compiz will use Emerald as the default window decorator.

---

### Post by david sousa on 2008-08-21
Thanks both!

mb_webguy thank you for that! That solved the problem! ;)

---

### Post by Septi on 2011-05-11
Emerald gives me a segmentation fault :(

---

### Post by WorMzy on 2011-05-11
How did you install it?

Try purging it:
```
sudo apt-get purge emerald
```
then remove apt's cached packages:
```
sudo apt-get clear
```
then update your package information
```
sudo apt-get update
```
then finally install it again:
```
sudo apt-get install emerald
```

---

