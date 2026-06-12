---
title: "ATA exceptions in syslog"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by gwi on 2007-06-29
What do these ata exceptions mean? They occurred at least a dozen times in a few hours. What is wrong?

```
Jun 27 19:56:34 kernel: [   57.616000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x1800000 action 0x2 frozen
Jun 27 19:56:34 kernel: [   57.616000] ata1.00: cmd c8/00:08:ac:b7:42/00:00:00:00:00/e1 tag 0 cdb 0x0 data 4096 in
Jun 27 19:56:34 kernel: [   57.616000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 27 19:56:34 kernel: [   64.932000] ata1: port is slow to respond, please be patient (Status 0xd0)
Jun 27 19:56:34 kernel: [   87.948000] ata1: port failed to respond (30 secs, Status 0xd0)
Jun 27 19:56:34 kernel: [   87.948000] ata1: soft resetting port
Jun 27 19:56:34 kernel: [   88.104000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 27 19:56:34 kernel: [   88.120000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Jun 27 19:56:34 kernel: [   88.128000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Jun 27 19:56:34 kernel: [   88.128000] ata1.00: configured for UDMA/133
Jun 27 19:56:34 kernel: [   88.128000] ata1: EH complete

```
```
Jun 27 19:56:39 kernel: [  132.296000] ata1.00: limiting speed to UDMA/100:PIO4
Jun 27 19:56:39 kernel: [  132.296000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Jun 27 19:56:39 kernel: [  132.296000] ata1.00: (BMDMA stat 0x24)
Jun 27 19:56:39 kernel: [  132.296000] ata1.00: cmd ca/00:08:4f:a1:77/00:00:00:00:00/e6 tag 0 cdb 0x0 data 4096 out
Jun 27 19:56:39 kernel: [  132.296000]          res 51/84:00:06:00:00/84:03:06:00:00/e6 Emask 0x10 (ATA bus error)
Jun 27 19:56:39 kernel: [  132.608000] ata1: soft resetting port
Jun 27 19:56:39 kernel: [  132.764000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 27 19:56:39 kernel: [  132.788000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Jun 27 19:56:39 kernel: [  132.796000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Jun 27 19:56:39 kernel: [  132.796000] ata1.00: configured for UDMA/100
Jun 27 19:56:39 kernel: [  132.796000] ata1: EH complete

```

When I tried to log in, I could not because the home partition could not be found. I pressed the reset button, Grub tried to load Ubuntu, but instead showed the message "inconsistent file system". I pressed the reset button again, and in the Grub menu chose Windows XP. WIndows would not boot either (without showing messages did not get past the first boot logo screen). After turning the system off and on, Ubuntu would boot again.

Extra information:
I had problems with random freezes with my system, after replacing my harddisk. Harddisk was then replaced by another one (of the same type). Problems continued. I bought another motherboard, CPU and memory. And now I have the problems described above. Random freezes also occured in Windows XP. Only common factors: the new harddisk (Western Digital WD5000AAKS), and the fact that Grub loaded the OS. The disk is not causing problems when the system is booted off another disk (the Ubuntu live CD).
Everytime I switched back to the previous (smaller) Seagate disk, the problems disappeared.

---

