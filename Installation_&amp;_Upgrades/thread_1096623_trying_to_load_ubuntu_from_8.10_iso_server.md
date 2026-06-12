---
title: "trying to load ubuntu from 8.10 iso server"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Len Tyree on 2009-03-15
having trouble loading ubuntu 8.10 from downloaded 8.10 iso server.  had it up a few days ago, but gnome was apparently updated with new screen which was not very likable (looked like a kiddie screen) So, started over with same down loaded cd.

reload will go through the motions, says to unload cd for restart, BUT when restarts, goes to terminal type signin, after signin gives terminal type line as 'len@len -$'.  regardless of what i enter here (except sudo reboot) does not get me to the gnome screen??  the reboot just gives me the same thing, telling me it is saving data for the reboot, going down, coming up, then gores to the terminal line signin again??  

any help would be appreciated.  thanks, len tyree.

---

### Post by Len Tyree on 2009-03-24
SOLVED...with new copy of ubuntu 8.10 from sjipit.
thanks for any help

---

### Post by albandy on 2009-03-24
Server don't install X by default, as you should know a server don't need graphical environment to work.
It's completely unecessary a graphical interface to use php, apache, mysql, ssh, .....

also if you need it you can install the desktop environment by installing the ubuntu-desktop package
sudo apt-get install ubuntu-desktop

---

