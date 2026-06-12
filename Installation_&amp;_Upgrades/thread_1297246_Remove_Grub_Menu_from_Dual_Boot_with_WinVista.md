---
title: "Remove Grub Menu from Dual Boot with WinVista"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by Max Avion on 2009-10-21
Hello,

I am running Ubuntu 8.04 along side Windows Vista but somehow have ended up with a Grub boot menu which is displayed at startup to OS selection. I was wondering if it is possible to take this out without damaging either OS installation. I would like to see the boot menu which is simply Windows Vista/Ubuntu right now I have this large menu 3 for Ubuntu and 2 for Windows Vista Loghorn Loader. Any help or advice would be very much appreciated. Many thanks in advance. 

Regards,
Max

---

### Post by ajgreeny on 2009-10-21
You can edit your grub menu.lst file easily if you really want to, but the three ubuntu entries are probably:-
1.  The kernel you normally boot.
2.  Recovery mode for the kernel you boot.
3.  Memtest 86+

And the two windows entries are possibly/probably:-
1.  The windows install you boot to.
2.  A recovery partition used to recover a broken or re-install your windows OS.

I suggest you leave all of them as it may be useful to have them in future if something goes wrong with your system in any way.

However install startup-manager from the repos and you can do what you want, and also reduce the time the menu shows from 10secs to 2 or 3 secs if you prefer.

---

