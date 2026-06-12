---
title: "potential xorg problem with fresh install?"
date: 2008-08-02
forum: General Help
---

### Post by treehouse on 2008-08-02
So I was using Hardy back when it was a beta and it wouldn't jive with my old 3dfx Voodoo3 card (super low resolution on my 1280x1040 monitor). Basically, it wouldn't use whatever was in the xorg.conf file, whether it was generated automatically, or hand typed. I fresh installed Gutsy and did the dpkg-configure, and everything worked. Since then I've had to upgrade to Gutsy, and it's still working (xorg.conf isn't generic, but has my video card info), but I was considering a fresh install in order to switch over to KDE. Am I likely to have the display issues? How clean and easy is it just to install KDE without fresh install? Benefits? Detriments?


Thanks, and sorry if this stuff has been posted already but I couldn't find anything that seemed to give me the answer I was looking for.

---

### Post by collinp on 2008-08-02
I dont see any problems with a fresh install, just remember to backup all your files and your xorg.conf file to re-add to your new install.

---

### Post by pietjanjaap on 2008-08-02
This has changed in 8.04, de detection of your videocard and monitor, so if ubuntu does not reconnize your card do this:

With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

