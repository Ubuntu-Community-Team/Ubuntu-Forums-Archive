---
title: "can i charge my PC backup.tgz to laptop?"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-01-30
hey every one,

i did backed up my PC OS (ubuntu) and i want it on my laptop as well, as i have it all configured and like it. 
can i do that with my laptop (core2duo) hardware being totally different from PC (Intel Pentium 4) both i86. Can I??

much thanks in advance....

---

### Post by lemming465 on 2009-02-01
You can try it.  There are likely to be some problems with drivers, particularly video chip differences, so you'd likely have to run things like *sudo dpkg-reconfigure xserver-xorg* afterwards.

If most of the setup your care about relates to user desktop stuff and which applications are installed, there is an intermediate option.  You can do a minimal install (desktop or server) to the laptop, use *dpkg --get-selections* on the desktop to get a list of what packages are installed, use *dpkg --set-selections* to import it on the laptop, and copy in your desktop home directory.

If you have a lot of modified daemon configuration files under /etc the migration would be trickier.

---

