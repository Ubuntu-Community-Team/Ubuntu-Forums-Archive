---
title: "plz any1 know to to intall a game at inux using wine?"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by spskark7 on 2009-08-07
hi!,
any1 know how to install titan quest and titan quest immortal throne at linux ububtu 8.04
i have aready instl wine but W I CAN USE IT??

---

### Post by joe2012 on 2009-08-07
You can try this:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3480](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3480)

Not sure if it's the right game or not though. Good luck.

---

### Post by spskark7 on 2009-08-07
dont work any other ways?

---

### Post by Mark Phelps on 2009-08-07
> **spskark7 said:**
> dont work any other ways?

This is a MS Windows game and won't run natively in Linux.  You can try some emulators like Wine or Crossover, or you can install Virtualbox, then install MS Windows inside that, and then install your game.  But, you're likely to get poor performance, then.

---

### Post by joelgsf on 2009-08-07
Not all Windows Apps can be run under Wine. Do as for any other Win App:
- change your current directory to wherever is your "setup.exe" (or whatever installation executable you have);
- then run
```
wine setup.exe
```
That is all, if it works. If not, my best next suggestion is installing Windows under some Virtual Machine (VBox, VMware, or the like) and install it as usual for Windows.
(Note: you can tell Wine which Windows to fake, if necessary - Win95/98/2K/XP)

---

