---
title: "Hardware RAID5 Not Mounting on Boot"
date: 2011-05-22
forum: Hardware
---

### Post by pjorge1036 on 2011-05-22
Hello, I'm running 10.10 64 on my home desktop and decided to upgrade my Motherboard and to ad a RAID 5 array with a RAID controller card, After which my computer would not boot and I would get an 'errno=5'. I pinpointed the problem to the RAID array, once I disconnected it from the MOBO the computer booted. after booting the system i reconnected the array and it was recognized. I transfered the files to it and everything seemed fine until I rebooted. Now the System takes forever to boot and if I don't disconnect the SATA cable from the controller and reconnect it again after the reboot the array doesn't show up in my computer.

My System Specs are:
Motherboard - Asus M4A87TD EVO
Processor - AMD Phenom ii x4 965
Boot Disk - 128GB  Kingston SNV425S
RAID Controller - Addonics AD5HPMSXA
Disk Array - 3- 1 TB Hitachi Deskstar 7k1000.C
in a RAID 5 configuration.
Any help will be apreciated

---

### Post by pjorge1036 on 2011-05-27
Well, after 5 days trying to fix this, I finally decided to reformat the volume and make the partition type; Linux LVM Partition and now The volume appears listed under Computer as: 2.0 TB Hard Disk: Media Files when I reboot and Ubuntu boots in less than 15 secs again!

---

