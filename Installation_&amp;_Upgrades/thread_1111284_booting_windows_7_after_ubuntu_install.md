---
title: "booting windows 7 after ubuntu install"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by pinkspice on 2009-03-30
hi, i have not long ago installed ubuntu intrepid on a machine that already had windows 7 installed. both are on separate hard drives. however since installing ubuntu, when i get to the grub loader it just shows windows xp (which i presumed was my windows 7) and when i select it i get a black screen with starting up.... in the top corner and it wont go any further. What can i do to get back my windows as there are programs I need to use for work that wont run with wine or crossover, so i hav to be able to use windows as well. Thanks

---

### Post by Mark Phelps on 2009-03-30
I'm guessing here, but if you had XP first, then installed Seven dual boot, it wrote the Seven loader files to the XP partition.  If you later removed the XP partion or overwrote it with something else, you removed the Seven loader files.  I'm guessing this because without XP there originally, you wouldn't get an XP entry in the Windows boot menu.

Windows 7 comes with an option to create a recovery CD.  Did you do that?  If you did, you can boot from that and restore your loader files.

If not, you can try downloading and burning a Vista recovery CD from the Neosmart forums.  It might work.

---

