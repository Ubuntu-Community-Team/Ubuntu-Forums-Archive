---
title: "DVD drive DMA problem"
date: 2009-03-23
forum: Hardware
---

### Post by lykwydchykyn on 2009-03-23
Having a problem with the DVD drive on my wife's laptop.  She's running Kubuntu 8.04 with all updates on an emachines laptop.  Video normally works fine, and we've got fglrx loaded for the ATI card, so 3D acceleration works; but when playing DVD video the playback is extremely jumpy.  CD reading and recording is also very slow.

I tracked down the problem to DMA being disabled on the drive.  The output of "dmesg|grep ata" shows this:
```

[    0.000000]  BIOS-e820: 000000001bea0000 - 000000001bea5000 (ACPI data)
[   11.161950] Memory: 440952k/457344k available (2179k kernel code, 15872k reserved, 1008k data, 368k init, 0k highmem)
[   11.161967]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   11.873764] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   13.837991] Write protecting the kernel read-only data: 806k
[   15.879089] libata version 3.00 loaded.
[   16.415383] scsi0 : pata_atiixp
[   16.416293] scsi1 : pata_atiixp
[   16.417266] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x10a0 irq 14
[   16.417269] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x10a8 irq 15
[   16.579951] ata1.00: ATA-6: WDC WD600UE-22HCT0, 09.07D09, max UDMA/100
[   16.579957] ata1.00: 117210240 sectors, multi 16: LBA 
[   16.587936] ata1.00: configured for UDMA/100
[   16.907784] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, GW01, max UDMA/33
[   16.907801] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   17.079649] ata2.00: configured for PIO4
[   18.318426] EXT3-fs: mounted filesystem with ordered data mode.
[   40.066127] ReiserFS: sda6: using ordered data mode
[   40.696911] ReiserFS: sda5: using ordered data mode

```

I followed the instructions on this page: [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

They did not work.  You can see from the output that it is indeed loading the pata_atiixp driver rather than the pata_generic driver, as per the advice on that wiki page.  However, DMA is still not working for the device.

I also found some references to blacklisting the pata_acpi driver on a mailing list, and did that.  Still no results.

Can anyone help me figure out why DMA is not working, and how to get it working on this drive?  It had worked fine in the past with other Linux distros (Including SimplyMEPIS 6.5, which was based on Dapper), but has not worked since installing Hardy Heron.

---

### Post by abn91c on 2009-03-23
try this system settings>desktop>desktop effects>advanced>composting type, change to Xrender, that how i managed to get transparent menus working on my old Dell GX240 with ATI Rage 128 video. Cnet Tv videos run/work ok. Did the same on my dell inspiron 1000 and the DVD's play good.

---

### Post by lykwydchykyn on 2009-03-23
We're running kde3 with no compositing.  Video settings are working fine, I'm 90% certain this is an issue with DMA on the DVD rom drive.

---

### Post by abn91c on 2009-03-23
Is there something in the Bios you may need to activate?

---

### Post by lykwydchykyn on 2009-03-23
Ok, I fixed it.  Someone may want to update the wiki page.

Apparently I needed to update /etc/initramfs-tools/modules and add this:
```

pata_atiixp
blacklist ata_generic

```

Then I ran update-initramfs and had her reboot.  BOOM DVD's play fine.

---

