---
title: "SIIG eSATA Expresscard"
date: 2009-01-12
forum: Hardware
---

### Post by mattengstrom on 2009-01-12
Just bought a 500 GB USB/eSATA hard drive.  Shows up in "sudo fdisk -l" just fine, so I know that there's no problem with the drive.

Also bought a SIIG eSATA II ExpressCard.  When the drive is plugged into that, it doesn't show up for fdisk.

Is there something special that I need to do to enable the ExpressCard?  Or should it be auto-detected if it's supported?

---

### Post by mattengstrom on 2009-01-13
Anyone? Bueller??

Or does anyone have any experience with eSATA Expresscards that work under ubuntu?

---

### Post by Hated On Mostly on 2009-01-14
According to the specifications on Newegg and the manufacturers specifications. None of the SIIG SATA expresscards feature support for linux.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16839150001](http://www.newegg.com/Product/Product.aspx?Item=N82E16839150001)
[http://www.siig.com/ViewProduct.aspx?pn=SC-SAE512-S1](http://www.siig.com/ViewProduct.aspx?pn=SC-SAE512-S1)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16839150002](http://www.newegg.com/Product/Product.aspx?Item=N82E16839150002)
[http://www.siig.com/ViewProduct.aspx?pn=SC-SAE612-S1](http://www.siig.com/ViewProduct.aspx?pn=SC-SAE612-S1)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16839150022](http://www.newegg.com/Product/Product.aspx?Item=N82E16839150022)
[http://siig.com/ViewProduct.aspx?pn=SC-SAEE22-S1](http://siig.com/ViewProduct.aspx?pn=SC-SAEE22-S1)

I have this card which works with Ubuntu (specs don't state support for Linux either):

[http://www.newegg.com/Product/Product.aspx?Item=N82E16839200006](http://www.newegg.com/Product/Product.aspx?Item=N82E16839200006)
[http://www.rosewill.com/products/814/productDetail.htm](http://www.rosewill.com/products/814/productDetail.htm)

However, I am replacing it with this card:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16839228001](http://www.newegg.com/Product/Product.aspx?Item=N82E16839228001)
[http://ppa-usa.com/products/pcmcia/1165.htm](http://ppa-usa.com/products/pcmcia/1165.htm)

I am replacing the Rosewill card, because I want a full size expresscard (54 mm vs 35 mm), because the 35mm expresscards are loose in my expresscard slot. Based on the specifications and a review by someone who tried the card using Ubuntu v7.04 and v7.10, it should work just fine with Ubuntu.

As far as your card goes you can keep it, wait, and hope that drivers are added to Linux to support it or return/replace it. Maybe try the latest daily build of Jaunty (9.04) or update your current system with the proposed updates and see if a new kernel has drivers for the device.

---

### Post by mattengstrom on 2009-01-15
Boy, do I feel stupid.  :(  It helps a LOT if you plug the card into the right slot.

My Thinkpad has a PCMCIA slot and an Expresscard slot.  The Expresscard is on top.  The laptop is ding'ed up a bit. and the card didn't want to slide in to the Expresscard slot, and it slid into the pcmcia slot just fine.

Anyways, after I pulled my head out of my a** and put the card in the right slot, it's being recognized after a reboot.  lspci shows:

```
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA
Raid II Controller (rev 01)
```

So the card is being recognized, but the drive that I plug into it isn't.  After rebooting, fdisk -l shows

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d8f8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 8383 67336416 83 Linux
/dev/sda2 12031 12161 1052257+ 82 Linux swap / Solaris
/dev/sda3 8384 12030 29294527+ 83 Linux
```

which is my internal drive.  No external drive showing up.  The drive works fine as eSATA on my Windows-based desktop.

So what do I need to do to get the drive to show up in Ubuntu?

---

### Post by mattengstrom on 2009-01-16
Still no joy on this one.  I opened up a support incident with SIIG.

---

### Post by markbuntu on 2009-01-16
I used a SIIG PCI SATA card (not PCIx) for a while and it worked OK. It had its own bios that ran after the mobo and rearranged my drives but it was usable. It had a 1.5Gb/s transfer rate so it was good enough and cheap enough for me. I think there was some way to change it from raid but I can't remember.

---

### Post by pcting on 2009-05-14
I'm using the SIIG SC-SAE512-S1 on my Lenovo T61 ThinkPad running Ubuntu 9.04 and it's working pretty stable. Here's the dump of my logs as it inits:
```

sata_sil24 0000:05:00.0: enabling device (0000 -> 0003)
sata_sil24 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
scsi5 : sata_sil24
scsi6 : sata_sil24
ata6: SATA max UDMA/100 host m128@0xd0004000 port 0xd0000000 irq 19
ata7: SATA max UDMA/100 host m128@0xd0004000 port 0xd0002000 irq 19
ata6: SATA link down (SStatus 0 SControl 0)
ata7: controller in dubious state, performing PORT_RST
ata7: controller in dubious state, performing PORT_RST
ata7: controller in dubious state, performing PORT_RST
ata7: reset failed (errno=-5), retrying in 25 secs
ata7: limiting SATA link speed to 1.5 Gbps
ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
ata7.00: ATA-8: ST9320421AS, SD13, max UDMA/133
ata7.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
ata7.00: configured for UDMA/100
scsi 6:0:0:0: Direct-Access     ATA      ST9320421AS      SD13 PQ: 0 ANSI: 5
sd 6:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
sd 6:0:0:0: [sdb] Write Protect is off
sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 6:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
sd 6:0:0:0: [sdb] Write Protect is off
sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb: sdb1
sd 6:0:0:0: [sdb] Attached SCSI disk
sd 6:0:0:0: Attached scsi generic sg2 type 0

```

There are a few things to note:
1. Although my external hd supports SATA 3.0, I'm only able to mount at SATA 1.5. Maybe it's because of my cheapo external hd case.
2. My internal partitions are ext3; my external hd is in xfs. I tested copying an ISO from one of my internal paritions to the external and it clocked at ~46MB/s.
3. Occational plugging the ESATA card will fail to init; so, I end up just pulling it out and plugging it back in and it's good to go.

---

### Post by size_XXM on 2009-05-24
markbuntu, the fact that your card works when plugged in before booting means there's nothing wrong with the card - it's all about hotplugging, which is this case is a PCIe device - some ExpressCard devices such as wireless modems are logically USB devices, while the high-speed devices (Firewire, SATA, etc.) are PCI-express. PCI-express hotplugging is a bit spotty in Linux (the preferred method relies on the hardware vendor's ACPI implementation and therefore BIOS; the hard-coded OTOH, works almost always but needs to be turned on manually).

To make it short, in Jaunty, edit the /boot/grub/menu.lst and add the option **pciehp.pciehp_force=1** to the kernel line of boot options you wish to change this way (I put it on both normal and recovery mode options):
```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
...
kernel          /boot/vmlinuz-2.6.28-11-generic root=... ro quiet splash **pciehp.pciehp_force=1**
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
savedefault
```

---

