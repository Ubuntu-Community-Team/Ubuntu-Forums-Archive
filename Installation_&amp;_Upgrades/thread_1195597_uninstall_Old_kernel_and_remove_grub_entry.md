---
title: "uninstall Old kernel and remove grub entry"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by sanumala on 2009-06-24
I have installed ubuntu 9.04 64 bit with the cd created 1 month back. Ubuntu update manager suggested new updatd and i have installed all suggested updates after clean install


In the update process kernel updated to newer version

sanumala@devone:~$ uname -r
2.6.28-13-generic

which was previously 11-generic.. 

I know i can comment grub.conf entries to don't show older kernel options while booting .

but how can i uninstall older kernels which I am not using and how can i reomove older kernel entries completly form grub??

Answers will get :popcorn: :D

---

### Post by merlinus on 2009-06-24
Use synaptic.  Search for the kernels you wish to remove, and grub's menu.lst will be automatically updated.

You can simply search for -11, and remove headers and image.

But be sure that -13 is working properly before doing this!

FWIW, I always keep two kernels.  When a new one is released, then I delete the oldest.  That way, should anything untoward occur, I can use the previous kernel and run ubuntu.

---

### Post by sanumala on 2009-06-24
> **merlinus said:**
> Use synaptic. Search for the kernels you wish to remove, and grub's menu.lst will be automatically updated.
 
You can simply search for -11, and remove headers and image.
 
But be sure that -13 is working properly before doing this!
 
FWIW, I always keep two kernels. When a new one is released, then I delete the oldest. That way, should anything untoward occur, I can use the previous kernel and run ubuntu.
 
Thankyou. then i will keep 2 kernels. :P

---

