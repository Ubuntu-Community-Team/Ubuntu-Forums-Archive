---
title: "ubuntu 9.10 not detecting sata"
date: 2009-12-21
forum: Hardware
---

### Post by aaronwater on 2009-12-21
I've installed a new 500GB SATA drive in my AMD64 computer and want to install ubuntu 9.10 from a flash drive (which I'm running now to post this).  fdisk can't detect the SATA drive:

```

Disk /dev/sde: 8009 MB, 8009023488 bytes
247 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Disk identifier: 0x000ccc3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        1021     7817766    c  W95 FAT32 (LBA)

```

Only the live flash drive.

Before we start suggesting its a BIOS configuration problem, I did install PCBSD on the drive to confirm that it works.  But PCBSD has a serious issue with Xorg not getting the screen resolution right.  Ubuntu resolution is a perfect 1680x1050 and thats what I need.

The dmesg from ubuntu live startup for the drive is:

```

[    0.172548] libata version 3.00 loaded.
[    1.639052] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 26
[    1.639056] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 26
[    1.639059] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 26
[    1.639062] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 26
[    1.639610] pata_via 0000:00:0f.1: version 0.3.4
[    1.639786] scsi4 : pata_via
[    1.639873] scsi5 : pata_via
[    1.641079] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.641081] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.980020] ata2: SATA link down (SStatus 0 SControl 300)
[    1.980037] ata3: SATA link down (SStatus 0 SControl 300)
[    1.990018] ata4: SATA link down (SStatus 0 SControl 300)
[    2.160018] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.160017] ata1.00: qc timeout (cmd 0xec)
[    7.160024] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[    7.690017] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   17.690011] ata1.00: qc timeout (cmd 0xec)
[   17.690017] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   17.690020] ata1: limiting SATA link speed to 1.5 Gbps
[   18.220017] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   48.220012] ata1.00: qc timeout (cmd 0xec)
[   48.220017] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   48.750018] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   48.950348] ata6.00: ATAPI: LITE-ON DVDRW SHW-160P6S, PS09, max UDMA/66
[   48.990228] ata6.00: configured for UDMA/66

```
So it can detect the drive during startup but the installer and fdisk can not.

I've been at it for 3 days to no avail.

---

### Post by aaronwater on 2009-12-29
Anyone?  Surely I'm not the first to use a sata disk drive with ubuntu?

---

### Post by aaronwater on 2010-01-02
Solved:

I set the boot option "nolapic" and the drive became visible for partitioning and installing.

Now I'm having trouble to put the same bootloader option on the SATA drive itself so it will boot.

---

