---
title: "Problems after system change"
date: 2008-07-24
forum: General Help
---

### Post by s57nev on 2008-07-24
I just bought  a new computer and plugged my old scsi disc in. I tried to run Ubuntu. I'm experiencing problems with Gnome environment. After I log in Gnome simply stops working. Sometimes my panel doasn't work, some programs doasn't work any more etc. Funny thing is that after reboot everything works ok for a while till I try to start Terminal or other apps. Firefox just doasn't work any more..etc.. I tried to delete all my gnome settings from home directory.  I don't think there are hardware problems since fckn Windows work OK. Now I have Core 2 Duo E8400, Intel based chipset motherboard and Nvidia 8600GT.


Is there anything I could do to renew whole ubuntu instalation as alternative to new instalation ? Is it possible this is hardware change problem ? Is there anything I can do to fix this ? Maybe reconfigure something ? Thanks!

PS: My old eth0 is now eth1 :(

---

### Post by ryanhaigh on 2008-07-28
Sounds like you put a hard disk with a previous ubuntu install into your new pc is that right? I have done this a couple of times and didn't have too many issues. The major thing is the graphics card. If your old pc used a different card or even an earlier nvidia then you probably need to change drivers. The bad news is that this can sometimes be a pain as old drivers sometimes leave files lying around which stop the new nvidia driver working (had this issue when i went from ati to nvidia). 

IIRC you can change the network interface back to eth0 by editing /etc/iftab.

---

