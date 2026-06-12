---
title: "bus error on dpkg configure.....help"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by chad4321 on 2009-04-20
i am pretty new to ubuntu, trying to update i am getting:


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

when i run 'sudo dpkg --configure -a' this is what i get:


Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Bus error
Bus error
Bus error
Bus error
Bus error
Bus error
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: subprocess post-installation script returned error exit status 1


need help

---

### Post by frmdstryr on 2009-06-25
+1 mine does this too, i can't install or upgrade anything. 


$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-3-rt
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.28-3-rt
dpkg: subprocess post-installation script returned error exit status 1

---

