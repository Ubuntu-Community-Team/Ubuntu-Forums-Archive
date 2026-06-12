---
title: "Setting up a dual boot on second HD."
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2009-04-27
I want to install Ubuntu on a second ubuntu only hard drive. 
my question is how would i set up the dual boot options.
I've only done this with 2 OSs on the same disk.
I would like it to be like that if possible...

---

### Post by SuperSonic4 on 2009-04-27
It depends what you want from grub.

**If you want total independence** with no interaction then remove the first drive, install ubuntu on the second and pick your favourite via the BIOS

**If you want grub on the second disk** then take out the first disk and install ubuntu onto the second. You can then edit the /boot/grub/menu.list to add in the first drive. Alterantively you can try and specify (hd1) during installation to put grub on the MBR of the second disk

**If you don't mind which disk grub is on** then go through as normal using the second drive

---

