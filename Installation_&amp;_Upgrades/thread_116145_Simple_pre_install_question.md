---
title: "Simple pre install question"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2006-01-12
I got myself a new hdd and plan to install Breezy on it in a dual boot system with XP; 
question: Can I configure the new hdd as slave and install Breezy on hdb0 and Grub in hd1,0  or does the Ubuntu OS need to be installed on hda?

Thanks

---

### Post by daschl on 2006-01-12
[QUOTE=Luke771]I got myself a new hdd and plan to install Breezy on it in a dual boot system with XP; 
question: Can I configure the new hdd as slave and install Breezy on hdb0 and Grub in hd1,0  or does the Ubuntu OS need to be installed on hda?

Thanks[/QUOTE]

no, ubuntu doesnt care about this fact

if you have windows installed already, just put in the ubuntu installation cd rom, install it on the second hard drive and let the automated grub-install script do the rest

in the expert mode you also can use linux if you want to do so

---

### Post by Luke771 on 2006-01-12
Got it up & running by installing Breezy in hdb1 and Grub in MBR.
(the first try with Grub in hd01,0 did not work)

---

