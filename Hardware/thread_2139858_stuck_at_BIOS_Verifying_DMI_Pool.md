---
title: "stuck at BIOS Verifying DMI Pool"
date: 2013-04-28
forum: Hardware
---

### Post by mmhalf3 on 2013-04-28
I am trying to use a PCI sata card with 4 ports to increase the number of disks for a zfs NAS in  an ubuntu 12.04 64bit install.  With disks attached to the PCI card the system won't complete the boot process, gets stuck at Verifying DMI Pool.  If the disks are powered down, and system reset the OS will complete a normal boot process.  Once in the OS, if the SATA disks get powered back up, the OS sees them just fine, and they can be used, but subsequent reboots have the same problem and don't finish.

I have tried reinstalling ubuntu 12.04, and the installation sees all the sata disks, and completes fine but on the reboot after completing installation, the boot sequence gets stuck at the same point.  Also tried installing on different disks, but no luck.   Don't think it is a driver issue, since a running Ubuntu system sees the disks just fine, been mucking with the BIOS settings, without any luck.  Any suggestions on how to get past this issue?


Thanks,

---

