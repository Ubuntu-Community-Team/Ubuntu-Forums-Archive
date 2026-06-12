---
title: "Can't Print over LAN after Latest Upgrade"
date: 2008-07-27
forum: General Help
---

### Post by misterfixit on 2008-07-27
[B][I]Problem using 2 printers connected directly to PC on a 2-PC LAN. CUPS on Firefox shows both printers available on remote Ubuntu 8.01 PC located 2 meters away and connected via LAN. Network shows both Ubuntu 8.01 machines; 


Soooo, anyone want to help me out here?

---

### Post by misterfixit on 2008-08-23
Bump??  83 views and no replies?  Nobody has ANY idea????  Hello, Ubuntu Community ?

---

### Post by oldsoundguy on 2008-08-23
Can you see all of the printers from all of the computers?  
The cups drivers for the printer on computer A have to be installed on computer B and every other computer on your network.  (if on a Windows machine, use the choice "Windows via Samba" when setting up the Linux machines.) You also have to go to the host computer (the one the printer is attached to) and "make it available to the network." (again, the set up utility will do that.)

I have 5 computers on my network .. 2 XP machines and 3 Gutsy machines. They reside in 3 locations so each location has a "local" printer. I have a total of 7 printers spread around (some SPECIALTY printers). 2 of those printers do NOT have cups drivers(one a Raster or Mac based laser and an Avery label printer) (so are hooked to Windows machines),  the other 5 (Post Script based) are accessible from anywhere on the network.

I have seen some instances where some of the el Cheapo printers have had to be installed to a networking printer hub, as they would not work otherwise. That too, could be your issue.


EDIT:
In re-reading I see it happened with an upgrade.  Now if that upgrade was the kernel or to Samba and you were using restricted drivers, those will have to be re-installed on all Linux machines.

I had an issue with restricted VIDEO driver and the last kernel update.  Required a re-install and all was well.

---

### Post by misterfixit on 2008-08-24
> **oldsoundguy said:**
> Can you see all of the printers from all of the computers?  

No. Cannot se printers from remote;

The cups drivers for the printer on computer A have to be installed on computer B and every other computer on your network.  (if on a Windows machine, use the choice "Windows via Samba" when setting up the Linux machines.) You also have to go to the host computer (the one the printer is attached to) and "make it available to the network." (again, the set up utility will do that.)

Both machines are Identical Ubuntu single boot;  Both machines have drivers installed, etc.

I have 5 computers on my network .. 2 XP machines and 3 Gutsy machines. They reside in 3 locations so each location has a "local" printer. I have a total of 7 printers spread around (some SPECIALTY printers). 2 of those printers do NOT have cups drivers(one a Raster or Mac based laser and an Avery label printer) (so are hooked to Windows machines),  the other 5 (Post Script based) are accessible from anywhere on the network.

Printers are both HP; a LaserJet 4000; a C7300 Multifunction

I have seen some instances where some of the el Cheapo printers have had to be installed to a networking printer hub, as they would not work otherwise. That too, could be your issue.


EVERYTHING worked fine up until last upgrade.

All "restricted drivers" reinstalled.

EDIT:
In re-reading I see it happened with an upgrade.  Now if that upgrade was the kernel or to Samba and you were using restricted drivers, those will have to be re-installed on all Linux machines.

I had an issue with restricted VIDEO driver and the last kernel update.  Required a re-install and all was well.


Thank you for your help.

---

### Post by oldsoundguy on 2008-08-24
Then maybe an uninstall of the printers, re-boot, and re-install.  That sometimes works in Windows but never have had to do so in Linux.  Since it is not working now, might be worth a shot.

---

### Post by misterfixit on 2008-08-24
> **oldsoundguy said:**
> Then maybe an uninstall of the printers, re-boot, and re-install.  That sometimes works in Windows but never have had to do so in Linux.  Since it is not working now, might be worth a shot.

Done that already.  No joy.

---

