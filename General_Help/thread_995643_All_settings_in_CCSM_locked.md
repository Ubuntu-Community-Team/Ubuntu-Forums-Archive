---
title: "All settings in CCSM locked"
date: 2008-11-28
forum: General Help
---

### Post by LinuxFanBoi on 2008-11-28
Problem,  After installing Emerald,  I later wanted to modify some settings in Compiz Configuration settings manager.  to my surprise,  every setting is locked.  I cant change anything.  

So far I have removed Emerald,  Reinstalled CCSM and Compiz all together.  Every setting is still locked.

Any suggestions?

---

### Post by LinuxFanBoi on 2008-11-28
solved..

solution was to rm -r /home/admin/.config/compiz/compizconfig/config

Restart CCSM make desired changes, problem solved.

---

### Post by eternalnewbee on 2008-11-28
Then you should mark this thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

