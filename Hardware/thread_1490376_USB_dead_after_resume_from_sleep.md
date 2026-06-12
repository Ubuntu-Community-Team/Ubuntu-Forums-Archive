---
title: "USB dead after resume from sleep"
date: 2010-05-22
forum: Hardware
---

### Post by fa2k on 2010-05-22
Hi, I recently purchased a thinkpad T410i, and installed 10.4, 64 bit version, on it. When I put it in sleep mode, then resume, the USB ports do not work. The ports do not seem to provide any power at all (at that point). 

I have the newest BIOS. Hibernate works well. There is no other "weirdness" when resuming from sleep. The problem happens with any USB device connected, and even with no devices at all connected when sleeping/resuming.

I included the output of ```
dmesg
```, please tell me if any other info would be useful:

```
[   40.001800]   domain 1: span 0-3 level MC
[   40.001801]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[   40.086335] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input12
[   45.924553] eth0: no IPv6 routers present
[   47.188429] vmnet1: no IPv6 routers present
[   47.409333] vmnet8: no IPv6 routers present
[  567.076954] CPU0 attaching NULL sched-domain.
[  567.076964] CPU1 attaching NULL sched-domain.
[  567.076968] CPU2 attaching NULL sched-domain.
[  567.076972] CPU3 attaching NULL sched-domain.
[  567.187946] CPU0 attaching sched-domain:
[  567.187951]  domain 0: span 0-1 level SIBLING
[  567.187955]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[  567.187961]   domain 1: span 0-3 level MC
[  567.187964]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178)
[  567.187972] CPU1 attaching sched-domain:
[  567.187975]  domain 0: span 0-1 level SIBLING
[  567.187977]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[  567.187983]   domain 1: span 0-3 level MC
[  567.187986]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178)
[  567.187993] CPU2 attaching sched-domain:
[  567.187995]  domain 0: span 2-3 level SIBLING
[  567.187998]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589)
[  567.188004]   domain 1: span 0-3 level MC
[  567.188006]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[  567.188013] CPU3 attaching sched-domain:
[  567.188015]  domain 0: span 2-3 level SIBLING
[  567.188018]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589)
[  567.188024]   domain 1: span 0-3 level MC
[  567.188026]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[  568.733520] bridge-eth0: disabling the bridge on dev down
[  568.773734] bridge-eth0: down
[  568.773818] bridge-eth0: detached
[  571.839566] PM: Syncing filesystems ... done.
[  572.298515] PM: Preparing system for mem sleep
[  572.298521] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  572.299268] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  572.299316] PM: Entering mem sleep
[  572.299332] Suspending console(s) (use no_console_suspend to debug)
[  572.540471] PM: suspend of drv:psmouse dev:serio2 complete after 241.312 msecs
[  572.696550] PM: suspend of drv:ieee80211 dev:phy0 complete after 156.348 msecs
[  572.816349] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  572.816564] sd 0:0:0:0: [sda] Stopping disk
[  573.246207] PM: suspend of drv:sd dev:0:0:0:0 complete after 430.647 msecs
[  573.674206] PM: suspend of drv:psmouse dev:serio1 complete after 389.400 msecs
[  574.273648] PM: suspend of drv:atkbd dev:serio0 complete after 600.532 msecs
[  574.279428] ACPI handle has no context!
[  574.294745] ACPI handle has no context!
[  574.294755] sdhci-pci 0000:0d:00.0: PCI INT A disabled
[  574.294766] ACPI handle has no context!
[  574.852635] HDA Intel 0000:01:00.1: PCI INT A disabled
[  574.852717] ACPI handle has no context!
[  574.872570] PM: suspend of drv:HDA Intel dev:0000:01:00.1 complete after 539.967 msecs
[  575.042273] ehci_hcd 0000:00:1d.0: PCI INT D disabled
[  575.261967] HDA Intel 0000:00:1b.0: PCI INT B disabled
[  575.281818] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 239.966 msecs
[  575.281831] ehci_hcd 0000:00:1a.0: PCI INT D disabled
[  575.446864] e1000e 0000:00:19.0: PCI INT A disabled
[  575.446871] e1000e 0000:00:19.0: PME# enabled
[  575.446880] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
[  575.461511] PM: suspend of drv:e1000e dev:0000:00:19.0 complete after 180.002 msecs
[  575.461594] PM: suspend of devices complete after 3167.791 msecs
[  575.461598] PM: suspend devices took 3.170 seconds
[  575.551288] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D3
[  575.631150] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D3
[  575.631236] PM: late suspend of devices complete after 169.946 msecs
[  575.730982] ACPI: Preparing to enter system sleep state S3
[  576.170118] Disabling non-boot CPUs ...
[  576.170146] CPU0 attaching NULL sched-domain.
[  576.170150] CPU1 attaching NULL sched-domain.
[  576.170152] CPU2 attaching NULL sched-domain.
[  576.170154] CPU3 attaching NULL sched-domain.
[  576.329831] CPU0 attaching NULL sched-domain.
[  576.331047] Broke affinity for irq 25
[  576.332260] CPU 1 is now offline
[  576.334042] Broke affinity for irq 26
[  576.335273] CPU 2 is now offline
[  576.336978] Broke affinity for irq 9
[  576.336998] Broke affinity for irq 16
[  576.337009] Broke affinity for irq 19
[  576.337025] Broke affinity for irq 27
[  576.439624] CPU 3 is now offline
[  576.439627] SMP alternatives: switching to UP code
[  576.444340] Extended CMOS year: 2000
[18446744064.899187] Back to C!
[18446744064.899445] CPU0: Thermal monitoring enabled (TM1)
[18446744064.899505] Extended CMOS year: 2000
[18446744064.899533] Enabling non-boot CPUs ...
[18446744064.899720] SMP alternatives: switching to SMP code
[18446744064.903850] Booting processor 1 APIC 0x1 ip 0x6000
[18446744064.914089] Initializing CPU#1
[18446744065.064483] CPU: Physical Processor ID: 0
[18446744065.064484] CPU: Processor Core ID: 0
[18446744065.064487] CPU: L1 I cache: 32K, L1 D cache: 32K
[18446744065.064489] CPU: L2 cache: 256K
[18446744065.064491] CPU: L3 cache: 3072K
[18446744065.064494] CPU 1/0x1 -> Node 0
[18446744065.064507] CPU1: Thermal monitoring enabled (TM1)
[18446744065.064511] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6
[18446744065.064556] CPU1: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[18446744065.064563] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[18446744065.084604] CPU0 attaching NULL sched-domain.
[18446744065.154325] CPU0 attaching sched-domain:
[18446744065.154328]  domain 0: span 0-1 level SIBLING
[18446744065.154330]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[18446744065.154335]   domain 1: span 0-1 level MC
[18446744065.154337]    groups: 0-1 (cpu_power = 1178)
[18446744065.154341] CPU1 attaching sched-domain:
[18446744065.154342]  domain 0: span 0-1 level SIBLING
[18446744065.154344]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[18446744065.154348]   domain 1: span 0-1 level MC
[18446744065.154350]    groups: 0-1 (cpu_power = 1178)
[18446744065.155084] hpet: hpet3 irq 25 for MSI
[18446744065.155089] CPU1 is up
[18446744065.155306] Booting processor 2 APIC 0x4 ip 0x6000
[18446744065.165535] Initializing CPU#2
[18446744065.314025] CPU: Physical Processor ID: 0
[18446744065.314026] CPU: Processor Core ID: 2
[18446744065.314029] CPU: L1 I cache: 32K, L1 D cache: 32K
[18446744065.314031] CPU: L2 cache: 256K
[18446744065.314031] CPU: L3 cache: 3072K
[18446744065.314034] CPU 2/0x4 -> Node 0
[18446744065.314047] CPU2: Thermal monitoring enabled (TM1)
[18446744065.314050] CPU 2 MCA banks SHD:6
[18446744065.314116] CPU2: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[18446744065.314123] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[18446744065.334170] CPU0 attaching NULL sched-domain.
[18446744065.334174] CPU1 attaching NULL sched-domain.
[18446744065.383896] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445469547763131453 new 18445469547758135204 attempts 1
[18446744065.463760] CPU0 attaching sched-domain:
[18446744065.463763]  domain 0: span 0-1 level SIBLING
[18446744065.463765]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[18446744065.463770]   domain 1: span 0-2 level MC
[18446744065.463772]    groups: 0-1 (cpu_power = 1178) 2
[18446744065.463776] CPU1 attaching sched-domain:
[18446744065.463777]  domain 0: span 0-1 level SIBLING
[18446744065.463779]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[18446744065.463783]   domain 1: span 0-2 level MC
[18446744065.463785]    groups: 0-1 (cpu_power = 1178) 2
[18446744065.463789] CPU2 attaching sched-domain:
[18446744065.463790]  domain 0: span 0-2 level MC
[18446744065.463792]   groups: 2 0-1 (cpu_power = 1178)
[18446744065.464526] hpet: hpet4 irq 26 for MSI
[18446744065.464533] CPU2 is up
[18446744065.464776] Booting processor 3 APIC 0x5 ip 0x6000
[18446744065.475005] Initializing CPU#3
[18446744065.623461] CPU: Physical Processor ID: 0
[18446744065.623462] CPU: Processor Core ID: 2
[18446744065.623466] CPU: L1 I cache: 32K, L1 D cache: 32K
[18446744065.623468] CPU: L2 cache: 256K
[18446744065.623470] CPU: L3 cache: 3072K
[18446744065.623473] CPU 3/0x5 -> Node 0
[18446744065.623487] CPU3: Thermal monitoring enabled (TM1)
[18446744065.623491] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6
[18446744065.623581] CPU3: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[18446744065.623588] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[18446744065.643644] CPU0 attaching NULL sched-domain.
[18446744065.643647] CPU1 attaching NULL sched-domain.
[18446744065.643649] CPU2 attaching NULL sched-domain.
[18446744065.763214] CPU0 attaching sched-domain:
[18446744065.763218]  domain 0: span 0-1 level SIBLING
[18446744065.763220]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[18446744065.763225]   domain 1: span 0-3 level MC
[18446744065.763227]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178)
[18446744065.763232] CPU1 attaching sched-domain:
[18446744065.763234]  domain 0: span 0-1 level SIBLING
[18446744065.763237]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[18446744065.763241]   domain 1: span 0-3 level MC
[18446744065.763243]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178)
[18446744065.763248] CPU2 attaching sched-domain:
[18446744065.763250]  domain 0: span 2-3 level SIBLING
[18446744065.763252]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589)
[18446744065.763256]   domain 1: span 0-3 level MC
[18446744065.763258]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[18446744065.763263] CPU3 attaching sched-domain:
[18446744065.763265]  domain 0: span 2-3 level SIBLING
[18446744065.763268]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589)
[18446744065.763272]   domain 1: span 0-3 level MC
[18446744065.763274]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[18446744065.764268] hpet: hpet5 irq 27 for MSI
[18446744065.764276] CPU3 is up
[18446744065.765784] ACPI: Waking up from system sleep state S3
[18446744066.512022] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[18446744066.512140] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x400, writing 0x40b)
[18446744066.512159] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xf2428000)
[18446744066.512168] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[18446744066.512273] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[18446744066.512336] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
[18446744066.512348] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[18446744066.512419] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[18446744066.512470] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x4010b)
[18446744066.512482] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[18446744066.512488] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xf210f210)
[18446744066.512494] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
[18446744066.512504] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[18446744066.512511] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[18446744066.512558] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x400, writing 0x40b)
[18446744066.512577] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xf2428400)
[18446744066.512586] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[18446744066.512711] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[18446744066.512781] pci 0000:00:1f.6: restoring config space at offset 0xf (was 0x400, writing 0x40b)
[18446744066.512805] pci 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[18446744066.512854] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x800010, writing 0x800000)
[18446744066.512860] nvidia 0000:01:00.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100007)
[18446744066.512924] HDA Intel 0000:01:00.1: restoring config space at offset 0x1 (was 0x100106, writing 0x100102)
[18446744066.513347] PM: early resume of devices complete after 1.419 msecs
[18446744066.549308] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[18446744066.549315] e1000e 0000:00:19.0: setting latency timer to 64
[18446744066.549323] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
[18446744066.549328] e1000e 0000:00:19.0: PME# disabled
[18446744066.549371] e1000e 0000:00:19.0: irq 34 for MSI/MSI-X
[18446744066.818428] PM: resume of drv:e1000e dev:0000:00:19.0 complete after 269.632 msecs
[18446744066.818435] ehci_hcd 0000:00:1a.0: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[18446744066.818442] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[18446744066.818507] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[18446744066.818514] HDA Intel 0000:00:1b.0: setting latency timer to 64
[18446744066.818545] ehci_hcd 0000:00:1d.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[18446744066.818552] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[18446744066.818618] pci 0000:00:1e.0: setting latency timer to 64
[18446744066.818630] ahci 0000:00:1f.2: setting latency timer to 64
[18446744067.259344] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 441.388 msecs
[18446744067.260290] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[18446744067.260302] HDA Intel 0000:01:00.1: setting latency timer to 64
[18446744067.260404] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
[18446744067.260411] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[18446744067.260413] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[18446744067.260472] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[18446744067.327564] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f2100800-f2100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[18446744067.530057] PM: resume of drv:usb dev:1-1 complete after 109.240 msecs
[18446744067.550014] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[18446744067.550043] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[18446744067.553079] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[18446744067.553911] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[18446744067.559771] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[18446744067.560501] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[18446744067.563111] ata2.00: configured for UDMA/100
[18446744067.564924] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[18446744067.564930] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[18446744067.565225] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[18446744067.565230] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[18446744067.568388] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[18446744067.568393] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[18446744067.568642] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[18446744067.568646] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[18446744067.570062] ata1.00: configured for UDMA/100
[18446744067.579965] ata5: SATA link down (SStatus 0 SControl 300)
[18446744067.593210] ata1.00: configured for UDMA/100
[18446744067.593215] ata1: EH complete
[18446744067.599914] ata6: SATA link down (SStatus 0 SControl 300)
[18446744067.639852] PM: resume of drv:usb dev:2-1 complete after 109.987 msecs
[18446744067.639860] sd 0:0:0:0: [sda] Starting disk
[18446744067.739881] usb 1-1.3: reset full speed USB device using ehci_hcd and address 3
[18446744067.850407] PM: resume of drv:usb dev:1-1.3 complete after 186.678 msecs
[18446744067.929509] usb 1-1.6: reset high speed USB device using ehci_hcd and address 4
[18446744068.044273] PM: resume of drv:usb dev:1-1.6 complete after 194.211 msecs
[18446744068.047857] PM: resume of devices complete after 1537.284 msecs
[18446744068.048026] PM: resume devices took 1.530 seconds
[18446744068.048054] PM: Finishing wakeup.
[18446744068.048055] Restarting tasks ... 
[18446744068.060637] usb 2-1.2: USB disconnect, address 3
[18446744068.060640] usb 2-1.2.1: USB disconnect, address 6
[18446744068.061293] usb 2-1.2.2: USB disconnect, address 4
[18446744068.078988] done.
[18446744068.318926] usb 2-1.2.6: USB disconnect, address 5
[18446744068.937630] e1000e 0000:00:19.0: irq 34 for MSI/MSI-X
[18446744068.990063] e1000e 0000:00:19.0: irq 34 for MSI/MSI-X
[18446744068.990469] ADDRCONF(NETDEV_UP): eth0: link is not ready
[18446744069.594196] CPU0 attaching NULL sched-domain.
[18446744069.594203] CPU1 attaching NULL sched-domain.
[18446744069.594208] CPU2 attaching NULL sched-domain.
[18446744069.594211] CPU3 attaching NULL sched-domain.
[18446744069.677437] CPU0 attaching sched-domain:
[18446744069.677442]  domain 0: span 0-1 level SIBLING
[18446744069.677445]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[18446744069.677452]   domain 1: span 0-3 level MC
[18446744069.677455]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178)
[18446744069.677463] CPU1 attaching sched-domain:
[18446744069.677466]  domain 0: span 0-1 level SIBLING
[18446744069.677469]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[18446744069.677475]   domain 1: span 0-3 level MC
[18446744069.677478]    groups: 0-1 (cpu_power = 1178) 2-3 (cpu_power = 1178)
[18446744069.677485] CPU2 attaching sched-domain:
[18446744069.677487]  domain 0: span 2-3 level SIBLING
[18446744069.677490]   groups: 2 (cpu_power = 589) 3 (cpu_power = 589)
[18446744069.677496]   domain 1: span 0-3 level MC
[18446744069.677498]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[18446744069.677505] CPU3 attaching sched-domain:
[18446744069.677508]  domain 0: span 2-3 level SIBLING
[18446744069.677511]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589)
[18446744069.677516]   domain 1: span 0-3 level MC
[18446744069.677519]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[18446744070.569438] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[18446744070.569443] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[18446744070.571573] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[18446744070.571788] /dev/vmnet: open called by PID 1464 (vmnet-bridge)
[18446744070.571803] /dev/vmnet: hub 0 does not exist, allocating memory.
[18446744070.571821] /dev/vmnet: port on hub 0 successfully opened
[18446744070.571834] bridge-eth0: up
[18446744070.571837] bridge-eth0: attached
[    7.687600] eth0: no IPv6 routers present

```
Any ideas?

---

### Post by fa2k on 2010-05-22
This is bug #566149 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149)), sorry for not spotting that

---

