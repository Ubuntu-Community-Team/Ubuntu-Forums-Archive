---
title: "[SOLVED] Boot freezes"
date: 2008-11-07
forum: General Help
---

### Post by pokerbirch on 2008-11-07
I'm running Ubuntu 8.04 and have had this problem since installing it several months ago, which is my first taste of Linux...and i won't be returning to Windows any time soon. My problem is with the boot up freezing but i press ctrl-alt-del each time and after about 3 or 4 attempts, it usually boots up ok. I have edited menu.lst so that i get a full read out during boot up and the freeze up happens after:


> Nov  8 00:46:26 AMD-Linux kernel: [   28.291221] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A103 PQ: 0 ANSI: 5
Nov  8 00:46:26 AMD-Linux kernel: [   28.291267] scsi 6:0:0:0: Attached scsi generic sg3 type 5
Nov  8 00:46:26 AMD-Linux kernel: [   28.313941] Driver 'sr' needs updating - please use bus_type methods
Nov  8 00:46:26 AMD-Linux kernel: [   28.332476] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Nov  8 00:46:26 AMD-Linux kernel: [   28.332482] Uniform CD-ROM driver Revision: 3.20


On a GOOD boot, this is followed by:

> Nov  8 00:46:26 AMD-Linux kernel: [   28.393988]          res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  8 00:46:26 AMD-Linux kernel: [   28.394011] ata6: soft resetting link
Nov  8 00:46:26 AMD-Linux kernel: [   28.580455] ata6.00: configured for UDMA/66
Nov  8 00:46:26 AMD-Linux kernel: [   28.596461] ata6.01: configured for UDMA/66
Nov  8 00:46:26 AMD-Linux kernel: [   28.596469] ata6: EH complete
Nov  8 00:46:26 AMD-Linux kernel: [   28.602009]          res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  8 00:46:26 AMD-Linux kernel: [   28.602026] ata6: soft resetting link
Nov  8 00:46:26 AMD-Linux kernel: [   28.788340] ata6.00: configured for UDMA/66
Nov  8 00:46:26 AMD-Linux kernel: [   28.804460] ata6.01: configured for UDMA/66
Nov  8 00:46:26 AMD-Linux kernel: [   28.804464] ata6: EH complete
Nov  8 00:46:26 AMD-Linux kernel: [   28.810066]          res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  8 00:46:26 AMD-Linux kernel: [   28.810083] ata6: soft resetting link
Nov  8 00:46:26 AMD-Linux kernel: [   28.996245] ata6.00: configured for UDMA/66
Nov  8 00:46:26 AMD-Linux kernel: [   29.012230] ata6.01: configured for UDMA/66
Nov  8 00:46:26 AMD-Linux kernel: [   29.012235] ata6: EH complete
Nov  8 00:46:26 AMD-Linux kernel: [   29.018038] ata6.00: limiting speed to UDMA/33:PIO4
Nov  8 00:46:26 AMD-Linux kernel: [   29.018048]          res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  8 00:46:26 AMD-Linux kernel: [   29.018064] ata6: soft resetting link
Nov  8 00:46:26 AMD-Linux kernel: [   29.204231] ata6.00: configured for UDMA/33
Nov  8 00:46:26 AMD-Linux kernel: [   29.220102] ata6.01: configured for UDMA/66
Nov  8 00:46:26 AMD-Linux kernel: [   29.220107] ata6: EH complete


This is not my full boot info, i've only posted the section that seems relevent. I've been fiddling around with my BIOS settings but haven't had much joy. I've now reset the BIOS to default settings.

Any suggestions from more experienced users?

---

### Post by cariboo on 2008-11-07
Try adding :

```
acpi=noirq 
```

at the end of the kernel line behind quiet splash. To see if that helps.

Jim

---

### Post by pokerbirch on 2008-11-12
Thanks for the reply. I'm afraid it's still no go. Boot freezes in the same place, although it *appears* to be less frequent. I'm still tapping ctrl-alt-del a couple of times to get a clean boot.

I have some more information that may be of interest. Since resetting my BIOS to default settings, my PC reboots itself when i shut down. I had this problem about 2 years ago (on Windows XP) and pinned it down to a hardware problem. After a LOT of messing around, i managed to stop it via BIOS settings. Of course, i can't remember WHICH settings i changed but if i remember correctly, it was USB related.

---

