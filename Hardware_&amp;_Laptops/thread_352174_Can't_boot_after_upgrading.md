---
title: "Can't boot after upgrading"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by eschatron on 2007-02-03
I just got a new Dell Inspiron 1501 and loaded it with Kubuntu 6.10 32-bit version.  During installation I had the standard problem of having to boot with the pci=nomsi option, but after that the installation was smooth, hard drive and wifi were fine.

I used it with no problems for one day, including numerous successful reboots.  Then I upgraded all of my packages to the latest version (not proposed).  Since then I've been unable to boot.

It hangs just after fscking the partitions.  If I boot in recovery mode then I see that it's when initializing network devices.  I've tried with "acpi=force irqpoll", which changed nothing, and I've tried without pci=nomsi, which prevents the drive from being mounted at all. If I boot the live CD, I can mount my HDD, chroot, and use it just fine. 

Presumably this is a bug in the current packages, not a hardware problem, because it worked prior to the upgrade and the windows partition still boots fine.  The machine has a SATA HDD and Turion 64-bit dual core, if that helps.

---

