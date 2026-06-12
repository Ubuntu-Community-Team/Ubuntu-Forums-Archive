---
title: "Upgrade from x86 to x64"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by Zerocool3001 on 2009-07-14
I just noticed (or maybe remembered) that the system on which I've been running Ubuntu 9.04 is a 64 bit processor. I've gone through several versions of Ubuntu on this machine and, having forgotten, I've always left them x86. Before it didn't really matter, but now that I've been using the machine for Video transcoding operations, I assume using 64-bit software would give me a significant boost. Am I right about this and is there any way to upgrade from x86 to x64 without reinstalling (possibly when 9.10 is released) or having a bunch of redundant files. I don't want to have to go back through and redownload and setup all the software I've installed over the years.

Any help would be much appreciated.

---

### Post by jerome1232 on 2009-07-14
Unfortunately the only way to change from x86 to x86_64 is to reinstall.

---

### Post by drs305 on 2009-07-14
You have to reinstall to change from 32 to 64-bit. 

There are a few things you can do to ease the transition. You can use the same /home if you put it on a separate partition and if you make a list of your current apps via dpkg or Synaptic, File, Save Markings you can import them into your new install.

---

### Post by Zerocool3001 on 2009-07-14
> **drs305 said:**
> You can use the same /home if you put it on a separate partition and if you make a list of your current apps via dpkg or Synaptic, File, Save Markings you can import them into your new install.

I take it there's no easy way to poll non-deb installed files (i.e. files installed from source) and non-user custom settings.

---

