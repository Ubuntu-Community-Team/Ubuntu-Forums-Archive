---
title: "SATA error - &quot;spurious completions during NCQ&quot;/&quot;NCQ disabled due to excessive errors&quot;"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by flowbot on 2007-08-07
I've got a new Inspiron 1420 from Dell. I've noticed the following message in dmesg quite regularly:

```

[ 3865.592000] ata1.00: exception Emask 0x2 SAct 0x24 SErr 0x0 action 0x2 frozen
[ 3865.592000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x24 FIS=005040a1:00000010)
[ 3865.592000] ata1.00: cmd 60/68:10:c1:81:a9/00:00:0a:00:00/40 tag 2 cdb 0x0 data 53248 in
[ 3865.592000]          res 50/00:20:29:82:a9/00:00:0a:00:00/40 Emask 0x2 (HSM violation)
[ 3865.592000] ata1.00: cmd 60/20:28:29:82:a9/00:00:0a:00:00/40 tag 5 cdb 0x0 data 16384 in
[ 3865.592000]          res 50/00:20:29:82:a9/00:00:0a:00:00/40 Emask 0x2 (HSM violation)
[ 3865.904000] ata1: soft resetting port
[ 3866.076000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3866.076000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[ 3866.076000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[ 3866.076000] ata1.00: configured for UDMA/100
[ 3866.076000] ata1: EH complete
[ 3866.076000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[ 3866.076000] sda: Write Protect is off
[ 3866.076000] sda: Mode Sense: 00 3a 00 00
[ 3866.076000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

and going back into dmesg, i notice it now says:

```

NCQ disabled due to excessive errors

```

Is this a problem with SATA? I've got a Hitachi HTS54161 120GB HDD.

In the BIOS, I notice there are two modes to run the HDD in: ATA or AHCI ... when i switched to ATA, the errors don't seem to occur, but it also says that changing between the two modes may result in needing to re-install the OS. What do the two modes mean, and would they be related to my errors?

I'm running latest Feisty generic kernel. Any help/info greatly appreciated.

---

### Post by flowbot on 2007-08-11
*bump*

---

### Post by IamAcoconut on 2007-10-06
Here's what my dmesg says about HDD:```
[  447.660000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  447.660000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[  447.660000]          res 58/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[  447.660000] ata2: soft resetting port
[  448.308000] ata2.00: configured for UDMA/33
[  448.308000] ata2: EH complete
[  609.808000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  609.808000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[  609.808000]          res 58/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[  609.808000] ata2: soft resetting port
[  610.456000] ata2.00: configured for UDMA/33
[  610.456000] ata2: EH complete
[  849.992000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  849.992000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[  849.992000]          res 58/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[  849.992000] ata2: soft resetting port
[  850.640000] ata2.00: configured for UDMA/33
[  850.640000] ata2: EH complete
[  960.064000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  960.064000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[  960.064000]          res 58/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[  960.064000] ata2: soft resetting port
[  960.708000] ata2.00: configured for UDMA/33
[  960.708000] ata2: EH complete

```
I'm running Feisty too, my kernel is   2.6.20-16-generic.

I don't know answers to your questions, but maybe this **HSM violation** is something important. What does it mean?

My system starts to lag and crash to death when I run several apps at once, which hadn't been happening before...

---

