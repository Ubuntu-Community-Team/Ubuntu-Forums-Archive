---
title: "Problem installing Ubuntu 17.10 on M.2 Samsung 960"
date: 2017-12-05
forum: Hardware
---

### Post by ckotan on 2017-12-05
Has ANYONE gotten an M.2 on a NUC system to build a Ubuntu ONLY system?

I've tried everything I can think of and searched the forums.

I have a new INTEL NUC 7i7, 32GB RAM, and 250GB M.2 Samsung NVMe 960 drive.

I have tried EUFI and Legacy installs, including using GParted to create an EFI system partition and a root partition on the M.2 drive.

I'm fairly well convinced that M.2 is useless as non-Windose boot drive.  I can return it to Amazon, but I'd like it to work.

/dev/nvme0n1p1 EFI System Partition Fat32 512MiB 1.02MiB used rest free flags: boot, ESP
/dev/nvme0n1p2 ext4 mounted as /target or / 232MiB 10.04GiB used rest free no flags

Of course, I cannot even load Screenshot to /cdrom, let alone boot-repair. I tried a boot-repair boot cd, but I suspect it is some old version of Linux that won't repair an M.2.  

Any help appreciated

---

### Post by oldfred on 2017-12-05
Nuc seems to require another setting.

 intel nuc - nuc5i5MYHE w/M.2 SSD 
[https://ubuntuforums.org/showthread.php?t=2376245](https://ubuntuforums.org/showthread.php?t=2376245)
boot into the EFI shell and manually point startup.nsh to the grubx64.cfg and run it
Running The Intel NUC6i7KYK On Linux With Skylake Iris Pro Graphics 16.10
[http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1)

---

### Post by ckotan on 2017-12-05
"[COLOR=#000000]manually point startup.nsh to the grubx64.cfg and run it[/COLOR]"

I can get into the EFI shell. From there I'm lost.  Startup.nsh and grub64.cfg are on the Ubuntu-17.10 flash drive?  I do this before I install, or after? In EUFI or Legacy mode?  Finally, how do I point the .nsh at the .cfg? And how do I run it?

---

### Post by oldfred on 2017-12-05
I assume that is somewhere in the NUC's UEFI. Do not know NUC and its details. The shell is mostly Intel, so would think it is part of the NUC.

But if not. More info on shell.
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[https://bbs.archlinux.org/viewtopic.php?id=168548](https://bbs.archlinux.org/viewtopic.php?id=168548)

While discussing Windows says he had to enable shell from UEFI.
[http://siwike.blogspot.com/2017/05/skull-canyon-nuc-uefi-install.html](http://siwike.blogspot.com/2017/05/skull-canyon-nuc-uefi-install.html)

---

### Post by ckotan on 2017-12-09
Tnx, OldFred - Something evil about this NUC EUFI stuff, M.2, and Ubuntu. Never got a 17.10 install to complete and allow boot from the M.2 drive.  Probably 50 or more tries of many variatoins.  

I had an old SSD with Ubuntu 14 from a ThinkPad I gave away.  I popped that into the NUC SSD slot and it booted right away. Ran Sofware Upgrade to 17.04, and it's working. Read of the 120GB Muskin SSD is same as the Samsung 960 M.2, but write is much slower, so I'll get a new Samsung SSD and clone it off this Mushkin. Now just need to decide what VM stuff to use on Ubuntu. I've used VMware a good bit, and Virtual Box a few times.  Need to look into cost of VMware and other options. I'll flush the M.2 and see what to use it for.  If I put Win on this machine it will be a VM.

Again, Thanks!

---

