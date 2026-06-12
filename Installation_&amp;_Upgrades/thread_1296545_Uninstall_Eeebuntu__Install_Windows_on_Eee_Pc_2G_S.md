---
title: "Uninstall Eeebuntu / Install Windows on Eee Pc 2G Surf"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by Satellite31 on 2009-10-20
Hello everyone!

I have just bought an Asus Eee PC 2G Surf. It came without OS.

I have installed on it Eeebuntu BASE 3.0, but I noticed that it occupied almost the entire capacity of my Eee PC (1.8 GB out of the total 2 GB).
That is way I want to replace Eeebuntu with a lighter version of Windows.

I have deleted with the partition manager of the Linux based OS, if I am right, the primary partition of Eeebuntu.

Currently I receive the GRUB Error 17, therefore I cannot use DOS to install Windows. Basically I do not have any operational OS on my Eee PC.

Could you please help me to resolve the GRUB Error 17, completely remove Eeebuntu and install for the first time, using a USB flash drive, Windows on this machine?

Thanks in advance!

---

### Post by mikewhatever on 2009-10-20
You get the GRUB error because the bootloader is looking for an OS, which you said you'd deleted. Just install Windows, DOS or whatever you want, and it will overwrite GRUB and everything else on the disk.

---

### Post by Satellite31 on 2009-10-21
Thanks for the reply, but finally I have solved the case using PeToUSB.

---

