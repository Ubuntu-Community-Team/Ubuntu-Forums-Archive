---
title: "serious updating/crashing issue."
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by roflnoob on 2009-01-11
I have absolutely no idea what is going on. I am new to ubuntu, and would put this on the absolute newbies board if this wasn't such a complex issue. And in case this is relevant, I used wubi to partition my hard drive and install ubuntu just yesterday, due to laziness.

Periodically, ubuntu will just crash (I think this is the correct term; my monitor either freezes or blacks out and I can't do anything other than unplug my computer and boot it back up again). There is nothing that connects these instances together; I could be playing a game or browsing the internet, or not even running anything while i'm away from the computer.This happens fairly often: about 5 times yesterday. 

Thinking there would be an update that fixed it, I turned on update manager and started downloading the 218 up, and in the middle of the installation, it crashed. after having to unplug the thing to turn it off and then booting ubuntu back up again, I can't get more programs or finish updating. when I turn on the update manager, I get an error message that says:

"E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache ->open() failed, please report"

I tried to run 'dpkg --configure -a' in terminal, but it says that I need "superuser priviledges" even though my account has adminship. I then tried uninstalling/reinstalling ubuntu through wubi and trying it all over again, and the same thing happened. Help!

---

### Post by Drubie on 2009-01-11
> **roflnoob said:**
> 
I tried to run 'dpkg --configure -a' in terminal, but it says that I need "superuser priviledges" even though my account has adminship. I then tried uninstalling/reinstalling ubuntu through wubi and trying it all over again, and the same thing happened. Help!

to get "superuser priviledges" type ```
sudo dpkg --configure -a
```

I have no idea why your computer keeps freezing...
I am currently figuring out why my own is acting funky...

Good Luck

---

### Post by avtolle on 2009-01-11
Due to your pulling the plug, your NFTS file system is likely corrupted. See [https://wiki.ubuntu.com/WubiGuide#Corrupted%20NTFS%20filesystem](https://wiki.ubuntu.com/WubiGuide#Corrupted%20NTFS%20filesystem) and follow the directions to see if it helps. Good luck.

---

