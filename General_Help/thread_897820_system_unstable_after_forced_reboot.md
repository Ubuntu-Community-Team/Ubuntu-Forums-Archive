---
title: "system unstable after forced reboot"
date: 2008-08-22
forum: General Help
---

### Post by dexter.deepak on 2008-08-22
i had to reboot my hardy system (i think that is called a hard reboot), through the reset button on my cpu.
during my next startup, the system came to a standstill on a line saying something related to MTA (i dont exactly remember what it was), but after some time, my startup continued. this MTA problem continued for 3-4 startups nd now i dont get any problem at that stage.

the only persistent problem i face is related to the system speed, it is almost 6 times slower than before. i cant think of any other cause. a terminal takes about 5 seconds to open:(

---

### Post by LateNiteTV on 2008-08-22
> **dexter.deepak said:**
> i had to reboot my hardy system (i think that is called a hard reboot), through the reset button on my cpu.
during my next startup, the system came to a standstill on a line saying something related to MTA (i dont exactly remember what it was), but after some time, my startup continued. this MTA problem continued for 3-4 startups nd now i dont get any problem at that stage.

the only persistent problem i face is related to the system speed, it is almost 6 times slower than before. i cant think of any other cause. a terminal takes about 5 seconds to open:(

this may or may not be whats going on, but it happens on my freebsd machines when i have to run fsck. fsck is "file system check". it WILL slow down your system until it completes, which depending on your hard drive capacity can take a while.

---

