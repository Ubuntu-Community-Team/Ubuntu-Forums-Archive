---
title: "ubuntu 8.10 freezes (ACPI?), older versions work smoothly"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by hrabeX on 2008-12-18
After updating (update /  fresh install) to 8.10 my computer freezes time to time (cca 5-10 m in). Only LEDs on keyboard blinking (num + caps lock). After reseting sometimes ACPI shows warning, that gzip magic numbers couldn't be found followed by kernel panic error. This problem occurs during install also ( disk partitioning tool ). All older -buntu versions worked smoothly.

hardware configuration: nForce n570 chipsets, 2 SATA disks,  Athlon 64 X2, 2gigs RAM.

Any help is appreciated!

---

### Post by tommcd on 2008-12-18
To test if it is an acpi problem, boot up Ubuntu and press "e" at the entry for booting Ubuntu. This will take you to the grub entry for booting Ubuntu. Scroll down to the kernel line and press "e" again. This will allow you to pass boot options to the kernel. Type the options at the end of the kernel line. Also, remove the words "quiet" and "splash" from the kernel line so you can see the boot up messages. Then press enter, and then "b" to boot. This will not make any permanent changes to your grub configuration. Here are boot options to try, one at a time:
```
acpi=off
acpi=force
acpi=force pci=noacpi
noapic
nolapic
```
Also see this for boot options:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
If any of these fix your problem, then you can add edit /boot/grub/menu.lst and add the options to the grub menu so Ubuntu boots with those options all the time.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

