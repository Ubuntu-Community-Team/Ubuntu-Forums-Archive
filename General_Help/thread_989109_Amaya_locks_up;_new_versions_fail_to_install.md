---
title: "Amaya locks up; new versions fail to install"
date: 2008-11-21
forum: General Help
---

### Post by hewen on 2008-11-21
Amaya installed via Ubuntu's installer locks up - it works well at first, but then begins to lock-unlock-lock-unlock as if every command it receives is taking 30 seconds to process. 

I uninstalled and dowloaded/installed two versions directly from Amaya's site ([http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)). I installed release 10.1 and then release 10. Both failed to install. The last message on the screen after each installation is:

trying to overwrite /usr/share/pixmaps/amaya.png which is also in package amaya-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I manually deleted amaya.png and retried. Same result even when the file clearly doesn't exist. 

I'm running: Ubuntu 8.04 on an Athlon 64 x2 Dual Core (but with Ubuntu 32-bit version installed).

Thanks for any help. Fortunately Bluefish works well.

---

### Post by beow on 2008-11-24
Had the same problem. Installed ver 10.0 ubuntu .deb from the Amaya home page and it looks much better. Haven't tested much yet but it looks promising.

---

