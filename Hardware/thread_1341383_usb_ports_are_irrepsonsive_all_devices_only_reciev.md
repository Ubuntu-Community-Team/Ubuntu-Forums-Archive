---
title: "usb ports are irrepsonsive all devices only recieve power but dmesg shows nothing"
date: 2009-11-29
forum: Hardware
---

### Post by scruffz on 2009-11-29
i have a dell inspiron 9200 laptop with 4 usb ports not one of them seems to work and i think i remember them working before then 9.10 update lsusb shows
 > Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and dmesg shows 
> [ 9456.000228] ipw2200 0000:02:03.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[ 9456.000253] ipw2200 0000:02:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfaffc000)
[ 9456.000258] ipw2200 0000:02:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[ 9456.000265] ipw2200 0000:02:03.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900116)
[ 9456.312999] pm_op(): pci_pm_resume+0x0/0x90 returns -16
[ 9456.313003] PM: Device 0000:00:00.0 failed to resume: error -16
[ 9456.313018] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 9456.313033] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 9456.313062] usb usb2: root hub lost power or was reset
[ 9456.313080] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 9456.313095] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 9456.313121] usb usb3: root hub lost power or was reset
[ 9456.313137] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 9456.313143] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 9456.313169] usb usb4: root hub lost power or was reset
[ 9456.313190] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9456.313196] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[ 9456.313203] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 9456.313217] usb usb1: root hub lost power or was reset
[ 9456.317103] ehci_hcd 0000:00:1d.7: debug port 1
[ 9456.317110] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[ 9456.317130] pci 0000:00:1e.0: setting latency timer to 64
[ 9456.317141] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 9456.317146] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 9456.320570] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[ 9456.320585] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 9457.312664] ata2.00: configured for UDMA/33
[ 9457.333915] pci 0000:00:1f.6: PME# disabled
[ 9457.333936] pci 0000:01:00.0: PME# disabled
[ 9457.333951] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 9457.333981] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 9457.410300] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 9457.419628] sdhci-pci 0000:02:01.2: PCI INT C -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[ 9457.420671] eth1: Coming out of suspend...
[ 9457.420694] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[ 9457.569211] ata1.00: configured for UDMA/100
[ 9457.578830] sd 0:0:0:0: [sda] Starting disk
[ 9457.600416] PM: resume devices took 1.600 seconds
[ 9457.600666] PM: Finishing wakeup.
[ 9457.600681] Restarting tasks ... done.
[ 9458.530512] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input14
[ 9458.578007] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input15
[ 9459.382848] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9459.398530] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9460.766040] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[ 9460.766098] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[ 9460.766186] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[ 9460.766258] [drm] Loading R300 Microcode
[ 9460.766331] [drm] Num pipes: 1
[ 9463.971070] b44: eth0: powering down PHY
[ 9464.283490] [drm] Num pipes: 1
[ 9467.659532] PM: Syncing filesystems ... done.
[ 9467.666421] PM: Preparing system for mem sleep
[ 9467.666432] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 9467.669095] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 9467.669208] PM: Entering mem sleep
[ 9467.669240] Suspending console(s) (use no_console_suspend to debug)
[ 9467.669609] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 9468.030263] sd 0:0:0:0: [sda] Stopping disk
[ 9468.924597] eth1: Going into suspend...
[ 9468.927344] ipw2200 0000:02:03.0: PCI INT A disabled
[ 9468.927356] ACPI handle has no context!
[ 9468.949268] ACPI handle has no context!
[ 9468.949278] sdhci-pci 0000:02:01.2: PME# disabled
[ 9468.949290] sdhci-pci 0000:02:01.2: PCI INT C disabled
[ 9468.949299] ACPI handle has no context!
[ 9468.984106] b44 0000:02:00.0: PCI INT A disabled
[ 9468.984116] ACPI handle has no context!
[ 9469.000291] pci 0000:01:00.0: PCI INT A disabled
[ 9469.000498] Intel ICH 0000:00:1f.5: PCI INT B disabled
[ 9469.000708] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 9469.000728] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[ 9469.000742] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 9469.000755] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 9469.000769] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 9469.000826] PM: suspend devices took 1.332 seconds
[ 9469.001118] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9469.022394] ACPI: Preparing to enter system sleep state S3
[ 9469.022991] Disabling non-boot CPUs ...
[ 9469.023032] Back to C!
[ 9469.023032] CPU0: Thermal monitoring enabled (TM1)
[ 9469.025101] ACPI: Waking up from system sleep state S3
[ 9469.031062] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 9469.031085] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 9469.031106] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xbf41)
[ 9469.031128] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 9469.031147] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[ 9469.031168] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xbf21)
[ 9469.031190] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 9469.031243] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 9469.031271] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9469.031293] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0xfff0, writing 0x23f02000)
[ 9469.031308] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20020200, writing 0x20060200)
[ 9469.031374] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x24000000)
[ 9469.031387] ata_piix 0000:00:1f.1: restoring config space at offset 0x7 (was 0x1, writing 0x375)
[ 9469.031399] ata_piix 0000:00:1f.1: restoring config space at offset 0x6 (was 0x1, writing 0x171)
[ 9469.031411] ata_piix 0000:00:1f.1: restoring config space at offset 0x5 (was 0x1, writing 0x3f5)
[ 9469.031422] ata_piix 0000:00:1f.1: restoring config space at offset 0x4 (was 0x1, writing 0x1f1)
[ 9469.031437] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800007)
[ 9469.031473] Intel ICH 0000:00:1f.5: restoring config space at offset 0x7 (was 0x0, writing 0xf8fff400)
[ 9469.031485] Intel ICH 0000:00:1f.5: restoring config space at offset 0x6 (was 0x0, writing 0xf8fff800)
[ 9469.031561] pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0x80000000)
[ 9469.031584] pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x2b00127, writing 0x2b00123)
[ 9469.031613] b44 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 9469.031639] b44 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfaffe000)
[ 9469.031650] b44 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x2000)
[ 9469.031663] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 9469.031692] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xf (was 0x7800100, writing 0x58001ff)
[ 9469.031704] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xe (was 0x0, writing 0xe4fc)
[ 9469.031716] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xd (was 0x0, writing 0xe400)
[ 9469.031727] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xc (was 0x0, writing 0xe0fc)
[ 9469.031739] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xb (was 0x0, writing 0xe000)
[ 9469.031751] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xa (was 0x0, writing 0x2bfff000)
[ 9469.031763] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x9 (was 0x0, writing 0x28000000)
[ 9469.031775] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x8 (was 0x0, writing 0x23fff000)
[ 9469.031786] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x7 (was 0x0, writing 0x20000000)
[ 9469.031798] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0060302)
[ 9469.031812] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfa000000)
[ 9469.031824] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x3 (was 0x820000, writing 0x82a800)
[ 9469.168085] ohci1394 0000:02:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xfaffd800)
[ 9469.168098] ohci1394 0000:02:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 9469.168112] ohci1394 0000:02:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 9469.168157] sdhci-pci 0000:02:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xfaffd400)
[ 9469.168170] sdhci-pci 0000:02:01.2: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 9469.168183] sdhci-pci 0000:02:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 9469.168212] ipw2200 0000:02:03.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[ 9469.168240] ipw2200 0000:02:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfaffc000)
[ 9469.168252] ipw2200 0000:02:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[ 9469.168265] ipw2200 0000:02:03.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900116)
[ 9469.471203] pm_op(): pci_pm_resume+0x0/0x90 returns -16
[ 9469.471213] PM: Device 0000:00:00.0 failed to resume: error -16
[ 9469.471242] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 9469.471255] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 9469.471282] usb usb2: root hub lost power or was reset
[ 9469.471310] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 9469.471323] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 9469.471347] usb usb3: root hub lost power or was reset
[ 9469.471372] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 9469.471384] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 9469.471407] usb usb4: root hub lost power or was reset
[ 9469.471430] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9469.471443] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[ 9469.471455] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 9469.471466] usb usb1: root hub lost power or was reset
[ 9469.475367] ehci_hcd 0000:00:1d.7: debug port 1
[ 9469.475380] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[ 9469.475399] pci 0000:00:1e.0: setting latency timer to 64
[ 9469.475420] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 9469.475431] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 9469.475530] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[ 9469.475542] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 9470.484519] ata2.00: configured for UDMA/33
[ 9470.486246] pci 0000:00:1f.6: PME# disabled
[ 9470.486257] pci 0000:01:00.0: PME# disabled
[ 9470.486271] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 9470.486292] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 9470.562152] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 9470.571357] sdhci-pci 0000:02:01.2: PCI INT C -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[ 9470.572385] eth1: Coming out of suspend...
[ 9470.572399] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[ 9470.725078] sd 0:0:0:0: [sda] Starting disk
[ 9470.725709] ata1.00: configured for UDMA/100
[ 9470.748297] PM: resume devices took 1.580 seconds
[ 9470.748477] PM: Finishing wakeup.
[ 9470.748482] Restarting tasks ... done.
[ 9471.669393] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9471.674166] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9471.690710] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input16
[ 9471.711199] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input17
[ 9472.850982] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[ 9472.851023] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[ 9472.851086] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[ 9472.851139] [drm] Loading R300 Microcode
[ 9472.851195] [drm] Num pipes: 1
[ 9486.177263] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9496.440227] eth1: no IPv6 routers present
[10113.626868] b44: eth0: powering down PHY
[10114.160568] [drm] Num pipes: 1
[10116.790271] PM: Syncing filesystems ... done.
[10116.796864] PM: Preparing system for mem sleep
[10116.796870] Freezing user space processes ... (elapsed 0.00 seconds) done.
[10116.800252] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[10116.800310] PM: Entering mem sleep
[10116.800331] Suspending console(s) (use no_console_suspend to debug)
[10116.800546] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[10117.262805] sd 0:0:0:0: [sda] Stopping disk
[10118.160467] eth1: Going into suspend...
[10118.161461] ipw2200 0000:02:03.0: PCI INT A disabled
[10118.161467] ACPI handle has no context!
[10118.177072] ACPI handle has no context!
[10118.177077] sdhci-pci 0000:02:01.2: PME# disabled
[10118.177083] sdhci-pci 0000:02:01.2: PCI INT C disabled
[10118.177088] ACPI handle has no context!
[10118.212074] b44 0000:02:00.0: PCI INT A disabled
[10118.212079] ACPI handle has no context!
[10118.228227] pci 0000:01:00.0: PCI INT A disabled
[10118.228429] Intel ICH 0000:00:1f.5: PCI INT B disabled
[10118.228566] ata_piix 0000:00:1f.1: PCI INT A disabled
[10118.228578] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[10118.228585] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[10118.228593] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[10118.228600] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[10118.228629] PM: suspend devices took 1.428 seconds
[10118.228831] ehci_hcd 0000:00:1d.7: PME# disabled
[10118.247691] ACPI: Preparing to enter system sleep state S3
[10118.248144] Disabling non-boot CPUs ...
[10118.248170] Back to C!
[10118.248170] CPU0: Thermal monitoring enabled (TM1)
[10118.248170] ACPI: Waking up from system sleep state S3
[10118.252740] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[10118.252753] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[10118.252766] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xbf41)
[10118.252778] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[10118.252788] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[10118.252801] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xbf21)
[10118.252813] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[10118.252850] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[10118.252867] ehci_hcd 0000:00:1d.7: PME# disabled
[10118.252880] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0xfff0, writing 0x23f02000)
[10118.252888] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20020200, writing 0x20060200)
[10118.252933] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x24000000)
[10118.252940] ata_piix 0000:00:1f.1: restoring config space at offset 0x7 (was 0x1, writing 0x375)
[10118.252945] ata_piix 0000:00:1f.1: restoring config space at offset 0x6 (was 0x1, writing 0x171)
[10118.252951] ata_piix 0000:00:1f.1: restoring config space at offset 0x5 (was 0x1, writing 0x3f5)
[10118.252956] ata_piix 0000:00:1f.1: restoring config space at offset 0x4 (was 0x1, writing 0x1f1)
[10118.252964] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800007)
[10118.252986] Intel ICH 0000:00:1f.5: restoring config space at offset 0x7 (was 0x0, writing 0xf8fff400)
[10118.252992] Intel ICH 0000:00:1f.5: restoring config space at offset 0x6 (was 0x0, writing 0xf8fff800)
[10118.253042] pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0x80000000)
[10118.253055] pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x2b00127, writing 0x2b00123)
[10118.253072] b44 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[10118.253088] b44 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfaffe000)
[10118.253093] b44 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x2000)
[10118.253099] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[10118.253116] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xf (was 0x7800100, writing 0x58001ff)
[10118.253122] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xe (was 0x0, writing 0xe4fc)
[10118.253127] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xd (was 0x0, writing 0xe400)
[10118.253133] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xc (was 0x0, writing 0xe0fc)
[10118.253138] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xb (was 0x0, writing 0xe000)
[10118.253143] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xa (was 0x0, writing 0x2bfff000)
[10118.253149] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x9 (was 0x0, writing 0x28000000)
[10118.253154] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x8 (was 0x0, writing 0x23fff000)
[10118.253160] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x7 (was 0x0, writing 0x20000000)
[10118.253165] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0060302)
[10118.253172] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfa000000)
[10118.253177] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x3 (was 0x820000, writing 0x82a800)
[10118.392060] ohci1394 0000:02:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xfaffd800)
[10118.392066] ohci1394 0000:02:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[10118.392072] ohci1394 0000:02:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[10118.392101] sdhci-pci 0000:02:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xfaffd400)
[10118.392106] sdhci-pci 0000:02:01.2: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[10118.392113] sdhci-pci 0000:02:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[10118.392130] ipw2200 0000:02:03.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[10118.392147] ipw2200 0000:02:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfaffc000)
[10118.392152] ipw2200 0000:02:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[10118.392159] ipw2200 0000:02:03.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900116)
[10118.670114] pm_op(): pci_pm_resume+0x0/0x90 returns -16
[10118.670117] PM: Device 0000:00:00.0 failed to resume: error -16
[10118.670132] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[10118.670139] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[10118.670160] usb usb2: root hub lost power or was reset
[10118.670178] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[10118.670184] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[10118.670202] usb usb3: root hub lost power or was reset
[10118.670218] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[10118.670224] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[10118.670242] usb usb4: root hub lost power or was reset
[10118.670258] ehci_hcd 0000:00:1d.7: PME# disabled
[10118.670263] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[10118.670270] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[10118.670275] usb usb1: root hub lost power or was reset
[10118.674175] ehci_hcd 0000:00:1d.7: debug port 1
[10118.674183] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[10118.674194] pci 0000:00:1e.0: setting latency timer to 64
[10118.674205] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[10118.674210] ata_piix 0000:00:1f.1: setting latency timer to 64
[10118.674271] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[10118.674277] Intel ICH 0000:00:1f.5: setting latency timer to 64
[10119.685850] pci 0000:00:1f.6: PME# disabled
[10119.685855] pci 0000:01:00.0: PME# disabled
[10119.685861] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[10119.685872] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[10119.724415] ata2.00: configured for UDMA/33
[10119.762221] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[10119.771296] sdhci-pci 0000:02:01.2: PCI INT C -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[10119.772307] eth1: Coming out of suspend...
[10119.772314] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[10119.925208] sd 0:0:0:0: [sda] Starting disk
[10119.925589] ata1.00: configured for UDMA/100
[10119.952233] PM: resume devices took 1.560 seconds
[10119.952348] PM: Finishing wakeup.
[10119.952350] Restarting tasks ... done.
[10120.855017] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input18
[10120.889744] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input19
[10121.738742] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10121.741613] ADDRCONF(NETDEV_UP): eth1: link is not ready
[10122.445316] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[10122.506239] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[10122.506280] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[10122.506342] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[10122.506397] [drm] Loading R300 Microcode
[10122.506452] [drm] Num pipes: 1
[10132.684031] eth1: no IPv6 routers present
[11873.358626] b44: eth0: powering down PHY
[11877.271123] [drm] Num pipes: 1
[11883.001859] PM: Syncing filesystems ... done.
[11883.004466] PM: Preparing system for mem sleep
[11883.004473] Freezing user space processes ... (elapsed 0.00 seconds) done.
[11883.006361] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[11883.006422] PM: Entering mem sleep
[11883.006443] Suspending console(s) (use no_console_suspend to debug)
[11883.006657] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[11883.325418] sd 0:0:0:0: [sda] Stopping disk
[11884.228464] eth1: Going into suspend...
[11884.229378] ipw2200 0000:02:03.0: PCI INT A disabled
[11884.229385] ACPI handle has no context!
[11884.245259] ACPI handle has no context!
[11884.245265] sdhci-pci 0000:02:01.2: PME# disabled
[11884.245270] sdhci-pci 0000:02:01.2: PCI INT C disabled
[11884.245275] ACPI handle has no context!
[11884.280074] b44 0000:02:00.0: PCI INT A disabled
[11884.280080] ACPI handle has no context!
[11884.296224] pci 0000:01:00.0: PCI INT A disabled
[11884.296409] Intel ICH 0000:00:1f.5: PCI INT B disabled
[11884.296545] ata_piix 0000:00:1f.1: PCI INT A disabled
[11884.296556] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[11884.296564] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[11884.296572] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[11884.296578] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[11884.296608] PM: suspend devices took 1.292 seconds
[11884.296810] ehci_hcd 0000:00:1d.7: PME# disabled
[11884.315637] ACPI: Preparing to enter system sleep state S3
[11884.316075] Disabling non-boot CPUs ...
[11884.316101] Back to C!
[11884.316101] CPU0: Thermal monitoring enabled (TM1)
[11884.316101] ACPI: Waking up from system sleep state S3
[11884.320770] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[11884.320784] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[11884.320796] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xbf41)
[11884.320808] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[11884.320819] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[11884.320831] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xbf21)
[11884.320844] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[11884.320881] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[11884.320898] ehci_hcd 0000:00:1d.7: PME# disabled
[11884.320910] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0xfff0, writing 0x23f02000)
[11884.320918] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20020200, writing 0x20060200)
[11884.320962] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x24000000)
[11884.320969] ata_piix 0000:00:1f.1: restoring config space at offset 0x7 (was 0x1, writing 0x375)
[11884.320974] ata_piix 0000:00:1f.1: restoring config space at offset 0x6 (was 0x1, writing 0x171)
[11884.320980] ata_piix 0000:00:1f.1: restoring config space at offset 0x5 (was 0x1, writing 0x3f5)
[11884.320985] ata_piix 0000:00:1f.1: restoring config space at offset 0x4 (was 0x1, writing 0x1f1)
[11884.320993] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800007)
[11884.321016] Intel ICH 0000:00:1f.5: restoring config space at offset 0x7 (was 0x0, writing 0xf8fff400)
[11884.321022] Intel ICH 0000:00:1f.5: restoring config space at offset 0x6 (was 0x0, writing 0xf8fff800)
[11884.321072] pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0x80000000)
[11884.321085] pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x2b00127, writing 0x2b00123)
[11884.321103] b44 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[11884.321118] b44 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfaffe000)
[11884.321124] b44 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x2000)
[11884.321130] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[11884.321147] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xf (was 0x7800100, writing 0x58001ff)
[11884.321152] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xe (was 0x0, writing 0xe4fc)
[11884.321158] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xd (was 0x0, writing 0xe400)
[11884.321163] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xc (was 0x0, writing 0xe0fc)
[11884.321169] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xb (was 0x0, writing 0xe000)
[11884.321174] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xa (was 0x0, writing 0x2bfff000)
[11884.321180] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x9 (was 0x0, writing 0x28000000)
[11884.321185] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x8 (was 0x0, writing 0x23fff000)
[11884.321191] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x7 (was 0x0, writing 0x20000000)
[11884.321196] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0060302)
[11884.321203] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfa000000)
[11884.321208] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x3 (was 0x820000, writing 0x82a800)
[11884.460060] ohci1394 0000:02:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xfaffd800)
[11884.460066] ohci1394 0000:02:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[11884.460073] ohci1394 0000:02:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[11884.460101] sdhci-pci 0000:02:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xfaffd400)
[11884.460107] sdhci-pci 0000:02:01.2: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[11884.460113] sdhci-pci 0000:02:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[11884.460131] ipw2200 0000:02:03.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
[11884.460147] ipw2200 0000:02:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfaffc000)
[11884.460153] ipw2200 0000:02:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[11884.460159] ipw2200 0000:02:03.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900116)
[11884.742122] pm_op(): pci_pm_resume+0x0/0x90 returns -16
[11884.742125] PM: Device 0000:00:00.0 failed to resume: error -16
[11884.742141] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[11884.742147] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[11884.742168] usb usb2: root hub lost power or was reset
[11884.742186] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[11884.742192] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[11884.742210] usb usb3: root hub lost power or was reset
[11884.742226] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[11884.742232] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[11884.742250] usb usb4: root hub lost power or was reset
[11884.742265] ehci_hcd 0000:00:1d.7: PME# disabled
[11884.742271] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[11884.742278] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[11884.742283] usb usb1: root hub lost power or was reset
[11884.746178] ehci_hcd 0000:00:1d.7: debug port 1
[11884.746185] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[11884.766556] pci 0000:00:1e.0: setting latency timer to 64
[11884.766568] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[11884.766573] ata_piix 0000:00:1f.1: setting latency timer to 64
[11884.766593] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[11884.766599] Intel ICH 0000:00:1f.5: setting latency timer to 64
[11885.777859] pci 0000:00:1f.6: PME# disabled
[11885.777865] pci 0000:01:00.0: PME# disabled
[11885.777871] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[11885.777881] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[11885.816416] ata2.00: configured for UDMA/33
[11885.854218] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[11885.863295] sdhci-pci 0000:02:01.2: PCI INT C -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[11885.864307] eth1: Coming out of suspend...
[11885.864313] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[11886.000076] ata1.00: configured for UDMA/100
[11886.016877] sd 0:0:0:0: [sda] Starting disk
[11886.044328] PM: resume devices took 1.584 seconds
[11886.044441] PM: Finishing wakeup.
[11886.044443] Restarting tasks ... done.
[11886.934950] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input20
[11886.958202] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input21
[11887.281036] ADDRCONF(NETDEV_UP): eth0: link is not ready
[11887.282586] ADDRCONF(NETDEV_UP): eth1: link is not ready
[11888.153833] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[11888.690473] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[11888.690514] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[11888.690575] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[11888.690633] [drm] Loading R300 Microcode
[11888.690689] [drm] Num pipes: 1
[11898.312235] eth1: no IPv6 routers present
[11901.820554] b44: eth0: powering down PHY
[11904.477190] [drm] Num pipes: 1
[11906.203859] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[11906.203866] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[11906.203871] PM: Basic memory bitmaps created
[11906.203873] PM: Syncing filesystems ... done.
[11906.205964] Freezing user space processes ... (elapsed 0.01 seconds) done.
[11906.219144] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[11906.219221] PM: Shrinking memory... done (68325 pages freed)
[11915.850646] PM: Freed 273300 kbytes in 9.63 seconds (28.38 MB/s)
[11915.850650] Suspending console(s) (use no_console_suspend to debug)
[11916.052116] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[11916.270117] eth1: Going into suspend...
[11916.272109] ipw2200 0000:02:03.0: PCI INT A disabled
[11916.272116] ACPI handle has no context!
[11916.289249] ACPI handle has no context!
[11916.289254] sdhci-pci 0000:02:01.2: PME# disabled
[11916.289259] sdhci-pci 0000:02:01.2: PCI INT C disabled
[11916.289264] ACPI handle has no context!
[11916.324253] b44 0000:02:00.0: PCI INT A disabled
[11916.324259] ACPI handle has no context!
[11916.340219] pci 0000:01:00.0: PCI INT A disabled
[11916.340422] Intel ICH 0000:00:1f.5: PCI INT B disabled
[11916.340556] ata_piix 0000:00:1f.1: PCI INT A disabled
[11916.342660] ACPI: Preparing to enter system sleep state S4
[11916.342964] PM: Saving platform NVS memory
[11916.343090] Disabling non-boot CPUs ...
[11916.343165] PM: Creating hibernation image: 
[11916.344203] PM: Need to copy 54665 pages
[11916.344203] PM: Normal pages needed: 54665 + 1024 + 14, available pages: 76223
[11916.344203] PM: Restoring platform NVS memory
[11916.344203] CPU0: Thermal monitoring enabled (TM1)
[11916.344203] ACPI: Waking up from system sleep state S4
[11916.347200] ehci_hcd 0000:00:1d.7: PME# disabled
[11916.347217] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20020200, writing 0x20060200)
[11916.347270] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800003, writing 0x2800007)
[11916.347298] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[11916.347379] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[11916.347396] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xf (was 0x74001ff, writing 0x58001ff)
[11916.347413] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x3 (was 0x822000, writing 0x82a800)
[11916.757785] pm_op(): pci_pm_restore+0x0/0x90 returns -16
[11916.757788] PM: Device 0000:00:00.0 failed to restore: error -16
[11916.757799] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[11916.757828] usb usb2: root hub lost power or was reset
[11916.757845] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[11916.757872] usb usb3: root hub lost power or was reset
[11916.757887] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[11916.757915] usb usb4: root hub lost power or was reset
[11916.757930] ehci_hcd 0000:00:1d.7: PME# disabled
[11916.757935] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[11916.757940] usb usb1: root hub lost power or was reset
[11916.761837] ehci_hcd 0000:00:1d.7: debug port 1
[11916.761844] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[11916.761859] pci 0000:00:1e.0: setting latency timer to 64
[11916.761871] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[11916.761876] ata_piix 0000:00:1f.1: setting latency timer to 64
[11916.761894] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[11916.761901] Intel ICH 0000:00:1f.5: setting latency timer to 64
[11916.940551] ata2.00: configured for UDMA/33
[11916.940848] ata1.00: configured for UDMA/100
[11917.773847] pci 0000:00:1f.6: PME# disabled
[11917.773852] pci 0000:01:00.0: PME# disabled
[11917.773859] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[11917.773869] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[11917.850219] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[11917.859297] sdhci-pci 0000:02:01.2: PCI INT C -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[11917.860303] eth1: Coming out of suspend...
[11917.860309] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[11918.013205] sd 0:0:0:0: [sda] Starting disk
[11918.092249] PM: Image restored successfully.
[11918.112358] Restarting tasks ... done.
[11918.115615] PM: Basic memory bitmaps freed
[11939.539991] ADDRCONF(NETDEV_UP): eth0: link is not ready
[11939.648355] ADDRCONF(NETDEV_UP): eth1: link is not ready
[11941.831846] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[11941.831884] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[11941.831945] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[11941.832001] [drm] Loading R300 Microcode
[11941.832090] [drm] Num pipes: 1
[11948.011282] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[11958.668048] eth1: no IPv6 routers present


---

