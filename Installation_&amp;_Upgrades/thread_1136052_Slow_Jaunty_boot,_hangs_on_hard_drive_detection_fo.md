---
title: "Slow Jaunty boot, hangs on hard drive detection for 1 minute"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by dkulchenko on 2009-04-24
I was searching the 'Net for a drive issue with Jaunty, and found this entry in a thread (by SamiD) in the Jaunty Testing Forum:

[INDENT]Hello,

I just upgrated form 8.10 to 9.04 beta....

During boot, The new kernel 2.6.28-11-generic takes nearly one minute to detect my sata hard drive. At the end, the system seems to work properly.

Looking in boot message (dmesg), I find some errors :
"ata1: link online but device misclassified, retrying"

This is new, previous kenel 2.6.27 and 2.6.26 worked fine ( hardy, installed on another disk partition, is still working perfectly )

I have seen that this kernel initialize now sata drives before IDE drives. I thought that my problem was related to this timing and tried to add the boot option rootdelay=90 in grub, but this has no effect.

The output of dmesg and some info on my hardware are given below

My questions :
- is it a bug in the kernel ?
( shall I submit it by another mean that this simple post ? )
- what can I try ?
Thanks for help


Extract of dmesg output :

[ 1.691932] ata1: SATA max UDMA/133 cmd 0xe880 ctl 0xe800 bmdma 0xe080 irq 17
[ 2.008081] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2.008091] ata1: link online but device misclassified, retrying
[ 2.008095] ata1: reset failed (errno=-11), retrying in 10 secs
[ 12.008078] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 12.008087] ata1: link online but device misclassified, retrying
[ 12.008090] ata1: reset failed (errno=-11), retrying in 10 secs
[ 22.008077] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 22.008087] ata1: link online but device misclassified, retrying
[ 22.008090] ata1: reset failed (errno=-11), retrying in 35 secs
[ 56.688022] ata1: limiting SATA link speed to 1.5 Gbps
[ 57.008077] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 57.008087] ata1: link online but device misclassified, device detection might fail
[ 57.016348] ata1.00: ATA-7: WDC WD2500JS-55NCB1, 10.02E01, max UDMA/133
[ 57.016352] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[ 57.024371] ata1.00: configured for UDMA/133

my hardware :
- pc model : Fujitsu Siemens scaleo
- processor : Intel Pentium 4 516, 2933 MHz (22 x 133)
- mother board : ASUS P5SD1-FM2 (chipset SiS 649 )
Disk :
- 2 IDE drives : DVD reader and burner
- 1 sata hard drive : Western digital WDC WD2500JS-55NCB1 (232 Go)[/INDENT]

My problem is almost verbatim to that problem. Anyone have any solution?

---

### Post by dkulchenko on 2009-04-27
bump

---

### Post by brunolabs on 2009-05-03
Same problem here:

[URL="http://ubuntuforums.org/showthread.php?p=7204577"]
http://ubuntuforums.org/showthread.php?p=7204577[/URL]

---

