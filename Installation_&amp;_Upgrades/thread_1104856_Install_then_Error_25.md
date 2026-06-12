---
title: "Install then Error 25"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by hmc on 2009-03-24
I have two hard disks:
HD 1 - Windows 
HD 2 - Empty

- Booted Ubuntu Live CD 8.1
- Installed Ubuntu
- It told me to remove CD and reboot
- Got an error
GRUB loading, please wait...
Error25

I tried a old help thread something like
-open terminal
-sudo grub
-find something
-root (hd1,0)
-setup (hd0)
-quit

No change, still gives me the error.

---

### Post by hmc on 2009-03-24
Motherboard is a Gigabyte EP45-DS3L

HD 1 is Sata
HD 2 is IDE

I tried making it boot first from the IDE drive, but it fails and just boots the windows drive.

---

### Post by hmc on 2009-03-24
Installed EasyBCD, added linux boot systems, failed.

Added neogrub, so I managed to start grub.

Tried:
hd(1,0) - Disk read error
hd(1,1) - Disk read error
hd(1,2) - Disk read error
hd(0,1) - NTFS partition

---

