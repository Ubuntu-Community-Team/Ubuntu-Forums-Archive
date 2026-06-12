---
title: "Seagate Momentus XT Hybrid Grub 2 Corruption"
date: 2011-10-15
forum: Hardware
---

### Post by errold32 on 2011-10-15
Ubuntu 10.04 LTS dual booted with Windows 7 pro x64 on a Seagate Momentus XT (SD28 firmware). I am spending a lot of time in windows, and every once in a while, when I reboot, Grub 2 fails to work. Usually my computer just restarts endlessly without showing the boot menu, but it has frozen at the bios screen. All problems are solved (untill the next time) by issuing the following command from a linux live cd

sudo grub-setup -d /media/XXXX/boot/grub /dev/sda
where XXX is the partition containing the ubuntu root

Please Help

Thanks

---

