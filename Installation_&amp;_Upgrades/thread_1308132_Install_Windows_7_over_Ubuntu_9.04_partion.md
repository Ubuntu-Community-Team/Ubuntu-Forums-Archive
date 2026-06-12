---
title: "Install Windows 7 over Ubuntu 9.04 partion?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by DemonDelight on 2009-10-31
How can i install Windows 7 over Ubuntu 9.04 while keeping the GRUB loader?

---

### Post by DemonDelight on 2009-10-31
Bump?

---

### Post by CalderCoalson on 2009-10-31
You mean you want Windows in one partition and Ubuntu in another?  If you've already made the partitions then just install Windows in the non-Ubuntu one and follow these instructions: [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

If you haven't, boot the a Live CD or GParted CD and resize/add partitions as needed, then follow above instructions.  Good luck!

---

### Post by Mark Phelps on 2009-10-31
> **DemonDelight said:**
> How can i install Windows 7 over Ubuntu 9.04 while keeping the GRUB loader?

If you mean you want to replace Ubuntu with Windows 7 but retain the GRUB loader -- you can't.

Windows 7 will automatically (1) overwrite the MBR, replacing the GRUB code there, and (2) install its own boot loader.

Unlike with Ubuntu, Windows 7 does not provide you a choice as to where to write its boot loader files.

---

