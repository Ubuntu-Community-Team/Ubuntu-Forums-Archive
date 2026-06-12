---
title: "wubi - what to do after trial"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by neilcox on 2009-10-27
Hi,
 
I'm just about to try Ubuntu for the first time and want to use Wubi to try it out. 
 
However, my (WinXP) laptop's disk is pretty full which rules out any dual-boot in the long-term. If I'm happy with Ubuntu, I'd like to remove Windows XP completely and make the machine a solely Ubunto system. I've no problem with backing up all my data from WinXP as I have a USB harddrive.
 
Is there a way to convert a Wubi-created system into a single boot image once I'm happy with it? It would be nice not to have to wipe everything and reinstall Ubuntu from scratch again.
 
Cheers
Neil.

---

### Post by Mark Phelps on 2009-10-27
Yes, there is a way to convert the Wubi install to a "normal" install -- but it requires creating space on the driver to hold Ubuntu partitions.

You said you were low on space, so even though the default Wubi install space is small. (about 2.5GB), it still takes up room.  When you then go to convert it, you will need the ADDITIONAL space set aside for the partitions.

So, it will actually take more room to do Wubi now, and convert later, than just to allocate space now and do a "normal" dual-boot install.

---

