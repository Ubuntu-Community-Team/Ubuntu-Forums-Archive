---
title: "Question about install/partition..."
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by neoltlink on 2005-12-14
Alright, I recently formatted my my 40gb hdd, and installed ubuntu. I then proceeded to install windows on a seperate partition(7gb swap, 20gb linux, 12gb windows xp).
However, I think that I either didn't/havn't done something right, or...well, I know that I messed up somewhere. 
Anyway, back to the point, only windows is listed in the OS selection menu, and in command prompt it states that the drives I installed linux and my swap space on don't exist.
(C: and E:). 
Any ideas on what to do?
EDIT: Reading around, it seems that I should have used something like partitianmagic to do it and install ubuntu on that. So, any ideas on how to get to/format those drives?

---

### Post by Qrk on 2005-12-14
I would load up your Ubuntu (live or install) CD and make sure you Ubuntu partitions still exist. Windows can overwrite them. By the way... are you sure you have 7 GB swap?? There is no way you need that much. Even 1GB is overkill for most people. 

If your partitions still exist, you should only need to edit Grub. The forums can help with that. If they don't.. just reinstall Ubuntu.

---

### Post by neoltlink on 2005-12-14
EDITx2: Disregard this post, my brain went dead for a second. And thanks! :D
EDIT: Forgot to mention, windows is on F: drive, so I'm pretty sure they still exist.

---

### Post by AmboyGuy on 2005-12-14
When I was setting up my system for dual boot, everything I read in the forums & wiki's & How to's always recomended installing windows first, and then installing Ubuntu. You would use the installer's partition manager in manual mode and let GRUB be your boot manager.
In the many times I installed Hoary when first starting out ( I had a bum memory chip in the hard drive buffer ) I used the install disk's expert mode to check & resize partitions and re-install GRUB.

---

