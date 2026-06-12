---
title: "Ubuntu Overworking My Hard Disk"
date: 2008-10-03
forum: General Help
---

### Post by DocHoliday52090 on 2008-10-03
I have no idea what Ubuntu is doing, but it loves screwing around the with hard disk when it doesn't need to. 

I can leave it with no running programs, just a blank desktop, and it hard drive activity light will flash every now and then, blink furiously for some time, and then dissapear for a good two seconds...

I got frustrated and used the following commands to see what's up:

echo 1 > /proc/sys/vm/block_dump

and then dmesg

Here's what I got.

```
(was 0x820000, writing 0x82a820)
[23392.112615] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100007)
[23392.268077] tifm_7xx1 0000:02:06.3: restoring config space at offset 0xf (was 0x40702ff, writing 0x407020a)
[23392.268103] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x4 (was 0x0, writing 0xd0102000)
[23392.268110] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[23392.268118] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[23392.268140] tifm_7xx1 0000:02:06.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[23392.284068] sdhci-pci 0000:02:06.4: restoring config space at offset 0xf (was 0x40703ff, writing 0x407030a)
[23392.284089] sdhci-pci 0000:02:06.4: restoring config space at offset 0x6 (was 0x0, writing 0xd0106000)
[23392.284095] sdhci-pci 0000:02:06.4: restoring config space at offset 0x5 (was 0x0, writing 0xd0105000)
[23392.284102] sdhci-pci 0000:02:06.4: restoring config space at offset 0x4 (was 0x0, writing 0xd0104000)
[23392.284109] sdhci-pci 0000:02:06.4: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[23392.284117] sdhci-pci 0000:02:06.4: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[23392.284134] sdhci-pci 0000:02:06.4: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[23392.284171] pci 0000:02:06.5: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[23392.284190] pci 0000:02:06.5: restoring config space at offset 0x7 (was 0x0, writing 0xd010a000)
[23392.284196] pci 0000:02:06.5: restoring config space at offset 0x6 (was 0x0, writing 0xd0109000)
[23392.284203] pci 0000:02:06.5: restoring config space at offset 0x5 (was 0x0, writing 0xd0108000)
[23392.284209] pci 0000:02:06.5: restoring config space at offset 0x4 (was 0x0, writing 0xd0107000)
[23392.284219] pci 0000:02:06.5: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100002)
[23392.287569] serial 00:02: activated
[23392.291087] parport_pc 00:04: activated
[23392.500496] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[23392.500499] ata1.01: ACPI cmd ef/03:22:00:00:00:b0 filtered out
[23392.508489] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[23392.508492] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[23392.508495] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[23392.508497] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
[23392.508645] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[23392.532414] ata1.00: configured for UDMA/100
[23392.548420] ata1.01: configured for MWDMA2
[23392.592435] ata1.00: configured for UDMA/100
[23392.608420] ata1.01: configured for MWDMA2
[23392.608423] ata1: EH complete
[23392.608482] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[23392.608502] sd 0:0:0:0: [sda] Write Protect is off
[23392.608504] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[23392.608536] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[23392.608567] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[23392.608584] sd 0:0:0:0: [sda] Write Protect is off
[23392.608586] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[23392.608616] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[23392.632088] sd 0:0:0:0: [sda] Starting disk
[23392.664078] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[23392.664082] pci 0000:00:02.0: setting latency timer to 64
[23392.924067] usb 2-1: reset low speed USB device using uhci_hcd and address 5
[23393.234412] PM: resume devices took 2.460 seconds
[23393.234470] PM: Finishing wakeup.
[23393.234471] Restarting tasks ... done.
[23394.533734] ADDRCONF(NETDEV_UP): eth0: link is not ready
[23395.883472] tg3: eth0: Link is up at 100 Mbps, full duplex.
[23395.883483] tg3: eth0: Flow control is off for TX and off for RX.
[23395.884326] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[23404.800029] eth1: no IPv6 routers present
[23406.052027] eth0: no IPv6 routers present
[23763.707966] PM: Syncing filesystems ... done.
[23763.709672] PM: Preparing system for mem sleep
[23763.710487] Freezing user space processes ... (elapsed 0.00 seconds) done.
[23763.712598] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[23763.712693] PM: Entering mem sleep
[23763.712696] Suspending console(s) (use no_console_suspend to debug)
[23763.732452] pci 0000:00:02.0: PCI INT A disabled
[23764.262944] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[23764.263112] sd 0:0:0:0: [sda] Stopping disk
[23766.792913] ACPI handle has no context!
[23766.794059] parport_pc 00:04: disabled
[23766.795639] serial 00:02: disabled
[23766.796077] ACPI: Transitioning device [C1A5] to D3
[23766.796206] ACPI handle has no context!
[23766.796214] sdhci-pci 0000:02:06.4: PCI INT C disabled
[23766.796222] ACPI handle has no context!
[23766.812083] ACPI handle has no context!
[23766.812090] tifm_7xx1 0000:02:06.3: PCI INT B disabled
[23766.812097] ACPI handle has no context!
[23766.828121] eth1: Going into suspend...
[23766.831682] ipw2200 0000:02:04.0: PCI INT A disabled
[23766.844238] ata2: port disabled. ignoring.
[23766.844290] ata_piix 0000:00:1f.1: PCI INT A disabled
[23766.844561] Intel ICH 0000:00:1e.2: PCI INT A disabled
[23766.844682] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[23766.860100] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[23766.860134] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[23766.860168] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[23766.880503] PM: suspend devices took 3.168 seconds
[23766.880851] ACPI: Preparing to enter system sleep state S3
[23766.881057] Disabling non-boot CPUs ...
[23766.881057] Back to C!
[23766.881057] Force enabled HPET at resume
[23766.881393] ACPI: Waking up from system sleep state S3
[23767.289740] ACPI: EC: non-query interrupt received, switching to interrupt mode
[23767.438457] pci 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[23767.438465] pci 0000:00:02.0: restoring config space at offset 0x7 (was 0x0, writing 0xd0480000)
[23767.438469] pci 0000:00:02.0: restoring config space at offset 0x6 (was 0x8, writing 0xc0000008)
[23767.438473] pci 0000:00:02.0: restoring config space at offset 0x5 (was 0x1, writing 0x5001)
[23767.438477] pci 0000:00:02.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0400000)
[23767.438481] pci 0000:00:02.0: restoring config space at offset 0x1 (was 0x900000, writing 0x900003)
[23767.454737] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x0, writing 0xd0500000)
[23767.454744] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[23767.454762] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x4010a)
[23767.454774] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[23767.454780] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xd000d000)
[23767.454785] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[23767.454795] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[23767.454802] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[23767.454841] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[23767.454859] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x4020b)
[23767.454871] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[23767.454877] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[23767.454882] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0xf0)
[23767.454892] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[23767.454899] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[23767.454936] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[23767.454947] uhci_hcd 0000:00:1d.0: enabling device (0000 -> 0001)
[23767.454954] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[23767.454961] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[23767.454967] uhci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[23767.454980] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x8 (was 0x1, writing 0x2021)
[23767.455017] usb usb1: root hub lost power or was reset
[23767.455035] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
[23767.455039] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[23767.455045] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[23767.455051] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[23767.455064] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x2041)
[23767.455098] usb usb2: root hub lost power or was reset
[23767.455127] uhci_hcd 0000:00:1d.2: enabling device (0000 -> 0001)
[23767.455131] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[23767.455137] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[23767.455143] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[23767.455157] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x2061)
[23767.455191] usb usb3: root hub lost power or was reset
[23767.468079] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[23767.468084] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[23767.468090] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[23767.468103] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[23767.468122] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0xd0580000)
[23767.468157] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x23f12001)
[23767.468163] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xd030d010)
[23767.468168] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800010, writing 0x22803030)
[23767.468180] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100001, writing 0x100107)
[23767.468196] pci 0000:00:1e.0: setting latency timer to 64
[23767.468304] Intel ICH 0000:00:1e.2: power state changed by ACPI to D0
[23767.468315] Intel ICH 0000:00:1e.2: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[23767.468329] Intel ICH 0000:00:1e.2: restoring config space at offset 0x7 (was 0x0, writing 0xd0582000)
[23767.468335] Intel ICH 0000:00:1e.2: restoring config space at offset 0x6 (was 0x0, writing 0xd0581000)
[23767.468340] Intel ICH 0000:00:1e.2: restoring config space at offset 0x5 (was 0x1, writing 0x2201)
[23767.468346] Intel ICH 0000:00:1e.2: restoring config space at offset 0x4 (was 0x1, writing 0x2101)
[23767.468354] Intel ICH 0000:00:1e.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900003)
[23767.468425] Intel ICH 0000:00:1e.2: power state changed by ACPI to D0
[23767.468432] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[23767.468438] Intel ICH 0000:00:1e.2: setting latency timer to 64
[23768.481948] pci 0000:00:1e.3: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[23768.481965] pci 0000:00:1e.3: restoring config space at offset 0x5 (was 0x1, writing 0x2501)
[23768.481971] pci 0000:00:1e.3: restoring config space at offset 0x4 (was 0x1, writing 0x2401)
[23768.481979] pci 0000:00:1e.3: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[23768.482027] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[23768.482041] ata_piix 0000:00:1f.1: restoring config space at offset 0x8 (was 0x1, writing 0x2581)
[23768.482054] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2880005)
[23768.482065] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[23768.482070] ata_piix 0000:00:1f.1: setting latency timer to 64
[23768.482121] ata2: port disabled. ignoring.
[23768.486680] tg3 0000:10:00.0: restoring config space at offset 0xc (was 0x0, writing 0xecff0000)
[23768.486703] tg3 0000:10:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[23768.486712] tg3 0000:10:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[23768.486740] eth1: Coming out of suspend...
[23768.500066] ipw2200 0000:02:04.0: enabling device (0000 -> 0002)
[23768.500072] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[23768.500084] ipw2200 0000:02:04.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[23768.500109] ipw2200 0000:02:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0100000)
[23768.500116] ipw2200 0000:02:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4010)
[23768.500124] ipw2200 0000:02:04.0: restoring config space at offset 0x1 (was 0x2900002, writing 0x2900006)
[23768.628619] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xf (was 0x34001ff, writing 0x5c0010b)
[23768.628625] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xe (was 0x0, writing 0x34fc)
[23768.628632] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xd (was 0x0, writing 0x3400)
[23768.628638] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xc (was 0x0, writing 0x30fc)
[23768.628645] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xb (was 0x0, writing 0x3000)
[23768.628651] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xa (was 0x0, writing 0x27fff000)
[23768.628658] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x9 (was 0x0, writing 0x24000000)
[23768.628665] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x8 (was 0x0, writing 0x23fff000)
[23768.628671] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x7 (was 0x0, writing 0x20000000)
[23768.628678] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0060302)
[23768.628702] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0101000)
[23768.628708] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x3 (was 0x820000, writing 0x82a820)
[23768.628717] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100007)
[23768.784078] tifm_7xx1 0000:02:06.3: restoring config space at offset 0xf (was 0x40702ff, writing 0x407020a)
[23768.784104] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x4 (was 0x0, writing 0xd0102000)
[23768.784111] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[23768.784119] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[23768.784141] tifm_7xx1 0000:02:06.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[23768.800069] sdhci-pci 0000:02:06.4: restoring config space at offset 0xf (was 0x40703ff, writing 0x407030a)
[23768.800091] sdhci-pci 0000:02:06.4: restoring config space at offset 0x6 (was 0x0, writing 0xd0106000)
[23768.800097] sdhci-pci 0000:02:06.4: restoring config space at offset 0x5 (was 0x0, writing 0xd0105000)
[23768.800104] sdhci-pci 0000:02:06.4: restoring config space at offset 0x4 (was 0x0, writing 0xd0104000)
[23768.800110] sdhci-pci 0000:02:06.4: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[23768.800119] sdhci-pci 0000:02:06.4: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[23768.800135] sdhci-pci 0000:02:06.4: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[23768.800173] pci 0000:02:06.5: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[23768.800192] pci 0000:02:06.5: restoring config space at offset 0x7 (was 0x0, writing 0xd010a000)
[23768.800198] pci 0000:02:06.5: restoring config space at offset 0x6 (was 0x0, writing 0xd0109000)
[23768.800205] pci 0000:02:06.5: restoring config space at offset 0x5 (was 0x0, writing 0xd0108000)
[23768.800211] pci 0000:02:06.5: restoring config space at offset 0x4 (was 0x0, writing 0xd0107000)
[23768.800221] pci 0000:02:06.5: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100002)
[23768.803576] serial 00:02: activated
[23768.807111] parport_pc 00:04: activated
[23769.128499] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[23769.128502] ata1.01: ACPI cmd ef/03:22:00:00:00:b0 filtered out
[23769.136491] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[23769.136494] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[23769.136497] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[23769.136500] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
[23769.136648] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[23769.148089] sd 0:0:0:0: [sda] Starting disk
[23769.160430] ata1.00: configured for UDMA/100
[23769.176434] ata1.01: configured for MWDMA2
[23769.200428] ata1.00: configured for UDMA/100
[23769.216434] ata1.01: configured for MWDMA2
[23769.216437] ata1: EH complete
[23769.229654] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[23769.229680] sd 0:0:0:0: [sda] Write Protect is off
[23769.229682] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[23769.229726] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[23769.229770] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[23769.229793] sd 0:0:0:0: [sda] Write Protect is off
[23769.229795] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[23769.229838] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[23769.244078] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[23769.244082] pci 0000:00:02.0: setting latency timer to 64
[23769.504064] usb 2-1: reset low speed USB device using uhci_hcd and address 5
[23769.814408] PM: resume devices took 2.524 seconds
[23769.814465] PM: Finishing wakeup.
[23769.814467] Restarting tasks ... done.
[23770.576683] ADDRCONF(NETDEV_UP): eth0: link is not ready
[23770.580407] ADDRCONF(NETDEV_UP): eth1: link is not ready
[23770.691335] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[23772.103094] tg3: eth0: Link is up at 100 Mbps, full duplex.
[23772.103109] tg3: eth0: Flow control is off for TX and off for RX.
[23772.103873] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[23781.304027] eth1: no IPv6 routers present
[28438.788774] compiz.real[6343]: segfault at 5400d5 ip 08055bed sp bffa1670 error 4 in compiz.real[8048000+33000]
[28458.936357] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28462.165037] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28468.640604] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28478.313031] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28481.513292] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28484.699938] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28487.899352] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28491.090235] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28494.288330] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28497.507558] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28500.698576] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28503.889222] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28507.077421] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28510.261432] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28513.451544] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28516.639267] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28519.827913] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28523.013197] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28526.200544] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28529.411673] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28535.820707] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28539.013988] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28542.242768] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28545.446822] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28548.627490] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28555.024738] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28558.228621] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28567.858612] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28578.548395] ppdev0: registered pardevice
[28578.596290] ppdev0: unregistered pardevice
[28578.684153] ppdev0: registered pardevice
[28578.732052] ppdev0: unregistered pardevice
[28578.841107] ppdev0: registered pardevice
[28578.888404] ppdev0: unregistered pardevice
[28583.825717] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28587.024508] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28590.239528] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28593.445525] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28596.634908] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28599.842331] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28603.057726] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28606.258696] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28609.468887] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28612.719203] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28615.925278] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28619.158940] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28622.362495] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28625.567038] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28628.760342] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28635.160113] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28641.607781] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28644.811794] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28651.216402] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28654.405640] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28667.179986] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28676.791493] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[28964.017298] type=1503 audit(1223068459.567:5): operation="syscall" name="mount" pid=21669 profile="/usr/share/gdm/guest-session/Xsession"
[28964.147284] type=1503 audit(1223068459.695:6): operation="capable" name="dac_override" pid=21670 profile="/usr/share/gdm/guest-session/Xsession"
[28964.147312] type=1503 audit(1223068459.695:7): operation="capable" name="dac_read_search" pid=21670 profile="/usr/share/gdm/guest-session/Xsession"
[28964.155927] type=1503 audit(1223068459.703:8): operation="capable" name="dac_override" pid=21671 profile="/usr/share/gdm/guest-session/Xsession"
[28964.155952] type=1503 audit(1223068459.703:9): operation="capable" name="dac_read_search" pid=21671 profile="/usr/share/gdm/guest-session/Xsession"
[28979.934381] type=1503 audit(1223068475.483:10): operation="file_mmap" requested_mask="mrw::" denied_mask="m::" fsuid=114 name="/tmp/guest-home.e21409/.wapi/shared_data-laptop-Linux-i686-312-11-0" pid=21806 profile="/usr/share/gdm/guest-session/Xsession"
[28979.934875] type=1503 audit(1223068475.483:11): operation="file_mmap" requested_mask="mr::" denied_mask="m::" fsuid=114 name="/tmp/guest-home.e21409/.wapi/shared_data-laptop-Linux-i686-312-11-0" pid=21806 profile="/usr/share/gdm/guest-session/Xsession"
[29581.388542] ttyS2: LSR safety check engaged!
[42911.264517] gnome-do(12103): READ block 59439424 on sda5
[42911.264555] dd(4787): READ block 35392 on sda6
[42911.264673] dd(4787): READ block 35400 on sda6
[42911.264685] dd(4787): READ block 35408 on sda6
[42911.264696] dd(4787): READ block 35424 on sda6
[42911.264707] dd(4787): READ block 35432 on sda6
[42911.264716] dd(4787): READ block 35440 on sda6
[42911.264723] dd(4787): READ block 35448 on sda6
[42911.344473] dd(4787): READ block 47268464 on sda5
[42911.344497] dd(4787): READ block 47268472 on sda5
[42911.344509] dd(4787): READ block 47268480 on sda5
[42911.344518] dd(4787): READ block 47268488 on sda5
[42911.344528] dd(4787): READ block 47268496 on sda5
[42911.344537] dd(4787): READ block 47268504 on sda5
[42911.344546] dd(4787): READ block 47268512 on sda5
[42911.344555] dd(4787): READ block 47268520 on sda5
[42911.344565] dd(4787): READ block 47268528 on sda5
[42911.344574] dd(4787): READ block 47268536 on sda5
[42911.344583] dd(4787): READ block 47268544 on sda5
[42911.344594] dd(4787): READ block 47268552 on sda5
[42911.344615] dd(4787): READ block 47268560 on sda5
[42911.351812] gnome-do(12103): READ block 59245048 on sda5
[42911.358603] gnome-do(12103): READ block 623064 on sda5
[42911.385534] gnome-do(12104): READ block 830016 on sda6
[42911.385564] gnome-do(12104): READ block 830024 on sda6
[42911.385575] gnome-do(12104): READ block 830032 on sda6
[42911.385584] gnome-do(12104): READ block 830048 on sda6
[42911.385595] gnome-do(12104): READ block 830056 on sda6
[42911.385604] gnome-do(12104): READ block 830064 on sda6
[42911.404194] dd(4787): READ block 47268568 on sda5
[42911.404292] dd(4787): READ block 35136 on sda6
[42911.404305] dd(4787): READ block 35144 on sda6
[42911.404313] dd(4787): READ block 35152 on sda6
[42911.404321] dd(4787): READ block 35160 on sda6
[42911.404329] dd(4787): READ block 35168 on sda6
[42911.404336] dd(4787): READ block 35176 on sda6
[42911.404344] dd(4787): READ block 35184 on sda6
[42911.404351] dd(4787): READ block 35192 on sda6
[42911.415975] dd(4787): READ block 35200 on sda6
[42911.416074] dd(4787): READ block 35208 on sda6
[42911.416087] dd(4787): READ block 35216 on sda6
[42911.416095] dd(4787): READ block 35224 on sda6
[42911.416103] dd(4787): READ block 35232 on sda6
[42911.416111] dd(4787): READ block 35240 on sda6
[42911.416846] klogd(4790): READ block 23744456 on sda5
[42911.435999] gnome-do(12104): READ block 975880 on sda6
[42911.436316] gnome-do(12104): READ block 975888 on sda6
[42911.436330] gnome-do(12104): READ block 975896 on sda6
[42911.436339] gnome-do(12104): READ block 975904 on sda6
[42911.436348] gnome-do(12104): READ block 975912 on sda6
[42911.436356] gnome-do(12104): READ block 975920 on sda6
[42911.436364] gnome-do(12104): READ block 975928 on sda6
[42911.461583] klogd(4790): READ block 35328 on sda6
[42911.461689] klogd(4790): READ block 35336 on sda6
[42911.461702] klogd(4790): READ block 35344 on sda6
[42911.461711] klogd(4790): READ block 35352 on sda6
[42911.461719] klogd(4790): READ block 35360 on sda6
[42911.461727] klogd(4790): READ block 35368 on sda6
[42911.461735] klogd(4790): READ block 35376 on sda6
[42911.461742] klogd(4790): READ block 35384 on sda6
[42911.462362] klogd(4790): READ block 35456 on sda6
[42911.462441] klogd(4790): READ block 35464 on sda6
[42911.462452] klogd(4790): READ block 35472 on sda6
[42911.462460] klogd(4790): READ block 35480 on sda6
[42911.462468] klogd(4790): READ block 35488 on sda6
[42911.462476] klogd(4790): READ block 35496 on sda6
[42911.462483] klogd(4790): READ block 35504 on sda6
[42911.462491] klogd(4790): READ block 35512 on sda6
[42911.463237] syslogd(4733): dirtied inode 426058 (syslog) on sda5
[42911.463264] syslogd(4733): READ block 7763744 on sda5
[42911.473725] syslogd(4733): READ block 18010520 on sda5
[42911.486353] syslogd(4733): dirtied inode 426058 (syslog) on sda5
[42911.486375] syslogd(4733): dirtied inode 426058 (syslog) on sda5
[42911.486409] syslogd(4733): dirtied inode 426432 (kern.log) on sda5
[42911.486441] syslogd(4733): READ block 7063504 on sda5
[42911.501212] syslogd(4733): READ block 8074472 on sda5
[42911.507261] syslogd(4733): dirtied inode 426432 (kern.log) on sda5
[42911.507279] syslogd(4733): dirtied inode 426432 (kern.log) on sda5
[42911.507308] syslogd(4733): dirtied inode 426353 (debug) on sda5
[42911.507331] syslogd(4733): READ block 7484712 on sda5
[42911.522621] syslogd(4733): READ block 8071128 on sda5
[42911.535696] syslogd(4733): dirtied inode 426353 (debug) on sda5
[42911.535712] syslogd(4733): dirtied inode 426353 (debug) on sda5
[42911.538532] syslogd(4733): READ block 17825792 on sda5
[42911.709326] gnome-do(12104): READ block 1175968 on sda6
[42911.710852] gnome-do(12104): READ block 1175984 on sda6
[42911.712222] gnome-do(12104): READ block 1175992 on sda6
[42911.898128] gnome-do(12103): dirtied inode 3358863 (tmp299c0244.tmp) on sda5

```

