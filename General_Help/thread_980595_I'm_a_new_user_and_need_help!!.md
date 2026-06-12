---
title: "I'm a new user and need help!!"
date: 2008-11-13
forum: General Help
---

### Post by sparkythewondersquid on 2008-11-13
I just started using linux for the first time and am enjoying it vary much I have a problem and need help I am running ubuntu 8.10 and as I was playing with it on screen resolution my cat hit my arm and I hit a setting (I don't know which one) and now the screen is zoomed and I cannot get it back to normal there has to be a way to do it I don't know much about ubuntu so I don't know how to get the screen resolution back to something I can use please help

---

### Post by SuperSonic4 on 2008-11-13
Have you installed the propietory graphics card driver via hardware (looks like a chip)? That solves my problems. Look in your xorg.conf under monitor for a screen resolution and (as root) change it to your resolution and restart X (but be sure to backup xorg.conf)

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by tvtech on 2008-11-13
if you can get to a terminal type gksu gnome-display-properties

this will give you your screen resolution dialog, you should be able to change it from there. 

if you can't get to a terminal but can get to System>Preferences the program to change resolution is in there.

---

### Post by eternalnewbee on 2008-11-13
> 
Have you installed the propietory graphics card driver via hardware (looks like a chip)? That solves my problems. Look in your xorg.conf under monitor for a screen resolution and (as root) change it to your resolution and restart X (but be sure to backup xorg.conf)

Code:

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak


You could also try a reboot and see if that solves it.):P
Btw. Welcome to the Ubuntu Forums.;)

---

### Post by sparkythewondersquid on 2008-11-13
I cannot get to anything except the sound icon and user name I switched left to right on the "top bar" and cannot get to my menu at all when the cat hit my arm the selection was clicked fron the screen resolution so basically I can only see the upper left corner of the desk top w/ no menu options. I cannot get to a terminal or anything

---

### Post by blackened on 2008-11-13
alt+F2, then type gnome-display-properties and set your resolution back to normal.

---

### Post by cariboo on 2008-11-13
If you can't do anything else press Ctrl-Alt-F1 and at the prompt type:

```
sudo reboot
```

Jim

---

### Post by sparkythewondersquid on 2008-11-13
thank you for all the help :) I still cannot get it back being new to this perhaps I need more detail on what to do:confused: please help if anyone can I wish I could send a screen shot but it is on a differant computer

---

### Post by sparkythewondersquid on 2008-11-13
I guess no one has had this problem I guess this would make me a new and former user thank you though I read every book in the store and can find nothing on this

---

### Post by blackened on 2008-11-14
Ok, can you right click on the desktop? If so, then click "Create Launcher". In the dialog that comes up, give it a name, then gnome-terminal in the "command" box. Press enter. That should give you a desktop icon for the terminal. Let me know if this works and we'll use the terminal to fix your screen resolution.

---

