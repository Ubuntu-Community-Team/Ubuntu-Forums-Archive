---
title: "sata device missing after recent updates"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by thoughts on 2008-02-09
Hello,

I have an Intel Core 2 Duo Dell system running Gutsy.  It has onboard SATA, which has been working fine since I got the system a few months ago.  The boot/root drive is PATA, though, on a PCI IDE controller.

So after a few months of the system -- including the SATA drive -- working fine in Gutsy, some updates from a few days ago required a reboot.  After rebooting, the SATA drive is missing.  It was /dev/sdd before, but now there is no sdd, only sda, sdb, and sdc -- two of those are PATA devices and the third is USB.

lspci shows this:

```

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)

```

grepping the dmesg output for "00:1f.2" gives this:

```

[   38.224451] ata_piix 0000:00:1f.2: version 2.11
[   38.224456] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   38.224477] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 20
[   38.224501] PCI: Setting latency timer of device 0000:00:1f.2 to 64

```

And grepping the dmesg output for sata/SATA gives this:

```

[   38.224626] ata3: SATA max UDMA/133 cmd 0x0001f700 ctl 0x0001f602 bmdma 0x0001f300 irq 20
[   38.224629] ata4: SATA max UDMA/133 cmd 0x0001f500 ctl 0x0001f402 bmdma 0x0001f308 irq 20
[  164.298509] ata5: SATA max UDMA/133 cmd 0x0001f000 ctl 0x0001ef02 bmdma 0x0001ec00 irq 20
[  164.298512] ata6: SATA max UDMA/133 cmd 0x0001ee00 ctl 0x0001ed02 bmdma 0x0001ec08 irq 20

```

This seems to indicate that the kernel is at least recognizing the SATA controller(s).  But there's no sdd device, and no mention of sdd in the dmesg output.  Running "fdisk -l" and "lshw -C disk" shows only my PATA & USB drives.

Could it be possible that I need to load a SATA module?  Ubuntu seems to take care of loading all the necessary drivers automatically, but maybe this is a bug?  However, I'm not sure which module I'd need to load, since my SATA hardware is Intel, but there doesn't seem to be a SATA module named (or containing) "intel":

```

root@mybox:~# find /lib/modules/ -iname '*sata*'
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_sil24.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_vsc.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_sil.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_qstor.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_sis.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_mv.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_sx4.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_svw.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_via.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_uli.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_inic162x.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_nv.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/sata_promise.ko

```

I've searched the forums here, but the posts that seem related are all not quite applicable (i.e. for eSATA, or for special cases like a PATA drive using a SATA adapter).

What else can I try?

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