What's going on?

---

### Post by Neo_The_User on 2008-10-03
Well one thing is for sure. It's reading the blocks on your HDD. I have no idea WHY but it is.

---

### Post by RequinB4 on 2008-10-03
Try turning off avant-window-navigator.  I have also experienced this.  Considered writing a bug report, but haven't had the time yet.

---

### Post by DocHoliday52090 on 2008-10-03
I stopped using awn yesterday (after about a year of use). No difference.

---

### Post by RequinB4 on 2008-10-03
> **DocHoliday52090 said:**
> I stopped using awn yesterday (after about a year of use). No difference.

Have you rebooted since then? (yes, I know...)  I only noticed the symptom recently as well.

---

### Post by AmyRose on 2008-10-03
It's probably file indexing going on in the background by Tracker and/or slocate. You can disable some of it by going to System --> Preferences --> Search and Indexing.

---

### Post by DocHoliday52090 on 2008-10-03
Indexing is off and I have restarted.

---

### Post by AmyRose on 2008-10-03
Have you tried running top and letting it sit? It should give a hint as to which process is doing it.

---

### Post by DocHoliday52090 on 2008-10-03
dd places consistently high. What does it do?

EDIT: klogd as well.

---

### Post by DocHoliday52090 on 2008-10-04
bump.

