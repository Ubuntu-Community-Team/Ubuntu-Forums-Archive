---
title: "Can't boot without USB stick?"
date: 2008-11-20
forum: Hardware
---

### Post by gilgongo on 2008-11-20
I'm trying to install Hardy on a machine using a compact flash drive. For some reason, the IDE connection doesn't want to let me do this from the CD drive, so I installed the system from the net installer using a USB memory stick. 

All went well, but when I remove the USB stick, it get "no operating system found." When put the stick back in, the machine boots up OK.

I assume that the hardware is seeing the CF drive at least, but for some reason is not finding the boot partition, looking for it on the USB stick instead. 

Does anyone know what I need to do to get the machine to boot from the CF drive without the stick?

For the record, here's what I did to install from the stick:

wget [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz)

zcat boot.img.gz | sudo dd of=/dev/sdb

Inserted stick. Went in to BIOS setup, set it to boot from USB. Booted from the stick, did a command-line install of Hardy to the CF drive (no errors, all normal).

Removed the stick. Rebooted, went in to BIOS setup, changed the boot order back to normal, then see "no operating system found" on reboot.

Inserted the stick, rebooted, machine immediately boots to login prompt looking fine.

:confused:

---

