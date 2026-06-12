---
title: "SCSI config help needed"
date: 2020-06-18
forum: Hardware
---

### Post by 21Jerry on 2020-06-18
Hello,

I have two tape drives attached to a DL380 running Ubuntu Server 16.04, soon to be 18.04.  Both tape drives have uncompressed throughput of 288GB per hour or 80MB a second.  One is SAS attached and the other should be U160 according to doc I have.  The U160 drive is barely getting 35MB per second using a DD test of /dev/zero with compression off.

I noticed on the bottom of the following the device is set to FAST-20 SCSI 40.0 MB/s.  This looks incorrect.  Is the driver getting that value from the device? The card is configured for that device to be U320 and DSIK mode is off. Is there a config setting?  Driver issue?  I have another driver from HP for the SCSI adapter which is an UP U320E.  I haven't figured out how to install it after spending a few hours but before I dig in further, I thought I would check here.

Thanks 

Jerry

lspci | grep  "ATTO"
16:04.0 SCSI storage controller: ATTO Technology, Inc. Ultra320 SCSI Host Adapter (rev 08)
16:04.1 SCSI storage controller: ATTO Technology, Inc. Ultra320 SCSI Host Adapter (rev 08)

dmesg | grep "SCSI"

[    0.489760] SCSI subsystem initialized
[    1.030140] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    5.448317] hpsa 0000:05:00.0: scsi 4:0:8:0: added Sequential-Access HP       Ultrium 4-SCSI   tape SSDSmartPathCap- En- Exp=1
[    5.461272] scsi 4:0:1:0: Sequential-Access HP       Ultrium 4-SCSI   U64D PQ: 0 ANSI: 5
[    6.369026] scsi 3:0:0:0: Sequential-Access HP       Ultrium 4-SCSI   W51U PQ: 0 ANSI: 5
[    6.380289] scsi target3:0:0: FAST-20 WIDE SCSI 40.0 MB/s ST (50 ns, offset 64) <------------  is this a config option?

---

