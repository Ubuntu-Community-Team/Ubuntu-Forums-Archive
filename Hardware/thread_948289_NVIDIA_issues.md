---
title: "NVIDIA issues"
date: 2008-10-15
forum: Hardware
---

### Post by irisblaze on 2008-10-15
ok I have GeForce FX 5200, since I have an old pc at home, I decided to install OzOs which is based on Ubuntu Hardy Heron (8.04) with e17 instead of Gnome or kde, because it doesn't take much ram and got all the new stuff..

after installing the OS, it didn't make my screen resolution 1200X1024 but 1024X768, also games were running slowly.. so i decided to install nvidia drivers, first i tried the easiest method, typed restricted-manager but it told command not found, I skipped to envy, but envy told me it doesn't support my os (maybe because it's 8.04?) instead of exploring the source code of envy i skipped to installing the drivers manually, i downloaded the NVIDIA linux drivers from nvidia web site, stopped x server, and ran the installation, it went fine, and everything went good, and after starting the X server again, I made my screen resoultion 1200X1024, and ran neverball :)

now everything was fine until i restarted my pc :( then my screen resolution went to 800X600 0.o and the os doesn'tr detect my drivers, however when i type:

> cat /etc/X11/xorg.conf | grep nvidia

I get nvidia and also i get there's nvidia module when typing:

> lsmod | grep nvidia

i tried installing the drivers again and it worked... everytime i reinstall the drivers it works, until i restart my pc :(

what could be the problem?

---

### Post by kpkeerthi on 2008-10-15
[This]("http://ubuntuforums.org/showthread.php?t=815303") might help.

---

