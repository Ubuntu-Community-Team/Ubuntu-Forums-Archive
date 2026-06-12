---
title: "Strange hard disk spin down problem on HP nx7400"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by Vova.k on 2006-12-16
Hello All !

I'm trying to enable hard disk power saving on my nx7400 laptop. I've enabled laptop_mode (cat /proc/sys/vm/laptop_mode gives "2"), but HD was not spinning down. I've tried to enable in manually:
```
hdparm -B1 /dev/sda
hdparm -S1 /dev/sda
```
- still no result (I can hear my HD and hdparm -C gives "active/idle"). Then I've tried:
```
hdparm -y /dev/sda
```
- still no result. But when I've typed
```
hdparm -Y /dev/sda
```
my HD had stopped ! Then it remained inaccessible for a while (10 seconds or so, even hdparm -C had frozen) but after it my HD had woken up and started to suspend normally (by specified time-out) !

But when I turn off and on my laptop, HD is not spinning down again. It works only after hdparm -Y command !

This is part of my dmesg output after playing with hdparm:
```
[  307.984000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  307.984000] ata1.00: tag 0 cmd 0xca Emask 0x4 stat 0x40 err 0x0 (timeout)
[  308.296000] ata1: soft resetting port
[  308.468000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  308.472000] ata1.00: configured for UDMA/100
[  308.472000] ata1: EH complete
[  310.820000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[  310.832000] sda: Write Protect is off
[  310.832000] sda: Mode Sense: 00 3a 00 00
[  310.832000] SCSI device sda: drive cache: write back
```

According to smartctl my HD is FUJITSU MHV2080BH PL

Have someone any idea how to fix the problem permanently ? Thanks in advance.

---

