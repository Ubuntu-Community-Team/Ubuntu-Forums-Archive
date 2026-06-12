---
title: "[SOLVED] Command Line access to 2nd Hard Drive"
date: 2008-08-01
forum: General Help
---

### Post by bilijoe on 2008-08-01
My system (Ubuntu 8.04.1) runs entirely from a 250Gb SATA Hard Drive.  Recently, I re enabled the old 40Gb drive my 7.10 system had been on.  Everything works fine, the old drive shows up as "38.5GB Media" and I can access it just fine via the GUI.  However, I need command line access to it, to do some group renaming of files, before I can transfer them to the new drive, and take the old one out, for good.  How do I "cd" to the old drive? For that matter, how do I "cd" to my CD/DVD drives, so I can get command line access to those?

---

### Post by Ahadiel on 2008-08-01
Try looking in /media for access to your other drive. And if it's not there, see where it's mounted with df -h.

---

### Post by mc4man on 2008-08-01
What you might find handy is nautilus-open-terminal. Then you can browse to a directory, r. click -> open in terminal and it will open a terminal at that location. Search in synaptic or read here

[http://ubuntu-tutorials.com/2007/05/13/nautilus-open-terminal-terminal-quick-launch/](http://ubuntu-tutorials.com/2007/05/13/nautilus-open-terminal-terminal-quick-launch/)

---

