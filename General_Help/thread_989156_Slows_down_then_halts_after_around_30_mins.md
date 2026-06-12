---
title: "Slows down then halts after around 30 mins"
date: 2008-11-21
forum: General Help
---

### Post by jimhaddon on 2008-11-21
Using Kubuntu, after about 30 mins, the system slows to a crawl (where even the mouse pointer stutters and amarok goes silent), then halts completely. When the system is hanging, the HDD light is flashing like mad, and the CPU sounds like it is running very high. I'm unable to pin point what is causing this as by the time it has started, I'm unable to open the system monitor or do a ctrl+alt+f1. 

The only thing to fix it is to do a hard reboot.

Any ideas fellas?

---

### Post by Peter09 on 2008-11-21
Run System Monitor from when you start your session, then you will be able to see what is causing the problem (better still use htop)

---

### Post by jimhaddon on 2008-11-22
Looks like I found the problem...

Amarok is using ~41% of the CPU constantly, whilst also after a little while of internet streaming using 400MB of memory - but is constantly growing at about 100MB / 2 mins. 

Does amarok usually use this amount of resource?

---

### Post by jimhaddon on 2008-11-22
Further to the above, this only happens when I click the 'Playlists' button on the left.

Before clicking this, the CPU usage hovers around 4% and memory about 22MB.

As soon as I click playlists, CPU shoots to 41% and memory to 80MB and continues to grow - is this normal?

---

### Post by Peter09 on 2008-11-22
Its a bug

[http://lists.kde.org/?l=amarok-bugs-dist&m=121743493714009&w=2](http://lists.kde.org/?l=amarok-bugs-dist&m=121743493714009&w=2)

---

