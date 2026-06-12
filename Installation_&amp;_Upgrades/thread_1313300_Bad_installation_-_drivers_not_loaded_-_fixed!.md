---
title: "Bad installation - drivers not loaded - fixed!"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by psidrum on 2009-11-03
Here is how i fixed mine, 

my problems, after upgrading to 9.10, these things stopped working

Radeon x1600 drivers not loaded
SB X-Fi drivers not loaded
Compiz not working
new 9.10 kernel was not loaded

before you do anything first take a look if your system is using the new 9.10 (2.6.31) kernel, because the system will use the old kernel and label your system as karmic

When i upgraded i kept the old menu.lst, this prevented the new kernel from loading

if the kernel is using the old version, go to synaptic and download grub-pc

install it, then run it, reboot, this should load the new kernel,

after the new kernel was loaded, everything worked perfect, i just have ot turn on Visual Effects to get the Compiz working again,

even my SB X-Fi that did not have a driver in old kernel, started working perfectly,

Awesome!!

---

