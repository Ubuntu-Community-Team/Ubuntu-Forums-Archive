---
title: "Upgrades don't work, either video drivers fail or CD/DVD reader/writer doesn't work"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by nrr_shopping@yahoo.com on 2009-10-17
Hi! I am new to Ubuntu, and so far 2 out of 2 upgrades have failed miserably.  After the first upgrade, I was able to ignore the upgrade and boot in the original version of Ubuntu.  After the second upgrade, I can still boot in the original version, but the CD/DVD reader/writer no longer works.  When I tried to boot in either of the upgrades, it cannot load the nvidia drivers for my monitors, and reports an error and never loads the graphical operating system environment.  

Specific Info:
I am using 9.04.  The first version had kernel 2.6.28.11.  The second version had 2.6.28.14.  The last version had 2.6.28.15.  I have a dual-boot system with Windows Vista.

The upgrade manager comes up and lists the specific packages, which I am free to select from.  That appears to be doing what is appropriate.  When I select the "install updates" button, it still seems to be doing what is appropriate.  When I reboot the machine, it gives me a list of which operating system I want to boot into.  These include the original Ubuntu, the latest Ubuntu and Windows Vista.  If I select the latest Ubuntu, it load the nvidia drivers, and the Ubuntu can't complete loading.

I have two monitors.  I modified /etc/X11/xorg.conf, so that I wouldn't have to set up the dual monitors every time I turned on the computer.  I've attached a copy of that file to this thread.

Does anyone have any idea why my upgrades keep going bad, and does anyone have any idea how to fix the fact that I can't read from my CD/DVD reader/writer anymore?

Thanks in advance!
NRR

---

