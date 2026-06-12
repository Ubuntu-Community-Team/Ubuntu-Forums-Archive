---
title: "tried out kubuntu-desktop, dont like it, removable?"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by factotum218 on 2005-12-31
I gave kde a shot with installing the kubuntu-desktop meta-package. Turns out I dont like it so much. Just not a big fan of KDE I guess. Is there any way I can remove it and the packages that came with it or do I need to do into something like synaptic and hunt them all down individualy?


FIXED

---

### Post by tonym on 2005-12-31
If you had used aptitude to install kubuntu-desktop then the dependencies would also be removed,  but this doesn't apply with synaptic I understand.

Try removing kdelibs and kdebase packages.  Most others depend on these so should be flagged for removal.

---

### Post by Sutekh on 2005-12-31
Well you should check out this thread

[HowTo: Fully uninstall the kubuntu-desktop meta-package]("http://ubuntuforums.org/showthread.php?t=96048")

---

