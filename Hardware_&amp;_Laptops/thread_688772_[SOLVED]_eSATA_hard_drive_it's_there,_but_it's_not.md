---
title: "[SOLVED] eSATA hard drive: it's there, but it's not."
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by glibdud on 2008-02-05
I just purchased a Rosewill RX353-S USB/eSATA external hard drive enclosure and a 320GB Seagate SATA HDD. I'm reasonably certain USB will work fine, but I'm interested in getting it going over eSATA.

Though my mobo supposedly supports SATA hot-swap, I went ahead and rebooted after connecting the drive. Ubuntu can see it... here's the evidence I've been able to collect (drive is model ST3320620AS) :

From /var/log/messages:
```
Feb  5 17:39:43 adhara kernel: [    5.508000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb  5 17:39:43 adhara kernel: [    5.552000] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
Feb  5 17:39:43 adhara kernel: [    5.552000] ata1.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/32)
Feb  5 17:39:43 adhara kernel: [    5.620000] ata1.00: configured for UDMA/133
Feb  5 17:39:43 adhara kernel: [    5.932000] ata2: SATA link down (SStatus 0 SControl 300)
Feb  5 17:39:43 adhara kernel: [    5.940000] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
```

/proc/scsi/scsi:
```
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3320620AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: CDEmu    Model: Virt. CD/DVD-ROM Rev: 0.01
  Type:   CD-ROM                           ANSI  SCSI revision: 00
Host: scsi6 Channel: 00 Id: 01 Lun: 00
  Vendor: CDEmu    Model: Virt. CD/DVD-ROM Rev: 0.01
  Type:   CD-ROM                           ANSI  SCSI revision: 00
```

Problem is I can't figure out what device this shows up as. I've tried a "sudo fdisk -l" on all my hd* and sd* drives. There are 3 sg* devices, but fdisk calls to those just hang. Anything I'm missing here?

Any help appreciated.

---

### Post by Yellow Pasque on 2008-02-05
Try this:
```
sudo lshw -C disk
```
Does the disk show there?

---

### Post by glibdud on 2008-02-05
> **Temüjin said:**
> Try this:
```
sudo lshw -C disk
```
Does the disk show there?

Oh good God. I'm an idiot. *sigh*

Thanks for that. I've never used lshw before. I'll have to play with it some more.

Unfortunately, in the process of doing that, I realized that my internal hard drive isn't the 160GB I could have sworn it was... that's right, it's the identical 320GB drive I just bought for the external. So yeah... the one showing up in the above logs is in fact my internal. So my problem is far worse than I thought, and I'm probably just going to use USB.

---

### Post by glibdud on 2008-02-05
To ever-so-slightly redeem myself, I've gotten it working (with eSATA). Turns out in order to enable that port on the mobo (Asus M2N-SLI Deluxe), I had to enable a RAID controller in the BIOS. Did that, and the drive now shows up as /dev/sdb. Makes me a happy camper.

---

### Post by Yellow Pasque on 2008-02-05
Congrats. :) Mark thread as solved please.

---

