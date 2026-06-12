---
title: "Error when updating!  Please help"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Fidju on 2008-12-19
hello, when i try to intall updates i get the following error:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


when i try to run 'sudo dpkg --configure -a'  i get this:


dpkg: parse error, in file `/var/lib/dpkg/updates/0075' near line 1:
 field name `eatured' must be followed by colon.


I dont know where to go from here, PLEASE HELP!!!

---

### Post by abn91c on 2008-12-19
try running sudo apt-get check and sudo apt-get clean, also try changing the repositories servers

---

### Post by Fidju on 2008-12-20
i tried running 'sudo apt-get check' and i was given this error:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


so then i tried changing repositories and i was given the same error as before when trying to update.  any other suggestions?

---

