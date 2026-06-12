---
title: "Ubuntu shut downs when my laptop gets too hot"
date: 2008-09-06
forum: General Help
---

### Post by FastMady123 on 2008-09-06
Ubuntu shut downs automatically when my laptop gets too hot and doing "poweruser" tasks. It also shut down automatically when I'm browsing the Web fast. When It shut down, it shows me a log before the Ubuntu logo show up. The log contains the words "NetworkManager" and "dbus-daemon". This is a common problem that I face everyday and I'm tired with it. My laptop got water spilled on it before. I think it a bug in NetworkManager and/or my hardware problems that cause this problem. I think I need the Ubuntu and NetworkManager source code to fix this problem. My RAM memory is 494.1 MiB. My CPU is Intel Celeron M CPU 410 @ 1.46GHz. I may need to buy new RAM (2 GiB). What should I do to fix this problem?

---

### Post by ryanhaigh on 2008-09-07
The network-manager message is quite normal during shutdown, however your computer overheating and causing a shutdown is a much bigger issue. Are all your fans working since the water? There may be a way to overide the temperature at which the system will shutdown but I haven't tried this before and can't advise you to do it because it may end up damaging your computer. This option may also exist in the bios.

I would look at why your computer is getting so hot to begin with, can you install lmsensors or something to monitor the temperature of the system?

---

