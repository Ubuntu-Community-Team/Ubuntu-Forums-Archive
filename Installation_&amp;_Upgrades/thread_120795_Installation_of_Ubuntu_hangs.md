---
title: "Installation of Ubuntu hangs"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by devilslayer on 2006-01-23
I have tried to install the live cd version of ubuntu and the full versions of Edubuntu and Ubuntu Breezy Badger.

The install seems to be coing fine, then the screen just goes black and i have a white - in the top left hand corner of the screen.

Debian Sarge, xandros, libranet and all other debian based distros i have tried install just fine.

I have tried the install with different media and on different computers, both pentium 3's

Any ideas?

---

### Post by jimsmith80220 on 2006-01-25
I have the same problem, a white - after rebooting. In /var/log/syslog.0 at end of file is
modprobe: FATAL: Error insterting apm (/lib/modules/2.6.1 2-9-386/kernel/arch/i386/kernel/apm.ko): No such device
exiting on signal 15

also many instances of dependency problems in the log.

thanks for any help.

---

### Post by jimsmith80220 on 2006-01-26
Finally get things to work. I had the nvidia TNT2 problem and needed the legacy driver; these pages helped a lot:
[http://ubuntuforums.org/showthread.php?t=79224&highlight=tnt2](http://ubuntuforums.org/showthread.php?t=79224&highlight=tnt2)
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
I had to edit xorg.conf bus id and then I was up and running.
Now I just need help installing on an old emachine...
Thanks tseliot

---