### Post by pokerbirch on 2008-11-13
I've managed to sort the hardware problem which turned out to be a RAM related. I have an early AMD64 3000+ chip on a K8 board. Although my mother board is happy with my RAM (2Gb of Corsair 400Mhz), the CPU only likes 333 or less. So i've set the BIOS to a hard wired 333 bus speed and all is well.

Now back to the boot problem....any further suggestions? Where is the reference material to all the boot codes?

---

### Post by pokerbirch on 2008-11-14
Hmmmm, i'm quite surprised at the lack of responses. Have i asked a dumb-*** question or something? I'm quite new to Ubuntu and don't particularly want to return to Windows XP...:(

---

### Post by SoCalChris on 2008-11-14
The latest kernel seems to have some issues with power management when booting. I've got a problem where the computer freezes while booting, and won't continue booting unless a key is pressed.

I'd suggest checking [https://bugs.launchpad.net](https://bugs.launchpad.net) and seeing if someone has reported the bug. If not, go ahead and report it so that the developers will at least know about it, and will take a look at it.

---

### Post by l1nuxb0x on 2008-12-04
I'm no expert, let me say that right from the start, but it looks like your hard drive, or the hard drive controller is having problems

Looking at your dmesg, this part
> 
Nov 8 00:46:26 AMD-Linux kernel: [ 28.393988] res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov 8 00:46:26 AMD-Linux kernel: [ 28.394011] ata6: soft resetting link
Nov 8 00:46:26 AMD-Linux kernel: [ 28.580455] ata6.00: configured for UDMA/66
Nov 8 00:46:26 AMD-Linux kernel: [ 28.596461] ata6.01: configured for UDMA/66
Nov 8 00:46:26 AMD-Linux kernel: [ 28.596469] ata6: EH complete
Nov 8 00:46:26 AMD-Linux kernel: [ 28.602009] res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov 8 00:46:26 AMD-Linux kernel: [ 28.602026] ata6: soft resetting link
Nov 8 00:46:26 AMD-Linux kernel: [ 28.788340] ata6.00: configured for UDMA/66
Nov 8 00:46:26 AMD-Linux kernel: [ 28.804460] ata6.01: configured for UDMA/66
Nov 8 00:46:26 AMD-Linux kernel: [ 28.804464] ata6: EH complete
Nov 8 00:46:26 AMD-Linux kernel: [ 28.810066] res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov 8 00:46:26 AMD-Linux kernel: [ 28.810083] ata6: soft resetting link
Nov 8 00:46:26 AMD-Linux kernel: [ 28.996245] ata6.00: configured for UDMA/66
Nov 8 00:46:26 AMD-Linux kernel: [ 29.012230] ata6.01: configured for UDMA/66
Nov 8 00:46:26 AMD-Linux kernel: [ 29.012235] ata6: EH complete
**Nov 8 00:46:26 AMD-Linux kernel: [ 29.018038] ata6.00: limiting speed to UDMA/33:PIO4**
**Nov 8 00:46:26 AMD-Linux kernel: [ 29.018048] res 51/84:00:1f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)**
Nov 8 00:46:26 AMD-Linux kernel: [ 29.018064] ata6: soft resetting link
Nov 8 00:46:26 AMD-Linux kernel: [ 29.204231] ata6.00: configured for UDMA/33
Nov 8 00:46:26 AMD-Linux kernel: [ 29.220102] ata6.01: configured for UDMA/66
Nov 8 00:46:26 AMD-Linux kernel: [ 29.220107] ata6: EH complete 

it keeps coming up with an ATA bus error, and then it says it's limiting the speed to UDMA33/PIO, now pio is slower than dma

I googled and found a couple things that sound related, see if they help

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221677](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221677)
[http://ubuntuforums.org/showthread.php?t=598837](http://ubuntuforums.org/showthread.php?t=598837)

It seems in both of these links, the problem was fixed by replacing the cables, that's the first thing I would try

---

### Post by pokerbirch on 2008-12-18
For future reference:

My problem was due to a confirmed Kernel bug to do with certain VIA chips...which includes my oldish MSI K8 motherboard. I managed to (temporarily) get the pc to boot up without errors using:```
acpi=ht
```But i then had a problem with shutdown, where the process halted (which was more tolerable)

I have now wiped my main hard drive and installed Ubuntu 8.10 Intrepid with 2.6.27-9-generic kernel and have no problems so far.

---

