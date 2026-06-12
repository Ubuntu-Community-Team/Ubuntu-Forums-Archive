---
title: "Deleting Ubuntu Help"
date: 2008-08-21
forum: General Help
---

### Post by ZeroRider13 on 2008-08-21
Hey Im deleting Ubuntu until I can actually get broadband so itll work.

I downloaded it "as an application" so I could dual boot, but Id like to get it off, how can i do this?  Also, I have 2 partitions, one 2933mb, and the other 160gb, can i delete that second partition, or should i use it somehow or what?

---

### Post by rossjman1 on 2008-08-21
If you used Wubi then it would be in the Add/Remove dialog in Windows.
If you installed via a cd, you need to uninstall grub and repartition your drive so Windows takes up the entire drive.

---

### Post by ZeroRider13 on 2008-08-21
It was a cd...how do I do that?

---

### Post by rossjman1 on 2008-08-21
**Only do this if you have a Windows Install CD**
Boot off the Ubuntu live cd and go into GParted. Delete the Ubuntu partition AND the swap partition and resize the Windows partition to fill the empty space (Do a defrag in Windows before doing this!!!). Restart your computer and boot the Windows install CD. Go into the recovery prompt and type fixmbr. Restart and you should be all good!

---

