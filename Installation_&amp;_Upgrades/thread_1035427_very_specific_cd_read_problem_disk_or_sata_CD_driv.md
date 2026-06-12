---
title: "very specific cd read problem: disk or sata CD drive?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by slackware_is_the_best on 2009-01-09
I am new to these forums but definitely not to linux. I have survived (albeit barely) through the hell that is installing gentoo and slackware. But this time I want to install linux in under an hour just for the purpose of temporary usage so i downloaded xubuntu. 

background: Built my computer a year ago, yesterday both hard drives in RAID0 went bad (BOTH started clicking lol) so now reinstalling on a spare 80GB with a **_SATA DVD Writer that i just got and haven't used for anything yet (except the xubuntu boot disk)_**<--key point

error: it DOES boot from the xubuntu disk, so the motherboard reads the sata DVD drive. however, once at main menu any option i click returns a "I/O Error: cannot read disk" with the only option to restart the computer.
the reason I am not just assuming its a bad disk is because EVEN WHEN I CLICK ON CHECK FOR ERRORS ON DISK, it doesn't say there's an error on disk, instead it says it cannot even read the disk in the first place. This leads me to believe that there may not be any sata drivers in the boot disk!!!! zomg! but its linux, surely the people who made the boot iso's are friggin smart. 

so what am i missing here? HALP!

---

### Post by lemming465 on 2009-01-10
> it says it cannot even read the disk in the first place. This leads me to believe that there may not be any sata drivers in the boot disk

I'm afraid you are probably right, and your particular SATA controller isn't supported.  The initial syslinux menu off the CD or DVD is loaded from the BIOS.  Once the bootloader turns things over to the kernel, the kernel+initrd need a native driver for the SATA controller and have to find the install media again to continue.

If you can use a different computer to convert the CD to a USB install on a flash drive, you could move the resulting bootable USB flash drive over to the computer with the problem.  It's also possible that you could find BIOS changes that would make the SATA controller visible.

Good luck with it.

---

