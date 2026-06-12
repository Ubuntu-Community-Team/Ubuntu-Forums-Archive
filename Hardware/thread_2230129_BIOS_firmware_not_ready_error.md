---
title: "BIOS firmware not ready error"
date: 2014-06-17
forum: Hardware
---

### Post by rwohlhueter on 2014-06-17
**Hardware/OS:** Ubuntu 13.10, AMD64 bit, on ASUS motherboard M4A79T, with NVIDA GTX 660Ti grapics, Ubuntu boot disk is SATA port1; MSWinXP_x64 boot on PATA port 1

**Offending action:**  In an attempt to get a molecular graphics program working, I installed the newest GTX660Ti driver (v.331.67) directly from NVIDIA (replacing the version offered by Cannonical, 319.76) Prior to that everything -- the exception of the molecular graphics program was working fine.

**Consequence:**  Upon reboot, already at the BIOS level, I get "Please wait for IDE scan......Error! Firmware not ready."  Even so, I am then offered various boot options, cluding linux, linux-recovery and WinXP (?implies GRUB functioning OK).  Selecting linux, linux-recovery, or even Clonzilla-Live CD, I can't boot -- neither with graphic interface nor command-line.  Lot's of messages fly by on screen, but then hangs. And, specifically, I can't get to the "repair broken packages" module.

I would be inclined to take the firmware message to heart, except that, when a choose to boot WinXP, not only does it boot up properly, but I can mount (via "Ext2Fsd") and read without problem the SATA disk on with linux resides.  Thus, it would seem that firmware and disk are perfectly functional from WinXP side.  

Thus the "firmware error" seems to be some mirage due to the NVIDIA software installation.  But I'm totally lost to know what.

Any hints, wisdom, advice, solutions out there?

Bob Wohlhueter

---

