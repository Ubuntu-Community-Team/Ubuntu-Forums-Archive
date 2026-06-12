---
title: "ubiquity crashes during jaunty install"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by axyelp on 2009-05-05
the installation process goes above 50% and then the crash report msg saying ubiquity crashed!

tried the jaunty cd n dvd.. both!

---

### Post by axyelp on 2009-05-05
bump... help me out guys,.. i'am working entirely on a live cd!!!

---

### Post by slick601 on 2009-05-07
Me too. I am using a Dell Inspiron 8100, and during install it has failed multiple times.  I have tried to use EXT3 and EXT4 on two attempts, and tried to install from liveCD and once directly installing from boot menu. 

Any suggestions?  I have successfully installed onto my netbook without any issues using a different download; possibly corrupt ISO image for this download?  Will do a checksum and update if not matching.

-Mike

---

### Post by earthpigg on 2009-05-16
bump

same problem here

---

### Post by trumpcouptimmy on 2009-06-07
Me too. Does the install put a log file anywhere where you can see what the problem is? When it automatically reboots into the live cd, it wants to send a crash report for ubiquity. I'm trying to do a clean install on a Sony Vaio laptop with XP already installed. I also tried the LinuxMint 7 that is based on jaunty-same thing. It's not the cd - md5 of download good. Burned with K3b and verified OK. Ran the cd test on the boot menu-all OK.

---

### Post by markbuntu on 2009-06-08
I had that problem. Try this. Run the live cd. Open a terminal and...

ubiquity --no-migration-assistant

The installer should run OK after that. I have 5 different distros on this machine and ubiquity tried to migrate my setting from all of them so it crashed. There is a big pile of bug reports at launchpad about this.

[https://bugs.launchpad.net/bugs/326398](https://bugs.launchpad.net/bugs/326398)

---

### Post by trumpcouptimmy on 2009-06-10
It even did it with the no-migration line and it didn't work for me. I did get an install done. I had to download the alternate cd iso, burn it and use it. For those who can't make anything work, try it-

---

