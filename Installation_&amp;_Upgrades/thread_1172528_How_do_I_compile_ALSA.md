---
title: "How do I compile ALSA?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by rreyes1316 on 2009-05-28
I am still fairly new here. I have downloaded alsa driver 1.0.20 tar.bz2 onto the desktop and am not sure what to do next. I have an aspire one D150 that has the mic which does not work. I am using UNR 9.04 and wish to install the latest Alsa driver to see if I can get the mic to work. How do I backup the current drivers and install the newly downloaded drivers? And just in case i need to, how do I reinstall the original drivers? I found some instructions to compile it with ./configure --with-cards=all but I am not sure what this means.

Thanks

---

### Post by kerry_s on 2009-05-28
you don't need to compile it.
in the terminal:
**sudo apt-get install alsa-base alsa-utils**
or
use synaptic to install it from the repo.

make sure you run "alsamixer" crank up all the volumes and unmute, use the "m" button to umute, it should be green.

---

### Post by khelben1979 on 2009-05-28
[ALSA Quick install]("http://alsa.opensrc.org/index.php/Quick_Install") in case you want to do it anyway.

---

### Post by rreyes3000 on 2009-05-28
I tried to use the command and this is what I get.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Should I downgrade to a different driver to get the mic to work? What other suggestions might you have?

---

### Post by kerry_s on 2009-05-28
> **rreyes3000 said:**
> I tried to use the command and this is what I get.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Should I downgrade to a different driver to get the mic to work? What other suggestions might you have?

did you run alsamixer and unmute everything? the mic is always muted as default.

---

