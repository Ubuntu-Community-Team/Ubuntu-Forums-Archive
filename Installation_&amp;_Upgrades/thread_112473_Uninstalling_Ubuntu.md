---
title: "Uninstalling Ubuntu"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by jreist on 2006-01-04
My son brought home an install CD for ubuntu linix and I tried to install it on my computer using Grub to provide a dual boot to Win XP.

After trying to work with it I found it was not workingand could not get my video and sound cards to work properly.  Not meant for 50+

I went into Windows and deleted the partitions and restarted Windows only to having the computer stop at the command line 
Grub error.

How does one remove Ubuntu linix on a dual boot system using Grub with out effecting Window XP?

---

### Post by ed_d on 2006-01-04
IIRC:

Back up all your data.

Boot with windows cd and go into safe mode (F8)

get a command prompt from safe mode (C:\)

At prompt type in fixmbr.

Remove cd and reboot.

---

### Post by CzarAlex on 2006-01-04
Very close.

Its the Recovery mode, not safe mode.

---