Help!

---

### Post by elmer_42 on 2008-10-04
If I remember correctly, [FONT="Courier New"]dd[/FONT] makes a copy of whatever you tell it to. I've used it to make ISOs. But why would it be running?

---

### Post by DocHoliday52090 on 2008-10-06
Not a clue. dd is almost constantly writing to my hard disk for apparently no reason. Indexing is off and I have no backup solutions.

Help?

---

### Post by RequinB4 on 2008-10-06
You should be able to stop dd with:

```
sudo killall dd
```

However that's a temporary and fairly ugly fix - I'm not sure why dd is even running - do you ever remember running any kind of partitioning or hardware program?

---

### Post by DocHoliday52090 on 2008-10-06
Not that I know of. Is there any way of seeing what is calling up dd?

---

### Post by DocHoliday52090 on 2008-10-06
That quieted the hard drive a bit, but it's still working like crazy. Here's an updated dmesg with dd killed:

```
[14418.166208] kswapd0(196): WRITE block 429984 on sda6
[14418.166213] kswapd0(196): WRITE block 429992 on sda6
[14418.166218] kswapd0(196): WRITE block 430000 on sda6
[14418.166259] kswapd0(196): WRITE block 430008 on sda6
[14418.166269] kswapd0(196): WRITE block 430016 on sda6
[14418.166274] kswapd0(196): WRITE block 430024 on sda6
[14418.166280] kswapd0(196): WRITE block 430032 on sda6
[14418.166285] kswapd0(196): WRITE block 430040 on sda6
[14418.166290] kswapd0(196): WRITE block 430048 on sda6
[14418.166295] kswapd0(196): WRITE block 430056 on sda6
[14418.166300] kswapd0(196): WRITE block 430064 on sda6
[14418.166305] kswapd0(196): WRITE block 430072 on sda6
[14418.166310] kswapd0(196): WRITE block 430080 on sda6
[14418.166538] kswapd0(196): WRITE block 430088 on sda6
[14418.166543] kswapd0(196): WRITE block 430096 on sda6
[14418.166549] kswapd0(196): WRITE block 430104 on sda6
[14418.166553] kswapd0(196): WRITE block 430112 on sda6
[14418.166558] kswapd0(196): WRITE block 430120 on sda6
[14418.166563] kswapd0(196): WRITE block 430128 on sda6
[14418.166570] kswapd0(196): WRITE block 430136 on sda6
[14418.166575] kswapd0(196): WRITE block 430144 on sda6
[14418.166580] kswapd0(196): WRITE block 430152 on sda6
[14418.166585] kswapd0(196): WRITE block 430160 on sda6
[14418.166590] kswapd0(196): WRITE block 430168 on sda6
[14418.166595] kswapd0(196): WRITE block 430176 on sda6
[14418.166602] kswapd0(196): WRITE block 430184 on sda6
[14418.169002] kswapd0(196): WRITE block 430192 on sda6
[14418.169016] kswapd0(196): WRITE block 430200 on sda6
[14418.169022] kswapd0(196): WRITE block 430208 on sda6
[14418.169027] kswapd0(196): WRITE block 430216 on sda6
[14418.169032] kswapd0(196): WRITE block 430224 on sda6
[14418.169036] kswapd0(196): WRITE block 430232 on sda6
[14418.169041] kswapd0(196): WRITE block 430240 on sda6
[14418.169046] kswapd0(196): WRITE block 430248 on sda6
[14418.169051] kswapd0(196): WRITE block 430256 on sda6
[14418.169056] kswapd0(196): WRITE block 430264 on sda6
[14418.169061] kswapd0(196): WRITE block 430272 on sda6
[14418.169066] kswapd0(196): WRITE block 430280 on sda6
[14418.169071] kswapd0(196): WRITE block 430288 on sda6
[14418.169075] kswapd0(196): WRITE block 430296 on sda6
[14418.169080] kswapd0(196): WRITE block 430304 on sda6
[14418.169085] kswapd0(196): WRITE block 430312 on sda6
[14418.169090] kswapd0(196): WRITE block 430320 on sda6
[14418.169095] kswapd0(196): WRITE block 430328 on sda6
[14418.169100] kswapd0(196): WRITE block 430336 on sda6
[14418.169105] kswapd0(196): WRITE block 430344 on sda6
[14418.169110] kswapd0(196): WRITE block 430352 on sda6
[14418.169115] kswapd0(196): WRITE block 430360 on sda6
[14418.169120] kswapd0(196): WRITE block 430368 on sda6
[14418.169125] kswapd0(196): WRITE block 430376 on sda6
[14418.169129] kswapd0(196): WRITE block 430384 on sda6
[14418.169134] kswapd0(196): WRITE block 430392 on sda6
[14418.169139] kswapd0(196): WRITE block 430400 on sda6
[14418.169144] kswapd0(196): WRITE block 430408 on sda6
[14418.169149] kswapd0(196): WRITE block 430416 on sda6
[14418.169154] kswapd0(196): WRITE block 430424 on sda6
[14418.169159] kswapd0(196): WRITE block 430432 on sda6
[14418.169164] kswapd0(196): WRITE block 430440 on sda6
[14418.169851] kswapd0(196): WRITE block 430448 on sda6
[14418.169859] kswapd0(196): WRITE block 430456 on sda6
[14418.169865] kswapd0(196): WRITE block 430464 on sda6
[14418.169870] kswapd0(196): WRITE block 430472 on sda6
[14418.169875] kswapd0(196): WRITE block 430480 on sda6
[14418.169879] kswapd0(196): WRITE block 430488 on sda6
[14418.169884] kswapd0(196): WRITE block 430496 on sda6
[14418.169889] kswapd0(196): WRITE block 430504 on sda6
[14418.169894] kswapd0(196): WRITE block 430512 on sda6
[14418.169899] kswapd0(196): WRITE block 430520 on sda6
[14418.169904] kswapd0(196): WRITE block 430528 on sda6
[14418.169909] kswapd0(196): WRITE block 430536 on sda6
[14418.169913] kswapd0(196): WRITE block 430544 on sda6
[14418.169918] kswapd0(196): WRITE block 430552 on sda6
[14418.169923] kswapd0(196): WRITE block 430560 on sda6
[14418.169928] kswapd0(196): WRITE block 430568 on sda6
[14418.169933] kswapd0(196): WRITE block 430576 on sda6
[14418.169938] kswapd0(196): WRITE block 430584 on sda6
[14418.169943] kswapd0(196): WRITE block 430592 on sda6
[14418.169948] kswapd0(196): WRITE block 430600 on sda6
[14418.169953] kswapd0(196): WRITE block 430608 on sda6
[14418.169958] kswapd0(196): WRITE block 430616 on sda6
[14418.169963] kswapd0(196): WRITE block 430624 on sda6
[14418.169987] kswapd0(196): WRITE block 430632 on sda6
[14418.169993] kswapd0(196): WRITE block 430640 on sda6
[14418.169997] kswapd0(196): WRITE block 430648 on sda6
[14418.170002] kswapd0(196): WRITE block 430656 on sda6
[14418.170007] kswapd0(196): WRITE block 430664 on sda6
[14418.170012] kswapd0(196): WRITE block 430672 on sda6
[14418.170017] kswapd0(196): WRITE block 430680 on sda6
[14418.170022] kswapd0(196): WRITE block 430688 on sda6
[14418.170027] kswapd0(196): WRITE block 430696 on sda6
[14418.170032] kswapd0(196): WRITE block 430704 on sda6
[14418.170038] kswapd0(196): WRITE block 430712 on sda6
[14418.170043] kswapd0(196): WRITE block 430720 on sda6
[14418.170048] kswapd0(196): WRITE block 430728 on sda6
[14418.170053] kswapd0(196): WRITE block 430736 on sda6
[14418.170057] kswapd0(196): WRITE block 430744 on sda6
[14418.170062] kswapd0(196): WRITE block 430752 on sda6
[14418.170067] kswapd0(196): WRITE block 430760 on sda6
[14418.170074] kswapd0(196): WRITE block 430768 on sda6
[14418.170079] kswapd0(196): WRITE block 430776 on sda6
[14418.170084] kswapd0(196): WRITE block 430784 on sda6
[14418.170089] kswapd0(196): WRITE block 430792 on sda6
[14418.170094] kswapd0(196): WRITE block 430800 on sda6
[14418.170099] kswapd0(196): WRITE block 430808 on sda6
[14418.170104] kswapd0(196): WRITE block 430816 on sda6
[14418.170109] kswapd0(196): WRITE block 430824 on sda6
[14418.170114] kswapd0(196): WRITE block 430832 on sda6
[14418.170119] kswapd0(196): WRITE block 430840 on sda6
[14418.170124] kswapd0(196): WRITE block 430848 on sda6
[14418.170129] kswapd0(196): WRITE block 430856 on sda6
[14418.170134] kswapd0(196): WRITE block 430864 on sda6
[14418.170139] kswapd0(196): WRITE block 430872 on sda6
[14418.170144] kswapd0(196): WRITE block 430880 on sda6
[14418.172713] kswapd0(196): WRITE block 430888 on sda6
[14418.172721] kswapd0(196): WRITE block 430896 on sda6
[14418.172726] kswapd0(196): WRITE block 430904 on sda6
[14418.172730] kswapd0(196): WRITE block 430912 on sda6
[14418.172735] kswapd0(196): WRITE block 430920 on sda6
[14418.172740] kswapd0(196): WRITE block 430928 on sda6
[14418.172745] kswapd0(196): WRITE block 430936 on sda6
[14418.172750] kswapd0(196): WRITE block 430944 on sda6
[14418.172755] kswapd0(196): WRITE block 430952 on sda6
[14418.172760] kswapd0(196): WRITE block 430960 on sda6
[14418.172766] kswapd0(196): WRITE block 430968 on sda6
[14418.172771] kswapd0(196): WRITE block 430976 on sda6
[14418.172776] kswapd0(196): WRITE block 430984 on sda6
[14418.172781] kswapd0(196): WRITE block 430992 on sda6
[14418.172786] kswapd0(196): WRITE block 431000 on sda6
[14418.172790] kswapd0(196): WRITE block 431008 on sda6
[14418.172796] kswapd0(196): WRITE block 431016 on sda6
[14418.172800] kswapd0(196): WRITE block 431024 on sda6
[14418.172805] kswapd0(196): WRITE block 431032 on sda6
[14418.172810] kswapd0(196): WRITE block 431040 on sda6
[14418.172815] kswapd0(196): WRITE block 431048 on sda6
[14418.172820] kswapd0(196): WRITE block 431056 on sda6
[14418.172825] kswapd0(196): WRITE block 431064 on sda6
[14418.172830] kswapd0(196): WRITE block 431072 on sda6
[14418.172835] kswapd0(196): WRITE block 431080 on sda6
[14418.172839] kswapd0(196): WRITE block 431088 on sda6
[14418.172844] kswapd0(196): WRITE block 431096 on sda6
[14418.172849] kswapd0(196): WRITE block 431104 on sda6
[14418.172855] kswapd0(196): WRITE block 431112 on sda6
[14418.172859] kswapd0(196): WRITE block 431120 on sda6
[14418.172864] kswapd0(196): WRITE block 431128 on sda6
[14418.172869] kswapd0(196): WRITE block 431136 on sda6
[14418.175659] kswapd0(196): WRITE block 431144 on sda6
[14418.175666] kswapd0(196): WRITE block 431152 on sda6
[14418.175671] kswapd0(196): WRITE block 431160 on sda6
[14418.175676] kswapd0(196): WRITE block 431168 on sda6
[14418.175680] kswapd0(196): WRITE block 431176 on sda6
[14418.175686] kswapd0(196): WRITE block 431184 on sda6
[14418.175690] kswapd0(196): WRITE block 431192 on sda6
[14418.175695] kswapd0(196): WRITE block 431200 on sda6
[14418.175700] kswapd0(196): WRITE block 431208 on sda6
[14418.175705] kswapd0(196): WRITE block 431216 on sda6
[14418.175711] kswapd0(196): WRITE block 431224 on sda6
[14418.175716] kswapd0(196): WRITE block 431232 on sda6
[14418.175721] kswapd0(196): WRITE block 431240 on sda6
[14418.175726] kswapd0(196): WRITE block 431248 on sda6
[14418.175731] kswapd0(196): WRITE block 431256 on sda6
[14418.175736] kswapd0(196): WRITE block 431264 on sda6
[14418.175740] kswapd0(196): WRITE block 431272 on sda6
[14418.175745] kswapd0(196): WRITE block 431280 on sda6
[14418.175760] kswapd0(196): WRITE block 431288 on sda6
[14418.175764] kswapd0(196): WRITE block 431296 on sda6
[14418.175769] kswapd0(196): WRITE block 431304 on sda6
[14418.175774] kswapd0(196): WRITE block 431312 on sda6
[14418.175779] kswapd0(196): WRITE block 431320 on sda6
[14418.175784] kswapd0(196): WRITE block 431328 on sda6
[14418.175788] kswapd0(196): WRITE block 431336 on sda6
[14418.175793] kswapd0(196): WRITE block 431344 on sda6
[14418.176358] kswapd0(196): WRITE block 431352 on sda6
[14418.176364] kswapd0(196): WRITE block 431360 on sda6
[14418.176369] kswapd0(196): WRITE block 431368 on sda6
[14418.176374] kswapd0(196): WRITE block 431376 on sda6
[14418.176379] kswapd0(196): WRITE block 431384 on sda6
[14418.176384] kswapd0(196): WRITE block 431392 on sda6
[14418.176389] kswapd0(196): WRITE block 431400 on sda6
[14418.176394] kswapd0(196): WRITE block 431408 on sda6
[14418.176399] kswapd0(196): WRITE block 431416 on sda6
[14418.176404] kswapd0(196): WRITE block 431424 on sda6
[14418.176409] kswapd0(196): WRITE block 431432 on sda6
[14418.176414] kswapd0(196): WRITE block 431440 on sda6
[14418.176419] kswapd0(196): WRITE block 431448 on sda6
[14418.176423] kswapd0(196): WRITE block 431456 on sda6
[14418.252070] Xorg(6302): READ block 392224 on sda6
[14418.252092] Xorg(6302): READ block 392232 on sda6
[14418.252099] Xorg(6302): READ block 392240 on sda6
[14418.252103] Xorg(6302): READ block 392248 on sda6
[14418.262997] banshee-1(17423): READ block 7862104 on sda5
[14418.297930] banshee-1(17423): READ block 7862664 on sda5
[14418.305118] banshee-1(17423): READ block 7862848 on sda5
[14418.308998] banshee-1(17423): READ block 24720592 on sda5
[14418.309212] banshee-1(17423): READ block 24720600 on sda5
[14418.309423] banshee-1(17423): READ block 24720608 on sda5
[14418.309650] banshee-1(17423): READ block 24720616 on sda5
[14418.309877] banshee-1(17423): READ block 24720624 on sda5
[14418.310103] banshee-1(17423): READ block 24720632 on sda5
[14418.310326] banshee-1(17423): READ block 24720640 on sda5
[14418.310567] banshee-1(17423): READ block 24720752 on sda5
[14418.310777] banshee-1(17423): READ block 24720760 on sda5
[14418.311068] banshee-1(17423): READ block 24737056 on sda5
[14418.311307] banshee-1(17423): READ block 24737064 on sda5
[14418.311527] banshee-1(17423): READ block 24737072 on sda5
[14418.311754] banshee-1(17423): READ block 24737080 on sda5
[14418.311978] banshee-1(17423): READ block 24737088 on sda5
[14418.312203] banshee-1(17423): READ block 24737096 on sda5
[14418.312423] banshee-1(17423): READ block 24737104 on sda5
[14418.312654] banshee-1(17423): READ block 24737208 on sda5
[14418.312872] banshee-1(17423): READ block 24737224 on sda5
[14418.313100] banshee-1(17423): READ block 24737256 on sda5
[14418.313329] banshee-1(17423): READ block 24739872 on sda5
[14418.328937] banshee-1(17423): READ block 24772944 on sda5
[14418.331200] banshee-1(17423): READ block 36503488 on sda5
[14418.346549] banshee-1(17423): READ block 36503504 on sda5
[14418.346746] banshee-1(17423): READ block 36503512 on sda5
[14418.346943] banshee-1(17423): READ block 36503520 on sda5
[14418.347100] banshee-1(17423): READ block 37182968 on sda5
[14418.357748] banshee-1(17423): READ block 37888352 on sda5
[14418.371607] banshee-1(17423): READ block 37888416 on sda5
[14418.372296] banshee-1(17423): READ block 37889336 on sda5
[14418.387630] banshee-1(17423): READ block 37889344 on sda5
[14418.387807] banshee-1(17423): READ block 37889384 on sda5
[14418.389802] banshee-1(17423): READ block 37889512 on sda5
[14418.392051] banshee-1(17423): READ block 37889728 on sda5
[14418.394964] banshee-1(17423): READ block 37889768 on sda5
[14418.395564] banshee-1(17423): READ block 37937152 on sda5
[14418.469898] smbd(29861): WRITE block 8028792 on sda5
[14418.469923] smbd(29861): WRITE block 8028800 on sda5
[14418.472083] kjournald(2158): WRITE block 53844168 on sda5
[14418.472094] kjournald(2158): WRITE block 24720584 on sda5
[14418.472099] kjournald(2158): WRITE block 53844208 on sda5
[14418.472189] kjournald(2158): WRITE block 53848528 on sda5
[14418.472195] kjournald(2158): WRITE block 6868432 on sda5
[14418.472199] kjournald(2158): WRITE block 7860848 on sda5
[14418.472204] kjournald(2158): WRITE block 7861592 on sda5
[14418.472208] kjournald(2158): WRITE block 7861920 on sda5
[14418.472213] kjournald(2158): WRITE block 24737112 on sda5
[14418.472218] kjournald(2158): WRITE block 7862104 on sda5
[14418.472222] kjournald(2158): WRITE block 7862664 on sda5
[14418.472227] kjournald(2158): WRITE block 7862848 on sda5
[14418.472231] kjournald(2158): WRITE block 7863048 on sda5
[14418.472235] kjournald(2158): WRITE block 24720592 on sda5
[14418.472240] kjournald(2158): WRITE block 24720600 on sda5
[14418.472244] kjournald(2158): WRITE block 24720608 on sda5
[14418.472248] kjournald(2158): WRITE block 24720616 on sda5
[14418.472251] kjournald(2158): WRITE block 24720624 on sda5
[14418.472255] kjournald(2158): WRITE block 24720632 on sda5
[14418.472258] kjournald(2158): WRITE block 24720640 on sda5
[14418.472262] kjournald(2158): WRITE block 24720648 on sda5
[14418.472265] kjournald(2158): WRITE block 24720752 on sda5
[14418.472270] kjournald(2158): WRITE block 24720760 on sda5
[14418.472273] kjournald(2158): WRITE block 24737056 on sda5
[14418.472277] kjournald(2158): WRITE block 24737064 on sda5
[14418.472281] kjournald(2158): WRITE block 24737072 on sda5
[14418.472284] kjournald(2158): WRITE block 24737080 on sda5
[14418.472288] kjournald(2158): WRITE block 24737088 on sda5
[14418.472291] kjournald(2158): WRITE block 24737096 on sda5
[14418.472383] kjournald(2158): WRITE block 24737104 on sda5
[14418.472388] kjournald(2158): WRITE block 24737208 on sda5
[14418.472393] kjournald(2158): WRITE block 24737224 on sda5
[14418.472397] kjournald(2158): WRITE block 24737256 on sda5
[14418.472402] kjournald(2158): WRITE block 24739872 on sda5
[14418.472406] kjournald(2158): WRITE block 24772944 on sda5
[14418.472410] kjournald(2158): WRITE block 36503488 on sda5
[14418.472415] kjournald(2158): WRITE block 36503504 on sda5
[14418.472420] kjournald(2158): WRITE block 36503512 on sda5
[14418.472423] kjournald(2158): WRITE block 36503520 on sda5
[14418.472427] kjournald(2158): WRITE block 37182968 on sda5
[14418.472431] kjournald(2158): WRITE block 37888352 on sda5
[14418.472435] kjournald(2158): WRITE block 37888416 on sda5
[14418.472440] kjournald(2158): WRITE block 37889336 on sda5
[14418.472445] kjournald(2158): WRITE block 37889344 on sda5
[14418.472448] kjournald(2158): WRITE block 37889384 on sda5
[14418.472453] kjournald(2158): WRITE block 37889512 on sda5
[14418.472457] kjournald(2158): WRITE block 37889728 on sda5
[14418.472461] kjournald(2158): WRITE block 37889768 on sda5
[14418.472466] kjournald(2158): WRITE block 37937152 on sda5
[14418.472470] kjournald(2158): WRITE block 17099696 on sda5
[14418.472474] kjournald(2158): WRITE block 17099704 on sda5
[14418.480067] kjournald(2158): WRITE block 51192 on sda5
[14418.480095] kjournald(2158): WRITE block 51200 on sda5
[14418.480100] kjournald(2158): WRITE block 51208 on sda5
[14418.480103] kjournald(2158): WRITE block 51216 on sda5
[14418.480106] kjournald(2158): WRITE block 51224 on sda5
[14418.480109] kjournald(2158): WRITE block 51232 on sda5
[14418.480113] kjournald(2158): WRITE block 51240 on sda5
[14418.480116] kjournald(2158): WRITE block 51248 on sda5
[14418.480119] kjournald(2158): WRITE block 51256 on sda5
[14418.480122] kjournald(2158): WRITE block 51264 on sda5
[14418.480125] kjournald(2158): WRITE block 51272 on sda5
[14418.480128] kjournald(2158): WRITE block 51280 on sda5
[14418.480132] kjournald(2158): WRITE block 51288 on sda5
[14418.480135] kjournald(2158): WRITE block 51296 on sda5
[14418.480138] kjournald(2158): WRITE block 51304 on sda5
[14418.481550] kjournald(2158): WRITE block 51312 on sda5
[14418.481786] smbd(29861): dirtied inode 491521 (share_info.tdb) on sda5
[14418.481800] smbd(29861): WRITE block 8028792 on sda5
[14418.482075] smbd(29861): WRITE block 8011800 on sda5
[14418.482286] smbd(29861): WRITE block 8028792 on sda5
[14418.482537] smbd(29861): dirtied inode 491521 (share_info.tdb) on sda5
[14418.930211] banshee-1(17405): READ block 52952872 on sda5
[14418.930231] banshee-1(17405): READ block 52953072 on sda5
[14418.930238] banshee-1(17405): READ block 53079080 on sda5
[14418.949885] banshee-1(17405): READ block 53079096 on sda5
[14419.442310] banshee-1(17423): dirtied inode 3187001 (banshee.db-journal) on sda5
[14419.787963] banshee-1(18690): READ block 2573376 on sda5
[14419.924859] notification-da(6956): READ block 91840 on sda6
[14419.924880] notification-da(6956): READ block 91848 on sda6
[14419.924887] notification-da(6956): READ block 91856 on sda6
[14419.924892] notification-da(6956): READ block 91864 on sda6
[14419.924896] notification-da(6956): READ block 91872 on sda6
[14419.924900] notification-da(6956): READ block 91880 on sda6
[14419.924905] notification-da(6956): READ block 91888 on sda6
[14419.924909] notification-da(6956): READ block 91896 on sda6
[14420.084095] Xorg(6302): READ block 419136 on sda6
[14420.084200] Xorg(6302): READ block 419144 on sda6
[14420.084207] Xorg(6302): READ block 419152 on sda6
[14420.084213] Xorg(6302): READ block 419160 on sda6
[14420.084217] Xorg(6302): READ block 419168 on sda6
[14420.084221] Xorg(6302): READ block 419176 on sda6
[14420.084225] Xorg(6302): READ block 419184 on sda6
[14420.084229] Xorg(6302): READ block 419192 on sda6
[14420.128285] pdflush(195): WRITE block 50643760 on sda5
[14420.128319] pdflush(195): WRITE block 8 on sda5
[14420.128327] pdflush(195): WRITE block 6815744 on sda5
[14420.128333] pdflush(195): WRITE block 6815752 on sda5
[14420.128339] pdflush(195): WRITE block 6815760 on sda5
[14420.128343] pdflush(195): WRITE block 6815768 on sda5
[14420.128347] pdflush(195): WRITE block 6815776 on sda5
[14420.128351] pdflush(195): WRITE block 6815792 on sda5
[14420.128438] pdflush(195): WRITE block 6815848 on sda5
[14420.128444] pdflush(195): WRITE block 6815864 on sda5
[14420.128449] pdflush(195): WRITE block 6815872 on sda5
[14420.128453] pdflush(195): WRITE block 6815888 on sda5
[14420.128458] pdflush(195): WRITE block 6996168 on sda5
[14420.128483] pdflush(195): WRITE block 7086128 on sda5
[14420.128488] pdflush(195): WRITE block 7602392 on sda5
[14420.128494] pdflush(195): WRITE block 9175056 on sda5
[14420.128499] pdflush(195): WRITE block 9521048 on sda5
[14420.128504] pdflush(195): WRITE block 17039360 on sda5
[14420.128512] pdflush(195): WRITE block 17099472 on sda5
[14420.128517] pdflush(195): WRITE block 17122952 on sda5
[14420.128522] pdflush(195): WRITE block 17825792 on sda5
[14420.128526] pdflush(195): WRITE block 18350080 on sda5
[14420.128531] pdflush(195): WRITE block 18361280 on sda5
[14420.128536] pdflush(195): WRITE block 18377680 on sda5
[14420.128541] pdflush(195): WRITE block 18378512 on sda5
[14420.128546] pdflush(195): WRITE block 18394096 on sda5
[14420.128561] pdflush(195): WRITE block 48758784 on sda5
[14420.128652] pdflush(195): WRITE block 48758792 on sda5
[14420.128657] pdflush(195): WRITE block 48758800 on sda5
[14420.128661] pdflush(195): WRITE block 50593792 on sda5
[14420.128667] pdflush(195): WRITE block 50593800 on sda5
[14420.128671] pdflush(195): WRITE block 50593808 on sda5
[14420.128675] pdflush(195): WRITE block 50593928 on sda5
[14420.128680] pdflush(195): WRITE block 50593960 on sda5
[14420.128684] pdflush(195): WRITE block 50594072 on sda5
[14420.128689] pdflush(195): WRITE block 50594640 on sda5
[14420.128694] pdflush(195): WRITE block 50595120 on sda5
[14420.128698] pdflush(195): WRITE block 50597904 on sda5
[14420.128703] pdflush(195): WRITE block 50696224 on sda5
[14420.128708] pdflush(195): WRITE block 50790408 on sda5
[14420.128725] pdflush(195): WRITE block 50841416 on sda5
[14420.128735] pdflush(195): WRITE block 53477376 on sda5
[14420.128740] pdflush(195): WRITE block 53477384 on sda5
[14420.128745] pdflush(195): WRITE block 53477392 on sda5
[14420.128748] pdflush(195): WRITE block 53477464 on sda5
[14420.128755] pdflush(195): WRITE block 53477552 on sda5
[14420.128761] pdflush(195): WRITE block 53543328 on sda5
[14420.128767] pdflush(195): WRITE block 54140616 on sda5
[14420.128775] pdflush(195): WRITE block 58458120 on sda5
[14420.128780] pdflush(195): WRITE block 58459480 on sda5
[14420.141174] notification-da(6956): READ block 92168 on sda6
[14420.141189] notification-da(6956): READ block 92176 on sda6
[14420.721113] Xorg(6302): READ block 420288 on sda6
[14420.721217] Xorg(6302): READ block 420296 on sda6
[14420.721223] Xorg(6302): READ block 420304 on sda6
[14420.721229] Xorg(6302): READ block 420312 on sda6
[14420.721233] Xorg(6302): READ block 420320 on sda6
[14420.721237] Xorg(6302): READ block 420328 on sda6
[14420.721240] Xorg(6302): READ block 420336 on sda6
[14420.721245] Xorg(6302): READ block 420344 on sda6
[14420.735927] banshee-1(29848): dirtied inode 3165443 (shared_data-laptop-Linux-i686-312-11-0) on sda5
[14420.736192] banshee-1(29863): READ block 53641288 on sda5
[14420.751736] banshee-1(29863): READ block 53847040 on sda5
[14420.761755] banshee-1(29863): dirtied inode 3178617 (audioscrobbler-queue.xml) on sda5
[14420.761781] banshee-1(29863): dirtied inode 3165672 (shared_fileshare-laptop-Linux-i686-36-11-0) on sda5
[14420.761787] banshee-1(29863): dirtied inode 3165672 (shared_fileshare-laptop-Linux-i686-36-11-0) on sda5
[14421.082941] nm-applet(6907): READ block 138816 on sda6
[14421.083043] nm-applet(6907): READ block 138824 on sda6
[14421.083049] nm-applet(6907): READ block 138832 on sda6
[14421.083055] nm-applet(6907): READ block 138856 on sda6
[14421.098071] nm-applet(6907): READ block 84224 on sda6
[14421.098140] nm-applet(6907): READ block 84232 on sda6
[14421.098145] nm-applet(6907): READ block 84240 on sda6
[14421.098150] nm-applet(6907): READ block 84256 on sda6
[14421.098155] nm-applet(6907): READ block 84264 on sda6
[14421.098158] nm-applet(6907): READ block 84272 on sda6
[14421.098162] nm-applet(6907): READ block 84280 on sda6
[14421.109105] nm-applet(6907): READ block 138624 on sda6
[14421.109184] nm-applet(6907): READ block 138632 on sda6
[14421.109189] nm-applet(6907): READ block 138640 on sda6
[14421.109197] nm-applet(6907): READ block 138656 on sda6
[14421.109202] nm-applet(6907): READ block 138664 on sda6
[14421.109206] nm-applet(6907): READ block 138672 on sda6
[14421.109210] nm-applet(6907): READ block 138680 on sda6
[14421.109832] nm-applet(6907): READ block 174784 on sda6
[14421.109899] nm-applet(6907): READ block 174792 on sda6
[14421.109904] nm-applet(6907): READ block 174800 on sda6
[14421.109908] nm-applet(6907): READ block 174816 on sda6
[14421.109913] nm-applet(6907): READ block 174824 on sda6
[14421.109917] nm-applet(6907): READ block 174832 on sda6
[14421.109921] nm-applet(6907): READ block 174840 on sda6
[14421.434322] nmbd(5994): dirtied inode 426498 (browse.dat.) on sda5
[14421.444307] banshee-1(17405): READ block 345408 on sda6
[14421.444411] banshee-1(17405): READ block 345416 on sda6
[14421.444419] banshee-1(17405): READ block 345424 on sda6
[14421.444426] banshee-1(17405): READ block 345432 on sda6
[14421.444430] banshee-1(17405): READ block 345440 on sda6
[14421.444434] banshee-1(17405): READ block 345448 on sda6
[14421.444438] banshee-1(17405): READ block 345456 on sda6
[14421.444442] banshee-1(17405): READ block 345464 on sda6
[14421.454055] banshee-1(17405): READ block 336312 on sda6
[14421.465979] Xorg(6302): READ block 426048 on sda6
[14421.466055] Xorg(6302): READ block 426056 on sda6
[14421.466060] Xorg(6302): READ block 426064 on sda6
[14421.466066] Xorg(6302): READ block 426072 on sda6
[14421.466070] Xorg(6302): READ block 426080 on sda6
[14421.466073] Xorg(6302): READ block 426088 on sda6
[14421.466077] Xorg(6302): READ block 426096 on sda6
[14421.466081] Xorg(6302): READ block 426104 on sda6
[14421.931649] smbd(29869): WRITE block 8028792 on sda5
[14421.931676] smbd(29869): WRITE block 8028800 on sda5
[14421.932104] kjournald(2158): WRITE block 53844168 on sda5
[14421.932111] kjournald(2158): WRITE block 24720584 on sda5
[14421.932116] kjournald(2158): WRITE block 50643760 on sda5
[14421.932205] kjournald(2158): WRITE block 54140960 on sda5
[14421.932210] kjournald(2158): WRITE block 7014384 on sda5
[14421.932214] kjournald(2158): WRITE block 7043656 on sda5
[14421.932219] kjournald(2158): WRITE block 17099704 on sda5
[14421.933767] kjournald(2158): WRITE block 51320 on sda5
[14421.933774] kjournald(2158): WRITE block 51328 on sda5
[14421.933778] kjournald(2158): WRITE block 51336 on sda5
[14421.933781] kjournald(2158): WRITE block 51344 on sda5
[14421.933784] kjournald(2158): WRITE block 51352 on sda5
[14421.933787] kjournald(2158): WRITE block 51360 on sda5
[14421.933790] kjournald(2158): WRITE block 51368 on sda5
[14421.933794] kjournald(2158): WRITE block 51376 on sda5
[14421.933797] kjournald(2158): WRITE block 51384 on sda5
[14421.933800] kjournald(2158): WRITE block 51392 on sda5
[14421.933803] kjournald(2158): WRITE block 51400 on sda5
[14421.933807] kjournald(2158): WRITE block 51408 on sda5
[14421.933810] kjournald(2158): WRITE block 51416 on sda5
[14421.933813] kjournald(2158): WRITE block 51424 on sda5
[14421.933817] kjournald(2158): WRITE block 51432 on sda5
[14421.933820] kjournald(2158): WRITE block 51440 on sda5
[14421.933823] kjournald(2158): WRITE block 51448 on sda5
[14421.933827] kjournald(2158): WRITE block 51456 on sda5
[14421.933830] kjournald(2158): WRITE block 51464 on sda5
[14421.933833] kjournald(2158): WRITE block 51472 on sda5
[14421.935655] kjournald(2158): WRITE block 51480 on sda5
[14421.935872] smbd(29869): dirtied inode 491521 (share_info.tdb) on sda5
[14421.935881] smbd(29869): WRITE block 8028792 on sda5
[14421.936368] smbd(29869): WRITE block 8011800 on sda5
[14421.936592] smbd(29869): WRITE block 8028792 on sda5
[14421.936838] smbd(29869): dirtied inode 491521 (share_info.tdb) on sda5
[14421.956705] smbd(29870): WRITE block 8028792 on sda5
[14421.956733] smbd(29870): WRITE block 8028800 on sda5
[14421.960052] kjournald(2158): WRITE block 17099704 on sda5
[14421.960602] kjournald(2158): WRITE block 51488 on sda5
[14421.960608] kjournald(2158): WRITE block 51496 on sda5
[14421.960611] kjournald(2158): WRITE block 51504 on sda5
[14421.960976] kjournald(2158): WRITE block 51512 on sda5
[14421.961198] smbd(29870): dirtied inode 491521 (share_info.tdb) on sda5
[14421.961206] smbd(29870): WRITE block 8028792 on sda5
[14421.961434] smbd(29870): WRITE block 8011800 on sda5
[14421.961635] smbd(29870): WRITE block 8028792 on sda5
[14421.961873] smbd(29870): dirtied inode 491521 (share_info.tdb) on sda5
[14423.424446] smbd(29871): WRITE block 8028792 on sda5
[14423.424472] smbd(29871): WRITE block 8028800 on sda5
[14423.428049] kjournald(2158): WRITE block 17099704 on sda5
[14423.433063] kjournald(2158): WRITE block 51520 on sda5
[14423.433069] kjournald(2158): WRITE block 51528 on sda5
[14423.433072] kjournald(2158): WRITE block 51536 on sda5
[14423.433430] kjournald(2158): WRITE block 51544 on sda5
[14423.434141] smbd(29871): dirtied inode 491521 (share_info.tdb) on sda5
[14423.434149] smbd(29871): WRITE block 8028792 on sda5
[14423.434349] smbd(29871): WRITE block 8011800 on sda5
[14423.434540] smbd(29871): WRITE block 8028792 on sda5
[14423.434742] smbd(29871): dirtied inode 491521 (share_info.tdb) on sda5
[14423.951323] smbd(29872): WRITE block 8028792 on sda5
[14423.951350] smbd(29872): WRITE block 8028800 on sda5
[14423.952042] kjournald(2158): WRITE block 17099704 on sda5
[14423.952548] kjournald(2158): WRITE block 51552 on sda5
[14423.952554] kjournald(2158): WRITE block 51560 on sda5
[14423.952558] kjournald(2158): WRITE block 51568 on sda5
[14423.952924] kjournald(2158): WRITE block 51576 on sda5
[14423.953146] smbd(29872): dirtied inode 491521 (share_info.tdb) on sda5
[14423.953154] smbd(29872): WRITE block 8028792 on sda5
[14423.953373] smbd(29872): WRITE block 8011800 on sda5
[14423.953579] smbd(29872): WRITE block 8028792 on sda5
[14423.953819] smbd(29872): dirtied inode 491521 (share_info.tdb) on sda5
[14429.000064] kjournald(2158): WRITE block 51584 on sda5
[14429.000082] kjournald(2158): WRITE block 51592 on sda5
[14429.003609] kjournald(2158): WRITE block 51600 on sda5

```

