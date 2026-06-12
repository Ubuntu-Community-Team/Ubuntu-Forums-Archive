---
title: "stuck in rt..(hardy)"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by nematodsa on 2009-03-05
Hi, i have some funny problems over here which basically im pretty much stuck.

here is how it goes, 
i change from kde4 to ubuntu 8.04 due to some graphical issue, and when i was doing some audio editing work, i upgrade to ubuntustudio through commandline
-sudo apt-get install ubuntustudio*
and whalla .. everything goes fine right after the reboot stage, ubuntustudio cant start due to some graphic error.
so i revert back to the genome version and uninstall ubuntustudio, 
the result is i am able to boot direclty to rt (kernel linux 2.6.24-23-rt)
at the lost of all the graphics and shortcut keys.

anyhelp?

---

### Post by cariboo on 2009-03-05
Because you are using a different kernel you will have to reinstall your graphics drivers. Start in recovery mode, and at the menu choose xfix, once xfix is done choose resume to continue to your desktop.

Jim

---

### Post by nematodsa on 2009-03-06
hi jim, 

i have tried what you have suggested, there is no display while the os booth, but it has the ubuntustudio when it log out. so am i using ubuntu studio now?

i still cant use back my normal setting that is run by compiz when i was using ubuntu genome, how does i revert back to ubuntu genome from ubuntu rt.

---

### Post by nematodsa on 2009-03-10
hahaa..i have manage to revert back to generic hardy, but it seems that compfiz is not working, can i know how am i able to re-enable it?

---

