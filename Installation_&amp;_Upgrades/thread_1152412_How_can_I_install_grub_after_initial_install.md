---
title: "How can I install grub after initial install?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by CptanPanic on 2009-05-07
I installed ubuntu first on a secondary drive.  So now I want to make it standalone.  I checked synaptic and grub is installed, but I have no /boot/grub directory.  How do I get these files?  I am using 8.04
Thanks,
CP

---

### Post by logos34 on 2009-05-07
run this command with ubuntu on the secondary drive mounted:

# grub-install --root-directory=/media/sdb1 /dev/sdb

(replace '/media/sdb1' and 'sdb' with yours if diff.)

This will generate the grub files (incl. menu.lst) if they don't already exist and write grub IPL/stage1 to the MBR of drive sdb.  You can then boot ubuntu on the secondary drive directly through the Bios.

hope that helps

---

