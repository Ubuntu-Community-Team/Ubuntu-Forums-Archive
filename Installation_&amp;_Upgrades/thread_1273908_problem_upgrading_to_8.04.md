---
title: "problem upgrading to 8.04"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by themidget on 2009-09-23
i am having some issues upgrading to 8.04   i have 16 broken packages, 15 of which are openoffice, and the last is python. when i try to fix them in synaptic i get this error...

E: /var/cache/apt/archives/openoffice.org-java-common_1%3a2.4.0-3ubuntu6_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/java/openoffice/table.jar')
E: /var/cache/apt/archives/openoffice.org-writer_1%3a2.4.0-3ubuntu6_i386.deb: conflicting packages - not installing openoffice.org-writer
E: /var/cache/apt/archives/openoffice.org-common_1%3a2.4.0-3ubuntu6_all.deb: conflicting packages - not installing openoffice.org-common
E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.0-3ubuntu6_i386.deb: conflicting packages - not installing openoffice.org-core

also i don't seem to have any javascript, and on trying to install adobe i get " your system has broken dependencies" ??????

---

### Post by akakingess on 2009-09-23
Here is a stab in the dark, but I remember (way back when, it's been a while), but I ran a "sudo shutdown -dpkg now" or something to that affect and it repaired the dependencies before shutting down and everything was repaired when it came back up, however, my issue was not as severe/numerous as yours is, but it may be worth a shot.

---

### Post by rreese6 on 2009-09-23
did you try (in terminal-console-etc)
```

sudo updatedb
sudo dpkg --configure -a 
```
??
you might also want to do this:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
```

just to be sure everything is good to go

---

