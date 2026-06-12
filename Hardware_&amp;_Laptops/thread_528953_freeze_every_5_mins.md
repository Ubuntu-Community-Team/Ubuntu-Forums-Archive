---
title: "freeze every 5 mins"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by michal_c on 2007-08-18
hey, i just installed a fresh copy of feisty 32bit on my asus z35f laptop, and now it freezes every 5 mins - for about 10 sec's, and then continues normally, i think it's somthing to do with the dvd because this is the "dmesg" output:

```
[ 3391.956000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3391.956000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[ 3391.956000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 3398.968000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 3421.984000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 3421.984000] ata1: soft resetting port
[ 3422.336000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[ 3422.348000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[ 3422.348000] ata1.00: configured for UDMA/100
[ 3422.528000] ata1.01: configured for UDMA/33
[ 3422.528000] ata1: EH complete
[ 3422.544000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 3422.560000] sda: Write Protect is off
[ 3422.560000] sda: Mode Sense: 00 3a 00 00
[ 3422.576000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3422.592000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 3422.592000] sda: Write Protect is off
[ 3422.592000] sda: Mode Sense: 00 3a 00 00
[ 3422.628000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
michal@michal-laptop:~$ 
```

please help :(

---

### Post by fredj on 2007-08-19
It probably is to do with the DVD. Try to obtain updated firmware for your DVD drive.
At regular intervals Ubuntu interrogates the DVD drive and if it doesn't receive a suitable
reply it repeats the request until a timeout expires. This has the unfortunate effect of causing
the freeze you are experiencing.

---

### Post by adam_r on 2007-08-19
how do i update the firmware?

---

