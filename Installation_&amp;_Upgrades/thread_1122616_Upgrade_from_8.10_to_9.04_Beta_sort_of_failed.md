---
title: "Upgrade from 8.10 to 9.04 Beta sort of failed"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by Sebastian Mares on 2009-04-11
Hey guys, I just upgraded my Ubuntu this morning from 8.10 to 9.04. I had no errors whatsoever during the upgrade, but when I boot my computer now, I get to the point where I am supposed to enter my username and password and after I do this, I only see an empty desktop without icons or menus. Switching to the second desktop works and when I press CTRL+ALT+DEL the Shutdown / Reboot / Suspend / Hibernate window appears, but nothing else works (Win+E works and opens the desktop selector). Any ideas what might be wrong?

Edit: The 8.10 installation was modified to contain Thunderbird instead of Evolution, I installed Opera, VirtualBox and also Skype via the Medibuntu rep.

---

### Post by iponeverything on 2009-04-11
try adding an new user from the command line and logging in with it. -- if that works then there may have been an issue with the migration of your user account from 8.10.

---

### Post by Sebastian Mares on 2009-04-11
Thanks for the tip, it worked. Newly created users load fine. Any idea if it is somehow possible to copy some settings over to a new account?

---

