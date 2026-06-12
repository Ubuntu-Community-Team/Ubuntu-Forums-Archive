---
title: "Install Bootloader  To External HDD"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by Kemono on 2009-07-07
I have 2 hard drives - 1 internal and the other one is external. I'm using the internal one for Windows and the external one for Linux.

So far I've been disconnecting the internal hard drive in order to install Linux. Since I like messing with my computer and systems I'm getting tired of plugging and unplugging the hard drives.

I'm wondering if there's a way to install GRUB on my external HDD without disconnecting my internal HDD. Perhaps sometime during the installation?

---

### Post by ajgreeny on 2009-07-07
I think there is an Advanced button to hit at some point in the install to allow you to put grub somewhere else than on the disk 1 MBR, but can't remember where.

You can certainly do it later with the terminal, though you may need to edit the /boot/grub/device.map file to include the disk you want to put grub on to, and then with ubuntu running just run sudo grub-install /dev/sd#.  You will then need to restore the windows MBR which you can do with the win install CD or supergrub CD.  My machine is old enough to still have a floppy, and I always put a copy of grub on floppy disk for emergency purposes in exactly that way.

---

