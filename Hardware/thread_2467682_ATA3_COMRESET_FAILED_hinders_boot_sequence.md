---
title: "ATA3 COMRESET FAILED hinders boot sequence"
date: 2021-10-04
forum: Hardware
---

### Post by pj.connect on 2021-10-04
I'm running Ubuntu 20.04.3 LTS on an external drive

Two of my peripherals have died, namely the main hard drive, and the dvd/db drive. I had to contend with ATA2 COMRESET FAILED message at boot time for some time with no effect on boot sequences. But recently, the dvd/bd drive failed, and now I have an ATA3 COMRESET FAILED locking me most of the time in a boot/reboot sequence.

To solve this problem, I pass kernel parameters, namely "libata=2.0:disable,2.0:norst,3.0:disable,3.0:norst" in "/etc/default/grub" with an "update-grub". Now I can boot, but I get the ATA3 COMRESET FAILED at boot time, while in runtime, both in the logs, and at shutdown time, sometime on the screen, and most probably in the logs. I also tried without the ".0" to no avail.

I'm happy that I can boot without problems, but I though that the kernel parameters would not only _hide the peripherals_, but in doing so, _eliminate the need to comreset them_. Some have suggested that it might be the sata controller that is failing, but I have a SSD (ATA1.0) which is working fine. 

The laptop is broken at the base corner of the lid, so I fear the laptop will fall apart if I open it, thus I can't disconnect hard drive and dvd/db drive.

Any suggestions

---

