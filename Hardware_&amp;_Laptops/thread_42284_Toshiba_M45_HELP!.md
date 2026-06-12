---
title: "Toshiba M45 HELP!"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by AE86_Racer on 2005-06-16
Ok this is my second time installing Ubuntu on a PC.  My first attempt with a gateway went well accept no sound.  This time around Im running into a whole mess of trouble

Right now the system wont even load.  It locks up trying to load the hotplug subsystem

Any ideas?  I really want to get this installed but if it isnt gonna work, I may as well junk it

---

### Post by evenodd on 2005-06-19
I too have this problem.  It freezes at the "starting hotplug subsystem" and ctrl-alt-del doesn't work.  I have to physically shut down.

---

### Post by Angel Herranz on 2005-07-11
The cause of the problem is the module sk98lin that hangs the hotplug subsystem.

I blacklisted it inmediatly after first reboot in the installation process (/target/etc/hotplug/blacklist).

I got a M40-145 yesterday and I'm having a lot of problems with some drivers: lan, wireless and ati.  I'm interested in sharing solutions.  There is my email address.


--
angel
aherranz at gmail com

---

