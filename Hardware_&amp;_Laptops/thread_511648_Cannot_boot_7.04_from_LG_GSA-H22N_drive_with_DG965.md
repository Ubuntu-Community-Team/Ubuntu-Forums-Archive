---
title: "Cannot boot 7.04 from LG GSA-H22N drive with DG965ss mainboard"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by rleon on 2007-07-28
I have a DG965ss mainboard and LG GSA-H22N dvd rewriter. Installation begins but when Ubuntu checks the files it freezes due to errors. I have tried Ubuntu Live CD, and the alternate version of both  Ubuntu and Kubuntu. This particular drive behaves perfectly under Windows XP and I have run several tests to check it,  burned some slipstreamed XP iso´s and installed Windows without problem, and I also surface checked the Ubuntu cd. I swaped the drive temporarily  with a different model LG rewriter and at least it didn´t have problems with the files on the disc. Does Ubuntu 7.04 still have problems with this chipset and its particular PATA adapter?.  Could this be an issue related to the jmicron PATA driver used by the motherboard?. Has somebody used this drive with an intel P965 chipset?

---

### Post by rleon on 2007-07-28
I have now been able to load from Live CD using the boot option: all_generic_ide. This works under all the bios setup options that  this mainboard allows: IDE as LEGACY, IDE as NATIVE plus SATA as IDE,  and AHCI. But choosing AHCI makes CD access very, very slow.
Somewhere I found the option generic.all_generic_ide, but this does not work with the kernel that comes with Feisty. 
My previously burned CD-ROMS still do not work. I will try now with regular CD-R disks.
Why is the CD access so slow using AHCI?. Could this be corrected later once Ubuntu is installed?

---

