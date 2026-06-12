---
title: "[TSC] Marking TSC unstable due to: check_tsc_sync_source failed"
date: 2008-08-09
forum: Hardware
---

### Post by kakyoism on 2008-08-09
Get this in my dmesg...
Any ideas how to fix it? Thanks!

Below is my dmesg after a suspend-resume cycle:
```
[  296.388446] sky2 eth0: disabling interface
[  296.392835] bridge-eth0: disabling the bridge
[  296.399436] bridge-eth0: down
[  296.649049] sky2 eth0: enabling interface
[  296.653944] bridge-eth0: enabling the bridge
[  296.654158] bridge-eth0: up
[  296.675249] sky2 eth0: disabling interface
[  296.679768] bridge-eth0: disabling the bridge
[  296.687249] bridge-eth0: down
[  296.705316] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[  298.865980] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[  300.210338] Syncing filesystems ... done.
[  300.210475] PM: Preparing system for mem sleep
[  300.210477] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  300.211786] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
[  300.309569] PM: Entering mem sleep
[  300.309571] Suspending console(s)
[  300.310036] ACPI: PCI interrupt for device 0000:00:02.0 disabled
[  300.353377] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 663)
[  300.395468] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 665)
[  300.398612] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[  300.558696] sd 2:0:0:0: [sda] Stopping disk
[  301.121483] ACPI handle has no context!
[  301.121546] ACPI handle has no context!
[  301.121564] ACPI: PCI interrupt for device 0000:08:03.2 disabled
[  301.121571] ACPI handle has no context!
[  301.123902] ACPI handle has no context!
[  301.138064] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[  301.138214] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[  301.142669] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[  301.142707] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[  301.142745] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[  301.146289] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[  301.147671] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[  301.148893] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
[  301.148931] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
[  301.154874] Disabling non-boot CPUs ...
[  301.154895] CPU0 attaching NULL sched-domain.
[  301.154897] CPU1 attaching NULL sched-domain.
[  301.257618] CPU 1 is now offline
[  301.257621] SMP alternatives: switching to UP code
[  301.258982] CPU0 attaching sched-domain:
[  301.258985]  domain 0: span 01
[  301.258986]   groups: 01
[  301.259175] CPU1 is down
[    0.253555] Back to C!
[    0.254102] Enabling non-boot CPUs ...
[    0.254309] CPU0 attaching NULL sched-domain.
[    0.254383] SMP alternatives: switching to SMP code
[    0.255211] Booting processor 1/1 eip 3000
[    0.265492] Initializing CPU#1
[    0.326056] Calibrating delay using timer specific routine.. 3658.05 BogoMIPS (lpj=1829027)
[    0.326063] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[    0.326068] monitor/mwait feature present.
[    0.326071] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.326073] CPU: L2 cache: 2048K
[    0.326075] CPU: Physical Processor ID: 0
[    0.326076] CPU: Processor Core ID: 1
[    0.326077] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[    0.326585] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.326605] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.346577] Measured 22103272631 cycles TSC warp between CPUs, turning off TSC clock.
[    0.346579] Marking TSC unstable due to: check_tsc_sync_source failed.
[    0.346633] CPU0 attaching sched-domain:
[    0.346636]  domain 0: span 03
[    0.346637]   groups: 01 02
[    0.346641] CPU1 attaching sched-domain:
[    0.346642]  domain 0: span 03
[    0.346643]   groups: 02 01
[    0.347025] CPU1 is up
[    0.849504] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[    0.849506] ACPI: EC: read timeout, command = 128
[    0.849509] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
[    0.849514] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
[    0.849519] ACPI Error (psparse-0537): Method parse/execution failed [\_WAK] (Node f7c84734), AE_TIME
[    0.849556] ACPI Exception (hwsleep-0586): AE_TIME, During Method _WAK [20070126]
[    0.865015] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
[    0.877996] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[    0.878004] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    0.878062] usb usb2: root hub lost power or was reset
[    0.878083] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[    0.878089] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    0.878144] usb usb3: root hub lost power or was reset
[    0.879397] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    0.879403] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    0.880758] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[    0.880765] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
[    0.880790] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[    0.880798] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    0.880826] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 40100, writing 4010a)
[    0.880843] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 20002020, writing 2020)
[    0.880853] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
[    0.880860] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100007, writing 100407)
[    0.880904] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.880917] PM: Writing back config space on device 0000:00:1c.1 at offset f (was 40200, writing 40205)
[    0.880931] PM: Writing back config space on device 0000:00:1c.1 at offset 9 (was 10001, writing f3f1f201)
[    0.880936] PM: Writing back config space on device 0000:00:1c.1 at offset 8 (was 0, writing f9f0f800)
[    0.880942] PM: Writing back config space on device 0000:00:1c.1 at offset 7 (was 0, writing 3030)
[    0.880952] PM: Writing back config space on device 0000:00:1c.1 at offset 3 (was 810000, writing 810010)
[    0.880959] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100000, writing 100507)
[    0.881003] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.881015] PM: Writing back config space on device 0000:00:1c.2 at offset f (was 40300, writing 40307)
[    0.881029] PM: Writing back config space on device 0000:00:1c.2 at offset 9 (was 10001, writing f5f1f401)
[    0.881034] PM: Writing back config space on device 0000:00:1c.2 at offset 8 (was 0, writing fbf0fa00)
[    0.881040] PM: Writing back config space on device 0000:00:1c.2 at offset 7 (was 20000000, writing 4040)
[    0.881050] PM: Writing back config space on device 0000:00:1c.2 at offset 3 (was 810000, writing 810010)
[    0.881057] PM: Writing back config space on device 0000:00:1c.2 at offset 1 (was 100000, writing 100507)
[    0.881101] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.881110] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    0.881115] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    0.881170] usb usb5: root hub lost power or was reset
[    0.881191] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[    0.881196] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    0.881251] usb usb6: root hub lost power or was reset
[    0.881304] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.881312] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    0.881377] usb usb7: root hub lost power or was reset
[    0.883807] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    0.883813] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    0.883884] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 1fff1)
[    0.883889] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was 0, writing fc20fc20)
[    0.883895] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 22800000, writing 228000f0)
[    0.883900] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 38090800, writing 380c0800)
[    0.883912] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100107)
[    0.883936] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.883995] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 100, writing 1ff)
[    0.884021] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800005, writing 2880005)
[    0.884033] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
[    0.884038] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    0.885924] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 200, writing 20a)
[    0.885951] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00007, writing 2b00407)
[    0.886000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    0.938821] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    0.938823] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[    0.962380] ata1.00: configured for UDMA/33
[    1.009751] PM: Writing back config space on device 0000:00:1f.3 at offset 4 (was 0, writing c2000000)
[    1.009803] PM: Writing back config space on device 0000:02:00.0 at offset f (was 100, writing 105)
[    1.009833] PM: Writing back config space on device 0000:02:00.0 at offset 6 (was 1, writing 2001)
[    1.009843] PM: Writing back config space on device 0000:02:00.0 at offset 4 (was 4, writing f6000004)
[    1.009850] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 10)
[    1.009861] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100000, writing 100103)
[    1.009940] PM: Writing back config space on device 0000:06:00.0 at offset f (was 100, writing 10a)
[    1.009984] PM: Writing back config space on device 0000:06:00.0 at offset 4 (was 4, writing fa000004)
[    1.009997] PM: Writing back config space on device 0000:06:00.0 at offset 3 (was 0, writing 10)
[    1.010014] PM: Writing back config space on device 0000:06:00.0 at offset 1 (was 100000, writing 40100102)
[    1.010069] PM: Writing back config space on device 0000:08:03.0 at offset f (was 34001ff, writing 5c00105)
[    1.010075] PM: Writing back config space on device 0000:08:03.0 at offset e (was 0, writing 50fc)
[    1.010081] PM: Writing back config space on device 0000:08:03.0 at offset d (was 0, writing 5000)
[    1.010087] PM: Writing back config space on device 0000:08:03.0 at offset c (was 0, writing 14fc)
[    1.010093] PM: Writing back config space on device 0000:08:03.0 at offset b (was 0, writing 1400)
[    1.010099] PM: Writing back config space on device 0000:08:03.0 at offset a (was 0, writing cbfff000)
[    1.010105] PM: Writing back config space on device 0000:08:03.0 at offset 9 (was 0, writing c8000000)
[    1.010111] PM: Writing back config space on device 0000:08:03.0 at offset 8 (was 0, writing c7fff000)
[    1.010117] PM: Writing back config space on device 0000:08:03.0 at offset 7 (was 0, writing c4000000)
[    1.010123] PM: Writing back config space on device 0000:08:03.0 at offset 6 (was 0, writing b00c0908)
[    1.010131] PM: Writing back config space on device 0000:08:03.0 at offset 4 (was 0, writing fc204000)
[    1.010137] PM: Writing back config space on device 0000:08:03.0 at offset 3 (was 820000, writing 82a820)
[    1.010145] PM: Writing back config space on device 0000:08:03.0 at offset 1 (was 2100000, writing 2100007)
[    1.012488] PM: Writing back config space on device 0000:08:03.1 at offset f (was 4030200, writing 403020a)
[    1.012513] PM: Writing back config space on device 0000:08:03.1 at offset 5 (was 0, writing fc200000)
[    1.012519] PM: Writing back config space on device 0000:08:03.1 at offset 4 (was 0, writing fc206000)
[    1.012525] PM: Writing back config space on device 0000:08:03.1 at offset 3 (was 800000, writing 802010)
[    1.012534] PM: Writing back config space on device 0000:08:03.1 at offset 1 (was 2100000, writing 2100116)
[    1.062592] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.063994] PM: Writing back config space on device 0000:08:03.2 at offset f (was 40703ff, writing 4070307)
[    1.064019] PM: Writing back config space on device 0000:08:03.2 at offset 4 (was 0, writing fc205000)
[    1.064026] PM: Writing back config space on device 0000:08:03.2 at offset 3 (was 800000, writing 803910)
[    1.064033] PM: Writing back config space on device 0000:08:03.2 at offset 1 (was 2100000, writing 2100106)
[    1.064056] ACPI: PCI Interrupt 0000:08:03.2[C] -> GSI 18 (level, low) -> IRQ 18
[    1.094713] ata4: SATA link down (SStatus 0 SControl 0)
[    1.094783] ata5: SATA link down (SStatus 0 SControl 0)
[    1.856367] sd 2:0:0:0: [sda] Starting disk
[    6.288702] ata3: port is slow to respond, please be patient (Status 0x80)
[   11.125973] ata3: softreset failed (device not ready)
[   11.787367] ata3: port is slow to respond, please be patient (Status 0x80)
[   12.346426] ata3: COMRESET failed (errno=-16)
[   12.397659] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.399007] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 succeeded
[   12.399010] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   12.401553] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 succeeded
[   12.401556] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   12.402506] ata3.00: configured for UDMA/133
[   12.403837] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   12.403850] sd 2:0:0:0: [sda] Write Protect is off
[   12.403852] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.403870] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.754382] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   12.796574] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 663)
[   12.838749] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   12.880942] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   12.882560] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   12.884075] PM: Finishing wakeup.
[   12.884077] Restarting tasks ... <6>usb 6-2: USB disconnect, address 2
[   12.884289] done.
[   13.110942] usb 6-2: new low speed USB device using uhci_hcd and address 3
[   13.123341] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   13.123346] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   13.123490] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   13.123535] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   13.123558] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   13.143317] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   13.143338] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   13.143376] sky2 0000:02:00.0: v1.20 addr 0xf6000000 irq 17 Yukon-FE (0xb7) rev 3
[   13.144606] sky2 eth0: addr 00:1a:80:b5:8a:cb
[   13.213447] sky2 eth0: enabling interface
[   13.218000] bridge-eth0: enabling the bridge
[   13.218008] bridge-eth0: up
[   13.262722] sky2 eth0: disabling interface
[   13.267143] bridge-eth0: disabling the bridge
[   13.274929] usb 6-2: configuration #1 chosen from 1 choice
[   13.276689] bridge-eth0: down
[   13.282062] sky2 eth0: enabling interface
[   13.286680] bridge-eth0: enabling the bridge
[   13.286687] bridge-eth0: up
[   13.306026] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input14
[   13.322685] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   13.352814] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input15
[   13.368652] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   13.373928] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.395623] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   14.501844] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
```

---

### Post by Saija on 2008-10-09
Hi

I'm also getting this error message, but in my case all start with an upgrade from feisty to gutsy cancelled by me because i don't see any progress at all in the upgrade application, then i shut down the pc, but nothing happens, so i press down the power button in the case until it shut down, then the next day this error appears me...

any suggestion?

Thanks.

---

