---
title: "i think i really screwed up"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by ajlozier on 2009-01-25
i need help.

for reasons that really don't matter anymore, i wanted to attempt to upgrade from python2.5 to python3.  when upgrading seem to make no difference i thought i would uninstall python2.5.  in the synaptic package manager, i did a complete uninstall.  bad move.

within minutes the screen went black.  when i rebooted, i was taken to the command line.  i slowly began to realize the implications of what i had done.

so my question is - short of recovering all of my documents, etc and then doing a complete re-install of ubuntu, do i have any "better" options for restoring my desktop?  i'm reasonably comfortable with the command line.

thanks in advance!

Aaron

---

### Post by taurus on 2009-01-25
If you removed python2.5, you can try reinstalling it.

```
sudo apt-get update
sudo apt-get install python2.5
```

---

### Post by ajlozier on 2009-01-25
yep i did that.  the problem is a lot of stuff that depended on python got removed as well.  but, good news.  i ran apt-get install gnome and got back probably about 90% of what was lost.  was able to reboot back into the desktop.  from there what i've done is compare the "packages to be removed" list when i attempt the same action on an ubuntu virtual machine, with the packages i have installed, and i believe i have been able to recover most everything else.  i'm impressed with the resilience of ubuntu.  even though firefox had been uninstalled with the rest of it, after apt-get'ing gnome i was even able to restore my previous session!

---

### Post by taurus on 2009-01-25
```
sudo apt-get install ubuntu-desktop
```
Maybe it will recover 100%.

---