---

### Post by taladan on 2008-10-06
from my output of ps -ef|grep dd, it looks like dd is being used to copy the output of proc messages to log files...so that's likely something you do want running in the bg.  I haven't heard anyone having problems with it running away with the system though until your issue.  Is it possible you have something running to log files that is running away and calling dd?

Tal

---

### Post by DocHoliday52090 on 2008-10-06
Look at the log above your post. I killed dd but it hasn't been fixed. I think it's all those pdflush, kswap, kjournald, etc that's the problem.

---

### Post by ions on 2008-10-25
I had a problem with the CPU hitting high temps so I looked into it and dd and klogd were having a party. Not knowing whether it was crucial for dd and klogd to be running I did a killall -1 to restart them.  CPU temps dropped considerably.

Whether it's related or not I noticed this in my dmesg:

```
[ 8180.485099] Call Trace:
[ 8180.485106]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.485111]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.485117]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.485123]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.485131]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.485137]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.485141] 
[ 8180.486021] bad: scheduling from the idle thread!
[ 8180.486030] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.486035] 
[ 8180.486036] Call Trace:
[ 8180.486045]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.486051]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.486057]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.486064]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.486072]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.486078]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.486082] 
[ 8180.487685] bad: scheduling from the idle thread!
[ 8180.487693] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.487697] 
[ 8180.487698] Call Trace:
[ 8180.487706]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.487712]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.487718]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.487725]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.487733]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.487739]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.487744] 
[ 8180.500159] bad: scheduling from the idle thread!
[ 8180.500171] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.500175] 
[ 8180.500176] Call Trace:
[ 8180.500188]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.500194]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.500200]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.500208]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.500217]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.500224]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.500229] 
[ 8180.513071] bad: scheduling from the idle thread!
[ 8180.513082] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.513086] 
[ 8180.513088] Call Trace:
[ 8180.513099]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.513105]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.513111]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.513120]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.513129]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.513136]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.513141] 
[ 8180.516093] bad: scheduling from the idle thread!
[ 8180.516099] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.516103] 
[ 8180.516104] Call Trace:
[ 8180.516110]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.516116]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.516122]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.516128]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.516136]  [<ffffffff80271612>] ? clockevents_notify+0x42/0xa0
[ 8180.516143]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.516149]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.516153] 
[ 8180.572171] bad: scheduling from the idle thread!
[ 8180.572183] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.572187] 
[ 8180.572188] Call Trace:
[ 8180.572199]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.572208]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.572214]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.572219]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.572227]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.572236]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.572243]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.572248] 
[ 8180.588173] bad: scheduling from the idle thread!
[ 8180.588188] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.588194] 
[ 8180.588195] Call Trace:
[ 8180.588211]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.588221]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.588228]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.588233]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.588242]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.588252]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.588259]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.588264] 
[ 8180.605162] bad: scheduling from the idle thread!
[ 8180.605172] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.605177] 
[ 8180.605178] Call Trace:
[ 8180.605189]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.605197]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.605203]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.605209]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.605217]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.605226]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.605233]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.605237] 
[ 8180.629058] bad: scheduling from the idle thread!
[ 8180.629074] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.629079] 
[ 8180.629080] Call Trace:
[ 8180.629095]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.629101]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.629107]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.629115]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.629125]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.629132]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.629136] 
[ 8180.632094] bad: scheduling from the idle thread!
[ 8180.632100] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.632104] 
[ 8180.632106] Call Trace:
[ 8180.632112]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.632118]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.632123]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.632130]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.632138]  [<ffffffff80271612>] ? clockevents_notify+0x42/0xa0
[ 8180.632145]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.632151]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.632155] 
[ 8180.640091] bad: scheduling from the idle thread!
[ 8180.640100] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.640104] 
[ 8180.640105] Call Trace:
[ 8180.640114]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.640120]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.640126]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.640133]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.640142]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.640148]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.640153] 
[ 8180.655536] bad: scheduling from the idle thread!
[ 8180.655549] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.655553] 
[ 8180.655554] Call Trace:
[ 8180.655567]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.655574]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.655579]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.655587]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.655596]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.655604]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.655608] 
[ 8180.714603] bad: scheduling from the idle thread!
[ 8180.714616] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.714620] 
[ 8180.714621] Call Trace:
[ 8180.714633]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.714639]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.714645]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.714654]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.714663]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.714671]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.714675] 
[ 8180.716141] bad: scheduling from the idle thread!
[ 8180.716151] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.716155] 
[ 8180.716156] Call Trace:
[ 8180.716167]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.716173]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.716178]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.716186]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.716194]  [<ffffffff80271612>] ? clockevents_notify+0x42/0xa0
[ 8180.716203]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.716209]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.716213] 
[ 8180.718760] bad: scheduling from the idle thread!
[ 8180.718768] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.718772] 
[ 8180.718773] Call Trace:
[ 8180.718781]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.718787]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.718793]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.718800]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.718808]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
[ 8180.718816]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.718822]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.718826] 
[ 8180.719852] bad: scheduling from the idle thread!
[ 8180.719860] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.719864] 
[ 8180.719865] Call Trace:
[ 8180.719873]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.719879]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.719885]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.719891]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.719898]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
[ 8180.719906]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.719912]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.719916] 
[ 8180.725439] bad: scheduling from the idle thread!
[ 8180.725448] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.725453] 
[ 8180.725454] Call Trace:
[ 8180.725462]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.725468]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.725474]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.725481]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.725488]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
[ 8180.725496]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.725501]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.725506] 
[ 8180.727164] bad: scheduling from the idle thread!
[ 8180.727173] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.727177] 
[ 8180.727178] Call Trace:
[ 8180.727187]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.727193]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.727198]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.727205]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.727212]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
[ 8180.727220]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.727225]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.727230] 
[ 8180.736155] bad: scheduling from the idle thread!
[ 8180.736171] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.736176] 
[ 8180.736177] Call Trace:
[ 8180.736192]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.736199]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.736204]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.736212]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.736221]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.736228]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.736233] 
[ 8180.799437] bad: scheduling from the idle thread!
[ 8180.799448] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.799453] 
[ 8180.799454] Call Trace:
[ 8180.799467]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.799475]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.799481]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.799486]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.799494]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.799503]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.799510]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.799514] 
[ 8180.816267] bad: scheduling from the idle thread!
[ 8180.816276] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.816280] 
[ 8180.816281] Call Trace:
[ 8180.816290]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.816297]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.816303]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.816309]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.816315]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.816323]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.816329]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.816333] 
[ 8180.836090] bad: scheduling from the idle thread!
[ 8180.836100] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.836105] 
[ 8180.836106] Call Trace:
[ 8180.836116]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.836122]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.836128]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.836135]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.836144]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.836151]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.836155] 
[ 8180.860339] bad: scheduling from the idle thread!
[ 8180.860353] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.860358] 
[ 8180.860360] Call Trace:
[ 8180.860377]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.860383]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.860389]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.860397]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.860406]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.860413]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.860418] 
[ 8180.868152] bad: scheduling from the idle thread!
[ 8180.868163] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.868167] 
[ 8180.868169] Call Trace:
[ 8180.868181]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.868189]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.868195]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.868201]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.868209]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.868218]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.868224]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.868229] 
[ 8180.929096] bad: scheduling from the idle thread!
[ 8180.929112] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.929117] 
[ 8180.929118] Call Trace:
[ 8180.929133]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.929142]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.929148]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.929154]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.929162]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.929171]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.929178]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.929183] 
[ 8180.958319] bad: scheduling from the idle thread!
[ 8180.958333] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.958338] 
[ 8180.958339] Call Trace:
[ 8180.958354]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.958360]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.958366]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.958374]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.958383]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.958390]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.958394] 
[ 8180.962725] bad: scheduling from the idle thread!
[ 8180.962734] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.962739] 
[ 8180.962740] Call Trace:
[ 8180.962749]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.962755]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.962761]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.962768]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.962776]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.962782]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.962787] 
[ 8180.976178] bad: scheduling from the idle thread!
[ 8180.976191] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.976195] 
[ 8180.976196] Call Trace:
[ 8180.976208]  [<ffffffff80269ea5>] ? __remove_hrtimer+0x45/0xc0
[ 8180.976216]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.976222]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.976228]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.976236]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.976245]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.976251]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.976256] 
[ 8180.990379] bad: scheduling from the idle thread!
[ 8180.990389] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.990393] 
[ 8180.990394] Call Trace:
[ 8180.990405]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.990410]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.990416]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.990423]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.990432]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.990438]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.990442] 
[ 8180.996107] bad: scheduling from the idle thread!
[ 8180.996115] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8180.996119] 
[ 8180.996120] Call Trace:
[ 8180.996129]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8180.996135]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8180.996140]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8180.996147]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8180.996155]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8180.996161]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8180.996165] 
[ 8181.002961] bad: scheduling from the idle thread!
[ 8181.002971] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.002975] 
[ 8181.002976] Call Trace:
[ 8181.002986]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.002992]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.002998]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.003004]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.003013]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.003018]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.003023] 
[ 8181.023738] bad: scheduling from the idle thread!
[ 8181.023751] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.023755] 
[ 8181.023756] Call Trace:
[ 8181.023768]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.023774]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.023779]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.023787]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.023796]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.023803]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.023808] 
[ 8181.024345] bad: scheduling from the idle thread!
[ 8181.024356] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.024360] 
[ 8181.024362] Call Trace:
[ 8181.024372]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.024378]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.024383]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.024391]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.024399]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.024406]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.024410] 
[ 8181.032070] bad: scheduling from the idle thread!
[ 8181.032077] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.032081] 
[ 8181.032082] Call Trace:
[ 8181.032089]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.032094]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.032100]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.032106]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.032114]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.032119]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.032124] 
[ 8181.050586] bad: scheduling from the idle thread!
[ 8181.050598] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.050603] 
[ 8181.050604] Call Trace:
[ 8181.050618]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.050624]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.050630]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.050638]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.050648]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.050655]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.050659] 
[ 8181.065250] bad: scheduling from the idle thread!
[ 8181.065263] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.065268] 
[ 8181.065269] Call Trace:
[ 8181.065285]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.065291]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.065297]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.065305]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.065314]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.065321]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.065326] 
[ 8181.073264] bad: scheduling from the idle thread!
[ 8181.073276] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.073280] 
[ 8181.073281] Call Trace:
[ 8181.073293]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.073299]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.073305]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.073312]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.073321]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.073328]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.073332] 
[ 8181.078818] bad: scheduling from the idle thread!
[ 8181.078830] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.078834] 
[ 8181.078836] Call Trace:
[ 8181.078848]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.078854]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.078859]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.078867]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.078876]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.078883]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.078887] 
[ 8181.086570] bad: scheduling from the idle thread!
[ 8181.086583] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.086587] 
[ 8181.086588] Call Trace:
[ 8181.086600]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.086606]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.086611]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.086620]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.086629]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.086636]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.086640] 
[ 8181.096639] bad: scheduling from the idle thread!
[ 8181.096651] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.096656] 
[ 8181.096657] Call Trace:
[ 8181.096670]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.096676]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.096682]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.096690]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.096699]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.096705]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.096710] 
[ 8181.127844] bad: scheduling from the idle thread!
[ 8181.127856] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.127860] 
[ 8181.127862] Call Trace:
[ 8181.127874]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.127880]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.127885]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.127893]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.127902]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.127909]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.127914] 
[ 8181.129054] bad: scheduling from the idle thread!
[ 8181.129063] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.129067] 
[ 8181.129068] Call Trace:
[ 8181.129076]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.129082]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.129088]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.129095]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.129103]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.129109]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.129113] 
[ 8181.129537] bad: scheduling from the idle thread!
[ 8181.129543] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.129547] 
[ 8181.129548] Call Trace:
[ 8181.129555]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.129560]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.129566]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.129572]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.129581]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
[ 8181.129588]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.129594]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.129598] 
[ 8181.136418] bad: scheduling from the idle thread!
[ 8181.136431] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 8181.136435] 
[ 8181.136436] Call Trace:
[ 8181.136449]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
[ 8181.136455]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
[ 8181.136460]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
[ 8181.136468]  [<ffffffff80500685>] thread_return+0x108/0x3c3
[ 8181.136476]  [<ffffffff80271612>] ? clockevents_notify+0x42/0xa0
[ 8181.136485]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
[ 8181.136492]  [<ffffffff804f0446>] rest_init+0x66/0x70
[ 8181.136496] 

```

Edit: Using Ibex that was installed on the 24th.

And here's an interesting [link](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285).

---

### Post by eigenman on 2008-11-23
> **DocHoliday52090 said:**
> Look at the log above your post. I killed dd but it hasn't been fixed. I think it's all those pdflush, kswap, kjournald, etc that's the problem.

Well, I just want to say that I have the same problem, and I think that pdflush and kjournald are the culprits here. However, I haven't found a way of fixing them yet. My computer is responsive, however, it is making unnecessary noise.

---

