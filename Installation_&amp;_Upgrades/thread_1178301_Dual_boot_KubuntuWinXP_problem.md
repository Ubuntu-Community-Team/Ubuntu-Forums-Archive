---
title: "Dual boot Kubuntu/WinXP problem"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2009-06-04
I have an AMD Phenom system set up to dual boot Kubuntu Jaunty 9.04 and WinXP. Kubuntu is on software RAID on two SATA disks /dev/sda and /dev/sdb and WinXP is on a partition on one of those disks - /dev/sad3. Boot choice is controlled thru GRUB, and this all worked fine for a while.

Kubuntu is fine, but suddenly WinXP stopped booting. Attempt at normal boot goes to WinXP boot screen, slider bar operates for a couple seconds, and the machine then reboots with no error message. Attempt at safe boot reaches MUP.sys, then reboots with no error message. When I attempt to recover using the WinXP install CD, the startup sequence is loading drivers when a BSOD occurs with error 0x0000007B, which is INACCESSIBLE_BOOT_DEVICE .

Immediately before the problem occurred, I had copied some files in Linux to the WinXP partition, and I suspect that the WinXP partition has somehow become corrupted. The WinXP still looks fine from Linux - ie. it seems to have the needed directories and files - but that's based on a quick look not an exhaustive check.

I tried running ntfsfix on the WinXP partition - it seemed to run successfully but it did not "make  Windows perform a thorough check next time it boots", which is what the docs say it's supposed to do.

Ideas to fix this appreciated - at this point I'm stumped

---

