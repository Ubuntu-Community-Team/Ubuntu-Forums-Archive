---
title: "I/O error, dev sr0 - after jaunty install"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Benthe1st on 2009-04-25
Hi everyone!

I've installed Ubuntu 9.04 on my laptop, and after install, when the installer says to take out cd, close tray, then press enter to continue, i pressed enter, and got error messages:
x.xxxxxx, end request: I/O error, dev sr0, logical block xxxxxx
(something similar)
I've read several forums, and turned out, that it is because of some problems with cd-rom, but others got this message before install, so they couldnt install. I got this after install, so my question is: could it corrupt my new ubuntu install or probably my install is perfect? (there has been no error message during install, just that ones after install.
Thx in advance!

---

### Post by jawadahmed on 2009-10-25
I am having exactly the same problem. If you find the answer please post back here so that i can also get the solution.

---

### Post by Bezmotivnik on 2009-10-29
Me too, even in live mode.

---

### Post by gvor54 on 2009-10-29
got a message of this sort when shutting down computer

---

### Post by DevilEvilGod on 2009-11-03
im having same error but on karmic 9.10 install
 
everex sa 2052t
 
with modules blacklisted:
sdhci
sdhci-pci
mmc_core
 
and error ends like this:
569.954147 kernel panic -not syncing
pid: 1, comm: run-init not tainted 2.6.31-14-generic #48-ubuntu
call trace:
<c056e41c> ?printk+0x18/0x1c
drm:intelfb_panic *ERROR* panic ocurred
 
hmm hope someone can help im almost giving up....

---

### Post by Benthe1st on 2009-11-05
> **jawadahmed said:**
> I am having exactly the same problem. If you find the answer please post back here so that i can also get the solution.

Hi!

I couldn't find an answer to my question, so I decided to use my jaunty install on my laptop, and if something is wrong, then I'll try to solve it, but everything works great. I had no problem with my system, so it didn't corrupt my installation. So if you have the same problem I had, dont worry!

Ben

---

