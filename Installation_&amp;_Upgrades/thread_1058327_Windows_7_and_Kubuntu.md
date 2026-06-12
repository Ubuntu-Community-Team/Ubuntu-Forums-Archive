---
title: "Windows 7 and Kubuntu"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by poetofzwan on 2009-02-02
Does anyone know how difficult it is to install Kubuntu on a system that has Windows 7 already installed?

I heard that the bootloader has been changed.

---

### Post by jimv on 2009-02-02
It doesn't matter what Windows 7's bootloader is.  Installing Kubuntu will replace it with the GRUB bootloader.

---

### Post by poetofzwan on 2009-02-03
> **jimv said:**
> It doesn't matter what Windows 7's bootloader is.  Installing Kubuntu will replace it with the GRUB bootloader.

Yeah I know grub is installed, but will Grub recognise my Windows 7 installation?

---

### Post by pirate_tux on 2009-02-03
> **poetofzwan said:**
> Yeah I know grub is installed, but will Grub recognise my Windows 7 installation?

Yes, it will recognise Microsoft crapware. Gnu/Linux is not Windows...

---

### Post by jimv on 2009-02-03
My mistake, I thought you wanted to install over Windows 7.  But yes, GRUB should see the Windows install and put an entry in the boot menu for it.

---

### Post by loveandequality on 2010-02-08
Try Wubi.

---

### Post by efflandt on 2010-02-08
Shrink Win7 partition with its own administration tools to free up some space.  Then install Ubuntu in the freed up space.

I always prefer creating my own partitions rather than letting automatic partitioning possibly do something unexpected (in the past, 64-bit WinXP beta changed my partition table geometry, and after I fixed that so it could boot, SuSE wanted to change it too, but I caught that before it did).

---

