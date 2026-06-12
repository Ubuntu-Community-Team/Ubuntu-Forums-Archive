---
title: "Hardy Heron Lock Dialog ~ help plz"
date: 2008-09-19
forum: General Help
---

### Post by Crayboff on 2008-09-19
Alright, I'm still a noob so bare with me.

I'm trying to install a new lock dialog, however I have no clue what I am doing wrong. I am following the instructions listed on these sites: [http://www.gnome-look.org/content/show.php/New+Wave+Lock-Dialog+Theme?content=87773](http://www.gnome-look.org/content/show.php/New+Wave+Lock-Dialog+Theme?content=87773) and [http://yabblog.com/2008/09/13/show-offs-2/](http://yabblog.com/2008/09/13/show-offs-2/) The latter of which is slightly more indepth.

This is exactly what I am doing: I go to gnome-look.org and find what I want. I then download it to my desktop. From there I run "gksudo nautilus"
to get to the usr/share/gnome-screensaver. I then click and drag the tar.gz file straight to usr/share/gnome-screensaver. Then I right-click "Extract Here". It comes up with one of the files and then I open "gconf-editor" and navigate to apps>gnome-screensaver. There I go to "Lock_dialog_theme" and change the Value from "default" to, in this case, "newwave". Then I close the Configuration Editor and click the lock button, however this is where it gets dumb. The screen saver starts and when I move the mouse I end up with the same old default lock dialog.:confused:

I have tried running ```
gconftool-2 -s - -type=string /apps/gnome-screensaver/lock_dialog_newwave
```, a variation from [http://ubuntu-tutorials.com/2007/09/22/ubuntu-human-gnome-screensaver-lock-dialog-theme/](http://ubuntu-tutorials.com/2007/09/22/ubuntu-human-gnome-screensaver-lock-dialog-theme/) and this does nothing.

Please help me, oh great wise Ubuntu veterans! :smile:

**Manufacturer:** Dell
**Model:** Inspiron 1521
**Processor:** AMD Turion 64 X2 Mobile Technology TL-58 1.90GHz
**Memory (RAM):** 1918MB
**System Type:** 32-bit Operating System
**Operating System:** Ubuntu 8.04.1 (Hardy Heron) & Windows Vista Home Premium


**Edit:** I tried changing to newwave via "gksudo gconf-editor" to change it in root, incase there were permission issues. However, this didn't work either.

---

### Post by russ2001 on 2008-09-30
I had the same problem.  I read a thread about problems with changing while running Compiz and one thread about bug in screensaver.glade.  I quite messing with it and after my screensaver locked up and had to hard reboot, it works.  Sorry no help.

---

### Post by KiDQUiCK on 2008-12-03
I did the exact same steps as Crayboff and had the exact same problem. After some tinkering i got it to go. Here's the deal:

There seems to be a difference between running *gconf-editor* and *Applications --> System Tools --> Configuration Editor*. Each has their own set of config values. Editing the system settings through *gconf-editor* did NOT work for me. Editing the settings through the *Configuration Editor* **worked**. I have no idea why. Maybe someone can enlighten us as to why this happens?...

To enable the Configuration Editor in the Applications menu:
Applications --> Add/Remove --> System Tools --> enable (check) Configuration Editor

Also, you have a typo in the command line code you were trying to execute... it should be:

```
gconftool-2 -s - -type=string /apps/gnome-screensaver/lock_dialog_theme newwave
```

Cheers

---

