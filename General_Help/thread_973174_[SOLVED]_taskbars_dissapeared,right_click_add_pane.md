---
title: "[SOLVED] taskbars dissapeared,right click add panel option not there"
date: 2008-11-06
forum: General Help
---

### Post by simtaalo on 2008-11-06
i know it shouldnt make any difference to my system but i just tried the crunchbang live cd and when i exited out of that and rebooted into linux mint i am presented with no taskbar above or below.

ive tried the right-click and add panel but the only menu that comes up when i right-click is the "create folder, create launcher, create document, etc..."

ive tried to press create launcher but nothing happens.

alt+f2 doesnt bring up "run program" as it should do. the only way i can execute programs is using my keyboard shortcut to the terminal and typing the command in there.

ive also tried logging out and running a GNOME failsafe session which hasnt made any difference.

any ideas please?

---

### Post by geirha on 2008-11-06
Try running this in the console (Ctrl+Alt+F1) ```
DISPLAY=:0 gnome-panel &
```

---

### Post by simtaalo on 2008-11-06
it gave this output

```
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found

```

seems somehow its uninstalled itself, reinstalling now. 

thanks

EDIT: reinstalling and running that command bought it back. but it gives this error about the volume control

```
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

Do you want to delete this applet from your configuration
```

and this error for the deleted items bin

```
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet"
```

---

### Post by geirha on 2008-11-06
Install [apt://ubuntu-desktop](apt://ubuntu-desktop) to be certain that you don't also lack other gnome-packages.

This usually happens if you uninstall a package that ubuntu-desktop depends on.

---

### Post by Robertorps on 2008-11-10
Do you have to reinstall the whole desktop???

EDIT: Another question, how come this happened if I only removed the evolution (mail) packages and updated the OS?

---

### Post by MaxIBoy on 2008-11-10
I had the same problem.

Yes, you do. I had the same thing happen when I tried to get rid of Evolution. (Who knew an email client could be so important?) 

No big deal, really.

---

### Post by Robertorps on 2008-11-10
Is the link the same as sudo apt-get install gnome-desktop???


EDIT: After installing it, will I have two copies of gnome-desktop? If so, how can I get rid of the faulty one?

---

### Post by geirha on 2008-11-10
Clicking the [apt://ubuntu-desktop](apt://ubuntu-desktop) url is equvialent of doing **sudo apt-get install ubuntu-desktop**, yes. The ubuntu-desktop package is a virtual package that depends on all the needed gnome-packages to get the desktop the way it is after a fresh install. It will not reinstall all packages, just install the ones that have been uninstalled.

---

### Post by Robertorps on 2008-11-11
I did it and it solved the issue. Thanks a lot!!! :D

---

