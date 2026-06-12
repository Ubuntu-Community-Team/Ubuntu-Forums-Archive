---
title: "where to install bootloader?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by BlocknBleed on 2009-05-13
Just got a new system with Vista preinstalled. I wanted a separate /boot partition but cannot put it at the start of the disk because vista is there. So I had a partition scheme with

 vista, /boot, /, /home, swap.
 
There is actually 2 vista partitions for some reason. The first is only 10Gb and I don't know what it's for.
The installation went fine but when I rebooted it just loaded straight into vista without even looking at grub.

My ultimate goal is to have Vista dual booted with ubuntu and at least one other OS. I have about 150Gb of free space to play with. 

Any suggestions?

---

### Post by Mark Phelps on 2009-05-13
My guess is that the other 10GB partition is a "recovery" partition or image that can be used to restore your PC to its original state.

If you want to use the Vista Bootloader to boot both Ubuntu and Vista, have a look at EasyBCD.  You can get that from the NeoSmart forums and they have How-to guides on installing it and using it.

---

