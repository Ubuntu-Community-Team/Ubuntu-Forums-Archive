---
title: "Second install step not happening....."
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by Scrufdog on 2006-01-02
So here is my system, in case it matters....

AMD64 3000+ @ 2501Mhz
2GB RAM (2x1024)
DFI LanParty nF4 SLi-DR with 6/23-3 BIOS
SATA1 = WD Raptor 74g, WinXP on first partition (60g)
           2nd Partition ext2 9.5g
           3rd Partition swap 512m
SATA2 = Maxtor 300g
SATA4 = WD Cavair 320g

Sound blaster Audigy 2 Platinum
BFG 6800 Ultra 256

Now, in WinXPSP2, under the logical drive controller its list the Cavair 320 (SATA4) as logical disk 0, the Raptor as logical disk 1, and the Maxtor as logical disk 2. Dunno if that matters for any of this.

Anyway, after downlaoding 5.10, i burned it and rebooted. Once I got to the partition manager, I set the ext2 partition to root mount point, and bootable, making it the primary boot sector, not winxp any more. After that it continued installing packages and such. i told it to install grub, then it asked me to restart.

I restarted and i got a operating system error when it tried to boot. I fired up a recovery cd, set winxp back to primary boot and rebooted into winxp just fine. I tried the ubuntu install again, did everything the same except i didnt specifiy that ext2 be bootable. It again installed grub, restarted, and went right into Winxp.

During this I have never actually seen anything of grub except when it installs it.

I am using the AMD64 5.10 package.

Any ideas what is going on?

.....
.....

Also as a side note, i cant get a network connection during the install process since my only internet connection is a Linksys WMP54GS v2 PCI card. Is that a problem, or will it be fine once I get this install to work?

---

