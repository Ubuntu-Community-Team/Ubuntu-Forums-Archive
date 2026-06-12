---
title: "HOWTO: Abit NF7 with SATA and raid-1"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by kkvenkit on 2005-09-08
Hi.

After multiple days of struggle I finally managed to get Ubuntu 5.04 installed on an Abit NF7 motherboard with some key partitions (/var and /tmp for example) on an SATA drive. Further, I have /home mirrored by raid-1 between the SATA drive and another IDE drive. To save others from the painful struggle here's how I did it.

The install seems to work fine because it's able to load the sata_sil module (driver for the SATA chipset on the Abit NF7) during boot. It does not need access to the SATA drive while booting (because it's booting off the cd) and hence everything works.

But after the install when you reboot (not from cd but from your new install) you'll find that Ubuntu can't find any partitions on the SATA drive. This is because /dev/sda* does not exist because the sata_sil module has not been loaded. When it drops you to the shell, however, it has finished loading the module and /dev/sda* magically appears. 

The underlying problem is that the sata_sil module is not getting loaded early enough. Adding libata, sata_sil, etc. to /etc/modules doesn't even get the modules loaded early enough.

So I had to add *modprobe sata_sil >/dev/null 2>&1* to near the start of /etc/rcS.d/S04udev. Recall that scripts in /etc/rcS.d/ are executed during system boot. 

This fixed my problem with access to the SATA drive. But I was still getting error about not being able to mount a raid-1 partition, which is mirrored on an IDE drive and the aforementioned SATA drive.

So I also added */etc/init.d/mdadm-raid start* to /etc/rcS.d/S04udev immediately below my new modprobe line. 

And finally my machine would boot, find the SATA drive and the raid-1 partitions, and finish the install.

---

