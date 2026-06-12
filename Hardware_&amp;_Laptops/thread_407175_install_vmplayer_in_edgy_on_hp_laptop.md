---
title: "install vmplayer in edgy on hp laptop?"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by scradock on 2007-04-11
I'm trying to install vmplayer in edgy on my HP Pavilion. I got the .deb from vmware and installed using Gdeb. I cannot get vmplayer to launch. If I click on the vmplayer.sh in /etc/vmware nothing happens. If I click on a .vmx file in its own directory nothing happens.

If I go to /etc/vmware in a terminal and type "vmplayer" I get messages about the gtk24 wrapper being not found. I fixed that by copying it to the excpected place, but now it seems that evrything is in the "wrong" place.

The install has created a vmware directory in /usr/lib. It appears that the scripts are expecting vmplayer to be in /bin, rather than in /usr/lib/vmware/bin, for instance. What do I need to do to get this working correctly? I have tried re-installing - no change in behavior.

I have read several "how-tos", but they all take for granted that vmplayer simply installs and runs.....
sc

---

### Post by MyR on 2007-04-12
have you tryed installing vmware *server*?

---

### Post by scradock on 2007-04-13
OK, I got it.

The vmplayer package from VMware may need the vmplayer-headers package from the repositories to run. 

Also, the VMware package is a .rpm, and I needed to run "alien -ck vmp*.rpm" to include all the set-up scripts, not just "alien -k vmp*.rpm" .

After doing both those I got the player installed fine. 

Now I need some Windows .iso images....

---

