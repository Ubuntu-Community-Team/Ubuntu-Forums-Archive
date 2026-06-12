---
title: "I/O error on my CDROM drive"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by allanandr3w on 2008-03-16
i got this problem I/O error cannot copy file. but before that i encountere an error saying CDROM drive cannot be mount. did a reboot and the CDROM mounted ok, but then i encountered the I/O error.

tried also to insert another disc but same problem encountered.

this is my dmesg.

[ 1045.294643] sr 3:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1045.294650] sr 3:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1045.294658] end_request: I/O error, dev sr0, sector 85616
[ 1045.294663] Buffer I/O error on device sr0, logical block 21404
[ 1045.294673] Buffer I/O error on device sr0, logical block 21405
[ 1045.294682] Buffer I/O error on device sr0, logical block 21406
[ 1045.294689] Buffer I/O error on device sr0, logical block 21407
[ 1045.294696] Buffer I/O error on device sr0, logical block 21408
[ 1045.294702] Buffer I/O error on device sr0, logical block 21409
[ 1045.294708] Buffer I/O error on device sr0, logical block 21410
[ 1045.294714] Buffer I/O error on device sr0, logical block 21411
[ 1045.294721] Buffer I/O error on device sr0, logical block 21412
[ 1045.294727] Buffer I/O error on device sr0, logical block 21413
[ 1140.063534] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1140.063546] sr 3:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1140.063552] sr 3:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1140.063561] end_request: I/O error, dev sr0, sector 871892
[ 1140.063568] printk: 54 messages suppressed.
[ 1140.063573] Buffer I/O error on device sr0, logical block 217973
[ 1140.063584] Buffer I/O error on device sr0, logical block 217974
[ 1140.063591] Buffer I/O error on device sr0, logical block 217975
[ 1140.063598] Buffer I/O error on device sr0, logical block 217976
[ 1140.063604] Buffer I/O error on device sr0, logical block 217977
[ 1140.063611] Buffer I/O error on device sr0, logical block 217978
[ 1140.063617] Buffer I/O error on device sr0, logical block 217979
[ 1140.063623] Buffer I/O error on device sr0, logical block 217980
[ 1140.063629] Buffer I/O error on device sr0, logical block 217981
[ 1140.063635] Buffer I/O error on device sr0, logical block 217982
[ 1179.809659] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1179.809672] sr 3:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1179.809679] sr 3:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1179.809687] end_request: I/O error, dev sr0, sector 871120
[ 1179.809691] printk: 53 messages suppressed.
[ 1179.809694] Buffer I/O error on device sr0, logical block 217780
[ 1179.809704] Buffer I/O error on device sr0, logical block 217781
[ 1179.809713] Buffer I/O error on device sr0, logical block 217782
[ 1179.809720] Buffer I/O error on device sr0, logical block 217783
[ 1179.809727] Buffer I/O error on device sr0, logical block 217784
[ 1179.809733] Buffer I/O error on device sr0, logical block 217785
[ 1179.809740] Buffer I/O error on device sr0, logical block 217786
[ 1279.957881] UDF-fs: No VRS found
[ 1280.058064] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1280.059886] ISOFS: changing to secondary root
[ 1328.056272] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1328.056283] sr 3:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1328.056290] sr 3:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1328.056298] end_request: I/O error, dev sr0, sector 871120
[ 1328.056302] printk: 57 messages suppressed.
[ 1328.056308] Buffer I/O error on device sr0, logical block 217780
[ 1328.056317] Buffer I/O error on device sr0, logical block 217781
[ 1328.056327] Buffer I/O error on device sr0, logical block 217782
[ 1328.056333] Buffer I/O error on device sr0, logical block 217783
[ 1328.056340] Buffer I/O error on device sr0, logical block 217784
[ 1328.056347] Buffer I/O error on device sr0, logical block 217785
[ 1328.056353] Buffer I/O error on device sr0, logical block 217786
[ 1328.056360] Buffer I/O error on device sr0, logical block 217787
[ 1328.056366] Buffer I/O error on device sr0, logical block 217788
[ 1328.056396] Buffer I/O error on device sr0, logical block 217789
[ 1328.070089] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1328.070100] sr 3:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1328.070106] sr 3:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1328.070115] end_request: I/O error, dev sr0, sector 871632
[ 1328.152693] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1328.152703] sr 3:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1328.152710] sr 3:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1328.152718] end_request: I/O error, dev sr0, sector 871888

help me out guys, im a newbie!

---

### Post by Armaron on 2008-03-19
I have the same error, so basicly this is a bump to get a real answer on this question.

Btw, anybody know what device SR0 is?

---

### Post by KlausW on 2008-03-19
sr0 is the CD-Disk itself.
I have had the same problem. I updated from feisty fawn 7.04 to version 7.10, and then the problem was solved. I guess, that the Ultra-dma-Mode is to high, but you can not change this with hdparm, because its support not the new device-manager of feisty fawn.

You can try something, to manipulate the current system, but I wouldnt do this. I got a lot of problems with the tips there, but you can better understand the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636)

---

### Post by janfsd on 2008-05-24
I started getting this problem since I upgrade to Hardy. Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+bug/228624](https://bugs.launchpad.net/ubuntu/+bug/228624)
Please confirm the bug there, so maybe they can fix it.

Maybe the same bug:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/219628](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/219628)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)
[http://ubuntuforums.org/showthread.php?t=756200](http://ubuntuforums.org/showthread.php?t=756200)

*Possible* workarounds:
Using the kernel 2.6.24-12
Booting with irqpoll
**Booting with all_generic_ide=1**

I still didn't try any of those workarounds. But I will try them next time I make a reboot, and I will post here if something worked.

Using the all_generic_ide=1 parameter fixes the problem. Now i can see through hdparm that it detects well the drive speed (udma2), before it was appearing udma4, maybe this is why this problem generates.
Still didn't try the other workarouns.

---

### Post by uhappo on 2008-06-07
> **janfsd said:**
> I started getting this problem since I upgrade to Hardy. Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+bug/228624](https://bugs.launchpad.net/ubuntu/+bug/228624)
Please confirm the bug there, so maybe they can fix it.

Maybe the same bug:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/219628](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/219628)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)
[http://ubuntuforums.org/showthread.php?t=756200](http://ubuntuforums.org/showthread.php?t=756200)

*Possible* workarounds:
Using the kernel 2.6.24-12
Booting with irqpoll
**Booting with all_generic_ide=1**

I still didn't try any of those workarounds. But I will try them next time I make a reboot, and I will post here if something worked.

Using the all_generic_ide=1 parameter fixes the problem. Now i can see through hdparm that it detects well the drive speed (udma2), before it was appearing udma4, maybe this is why this problem generates.
Still didn't try the other workarouns.

Booting with all_generic_ide=1 solved my problem!!! Thanks alot!

---

### Post by janfsd on 2008-06-07
Glad to hear that. Please confirm the bug at launchpad if you can, so that the developers could look into the issue.

---

