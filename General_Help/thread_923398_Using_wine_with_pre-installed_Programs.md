---
title: "Using wine with pre-installed Programs"
date: 2008-09-18
forum: General Help
---

### Post by drako1011 on 2008-09-18
Hi,

I am dual booting Ubuntu 8.04LTS and Windows Vista Home Premium. I have a program already installed on my Windows partition and I'm wondering if there is a way to use wine to access the program without having to re-install it.

Thanks

---

### Post by Titan8990 on 2008-09-18
No, you can't. It needs to be reinstalled via WINE.

---

### Post by whizbaby on 2008-09-18
I had GTA San Andreas installed on an old windows drive and I could start it with wine instantly. This drives mount point is /media/hda5 and I start with
```
wine /media/hda5/games/gtasa/gta_sa.exe
```
Hope something similar works for you.
GreetZbaby

---

### Post by howefield on 2008-09-18
Afraid not, you would need to install your windows program to your Ubuntu installation, (assuming that it works with wine).

---

### Post by SecretCode on 2008-09-18
It really depends on the program. Surprisingly, some programs for windows are well-behaved* and don't require entries in the registry. Effectively they don't require installation at all. If it *needs* installation, it'll need reinstallation under wine.

* Not Microsoft's definition of well-behaved.

---

### Post by whizbaby on 2008-09-18
How about just syncing the real windows installation 'windows' folder to wines 'windows' folder? Shouldnt that copy the registry and .dlls, too? It shouldnt be too risky as only .wine/drive_c/windows gets messed up and can be reverted easily if you didnt install much software in wine.

---

