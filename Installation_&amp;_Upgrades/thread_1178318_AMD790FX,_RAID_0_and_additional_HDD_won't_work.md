---
title: "AMD790FX, RAID 0 and additional HDD won't work?"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Eagle3386 on 2009-06-04
Hey guys,

it's been a while since I had my last contact with Linux..
But since my Vista Business x64 is mainly for gaming, I don't see any reason for not using the faster and more flexible (I _love_ the BASH and Compiz-Fusion! :D) Linux..

Because most companies here in Germany like to see "knowledge in Debian" over Ubuntu, I burned an ISO with Lenny 5.0 and tried to install it - but that failed:

First of all my setup:
+ Gigabyte GA-MA790FX-DS5 (F8A-BIOS)
-- AMD 790FX-chipset, i.e. RD790 and SB600 (Promise)
-- Gigabyte GSATA (JMicron JMB363 or JMB362, can't say for sure)
-- 2 Samsung HD501LJ (Firmware: CR100-13)
-- 1 additional HD501LJ (Firmware: CR100-10, not updatable, only -11/12 are)

+ RAID controller configuration
-- both CR100-13 are defined as RAID 0
-- single HDD is defined as JBOD

+ Partitions
-- RAID 0: 100/300/125/200/200/6 GB, all NTFS 5
-- single HDD: 100 GB in total (boot/root/home/usr/var/swap), all ext3; about 350 GB for a backup-partition (via Batch/BASH-scripts)

At first, I left that single hard disk attached to the JMicron controller, but doing so, resulted in GRUB and GRUB2 (which I'd prefer) not being able to write their stuff into RAID 0's MBR..

So I thought that it might be the installer and/or GRUB(2) which is/are not able to "cross-write" from one controller to another..

Hence, I attached the single drive to the Promise controller and ran the installer again, but the _only_ way to get Debian installed successfully was done by disconnecting the RAID and running the installer with only that single hard disk attached..

Unfortunately, this way the Kernel gets "confused" at boot-time, when the RAID isn't disconnect - though, Vista doesn't bother and just boots.. ;)

So, my problem is: how to get Debian running on a single HDD with a RAID 0 where Vista, games and all my music/videos/etc. is stored?

Thanks in advance,
 Martin..

---

