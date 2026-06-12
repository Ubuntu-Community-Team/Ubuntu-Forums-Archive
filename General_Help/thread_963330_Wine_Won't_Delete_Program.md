---
title: "Wine Won't Delete Program"
date: 2008-10-30
forum: General Help
---

### Post by cj_g0bl1n on 2008-10-30
I installed wine, just to play around with it.  I got my ventrilo server up and running, and for fun I figured I'd try out the windows version.  I got it working...and I like the linux version better.  So I tried to uninstall ventrilo through wine's uninstaller thingy, it will not uninstall the program, I even tried restarting.  I tried to manually delete the files from the folder...they come back...

Is there a way to delete them from the terminal?  I'd rather not have to logon as root, because its a server and I would have to drag out the cords to a monitor and other things, unless there is a way to logon from user mode!

Thanks!
goblin

---

### Post by Pettman on 2008-10-30
If ventriol is the only thing you've installed under wine on your user removing the directory .wine ([FONT="Courier New"]rm -r .wine[/FONT] in a terminal)should get rid of it (and everything else installed under wine). If you got other stuff under wine you want to keep it will be a bit harder. You'll have to first remove the files and then run wine's regedit clone to remove all references to ventrilo in the wine register (use the find function).
You never have to be root while doing something with stuff you've got installed under wine since the files are installed under your $HOME and therefore are owned by you.

---

### Post by cj_g0bl1n on 2008-10-30
I tried the rm -r .wine, but it didn't get rid of them.  So I uninstalled wine, hoping it would delete all of its files, but the files stayed there.  On the Applications menu there is a file called Wine, maybe I can delete it now.  However I cannot find where it located.  My .wine folder is now gone, yet I still have the folder in the Application bar.

EDIT:
I deleted all of the files finally, I uninstalled wine completely before that.  Weird, didn't think it would be this much of a hassle to uninstall something...

---

### Post by Pettman on 2008-10-30
Oh... you meant the entries in the menu? Those I usally remove by searching for wine or what ever the program uninstalled is called in my home-dir and deleting the apropriet files.

---

### Post by tubunu on 2008-10-30
On Applications right click Edit Menus and uncheck the items you no longer want in the Wine programs list.

---

