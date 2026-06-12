---
title: "Revodrive is not recognized by 3.2.0 kernel after upgrade to 12.04"
date: 2012-06-05
forum: Hardware
---

### Post by zeehond on 2012-06-05
Hi everyone,

I have got 120GB OCZ Revodrive SSD and has been running Ubuntu for more than three years on it. However after upgrade to 12.04 it stopped booting at all.
Investigation revealed that Revodrive is not discovered during the boot, so the root partition could not be found.

Fortunately, old 3.0.0-15 kernel was still there so I was able to boot from it into 12.04 and everything else works just fine.

I've updated the firmware of the Revodrive to latest 1.35 but it didn't help.
Here's dmesg output about the Revodrive when I boot from 3.0.0-15 kernel.

```
[    3.879925] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    3.889705] ata1.00: ATA-8: OCZ-REVODRIVE, 1.35, max UDMA/133
[    3.889710] ata1.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.899695] ata1.00: configured for UDMA/100
[    3.899857] scsi 0:0:0:0: Direct-Access     ATA      OCZ-REVODRIVE    1.35 PQ: 0 ANSI: 5
[    3.899948] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.900038] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    3.900135] sd 0:0:0:0: [sda] Write Protect is off
[    3.900136] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.900153] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.902192]  sda: sda1 sda2
[    3.902195] sda: p1 size 195312384 extends beyond EOD, enabling native capacity
[    3.902464]  sda: sda1 sda2
[    3.902466] sda: p1 size 195312384 extends beyond EOD, truncated
[    3.902486] sda: p2 start 195313664 is beyond EOD, truncated
[    3.902668] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.129733] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    6.138146] ata2.00: ATA-8: OCZ-REVODRIVE, 1.35, max UDMA/133
[    6.138151] ata2.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.148138] ata2.00: configured for UDMA/100
[    6.148243] scsi 1:0:0:0: Direct-Access     ATA      OCZ-REVODRIVE    1.35 PQ: 0 ANSI: 5
[    6.148313] sd 1:0:0:0: [sdb] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    6.148328] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    6.148370] sd 1:0:0:0: [sdb] Write Protect is off
[    6.148372] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.148403] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.150904]  sdb: unknown partition table
[    6.151139] sd 1:0:0:0: [sdb] Attached SCSI disk
```

This is the very first of the Revodrives, not X2, X3 or whatever came next.

I tried installing proprietary closed source OCZ drivers from [http://www.oczenterprise.com/drivers.html](http://www.oczenterprise.com/drivers.html) but that didn't work for me either. I've booted Live CD and then installed via insmod but Revodrive didn't appear in dmesg.

I'm fine to build the custom 3.2.x kernel for that, if someone could point me to some patch or option in the kernel to switch on.

Thanks in advance for your attention!

---

### Post by zeehond on 2012-06-09
so.... no one could tell me how to fix this?

---

### Post by zeehond on 2012-07-12
> **zeehond said:**
> so.... no one could tell me how to fix this?

I tried different 3.0, 3.2 and 3.4 kernels, digging into kernel code and studying all available options of 'lspci' command.

But what did solve the issue was swapping of the REVODRIVE card and videocard (they occupied two similar 16x PCIe slots). 

I couldn't say anything other than WTF!!111 but that's it. Hope it may help someone.

---

