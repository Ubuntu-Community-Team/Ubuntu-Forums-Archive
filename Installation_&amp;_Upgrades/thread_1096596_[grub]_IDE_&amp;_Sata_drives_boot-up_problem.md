---
title: "[grub] IDE &amp; Sata drives boot-up problem"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by nightclaw on 2009-03-15
Hi,
what i had: 2 sata harddrives 250 gb each, 
drive1 NTFS winXP with grub bootable
drive2 ext3&swap ubuntu8.04 64bit

everything working fine grub showing all ubuntu kernels and windows

what i did: plugging old IDE disks into the system:
drive3 ext3&swap ubuntu8.10 server 32 bit with grub bootable
drive4 ext3 data partition

now i can boot into the grub on drive3 and ubuntu server
when i try to mount drive2 the following error occurs:
mount: unknown filesystem type 'nvidia_raid_member'

when i connect any IDE drives the system doesn't boot from the sata disks any longer: GRUB Error 17.
searching google led me to some pages suggesting that grub has problems with mixed setups SATA&IDE


any help appreciated
thx,
Sebastian

fdisk -l:
Disk /dev/sda:
/dev/sda1 * Linux
/dev/sda2 Extended
/dev/sda5 Linux swap /solaris

Disk: dev/sdb:
/dev/sdb1 Linux

Disk: /dev/sdc:
/dev/sdb1 Linux

disk: /dev/sdc:
/dev/sdc1 * HPFS/NTFS

Disk: /dev/sdd
/dev/sdd1 Linux
/dev/sdd2 Extended
/dev/sdd5 Linux swap/ solaris

when i disconnect any of the 2 sata drives the boot results in "disk boot failure. insert system disks..."
i'm totally confused by now.
with the sata disks connected it boot from the grub on IDE drive
without sata it doesn't boot at all.

---

