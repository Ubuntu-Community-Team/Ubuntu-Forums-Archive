---
title: "ACPI: EC: Input buffer not empty, aborting..."
date: 2009-09-03
forum: Hardware
---

### Post by xtremesupremacy3 on 2009-09-03
Hello there,

I hope you can help me.
I purchased an MSI CR700 today.
As I always do with all my previous laptops, I went and threw off Windows and install Ubuntu.
Having now gotten Ubuntu 9.04, and having to had to update my kernel due to Atheros problems, all seemed well...

Yet whenever I start the laptop I get line upon line upon line of "]```
"ACPI: EC: Input buffer not empty, aborting transaction"
```

Or something along those lines.

Now I have the following problems; When I run the laptop off the battery it detects it as being on AC, the brightness won't change when plugging out/in the AC adapter and what for me is most annoying is that when I'm surfing the web, and scroll down, the page starts to mess up.

Now please note, I'm no newbie, BUT...after having read some pages and not having a clue what theyre talking about, I ask that you please explain thoroughly what I need to do.

Thanks
Arthur

---

### Post by Plasma_Snake on 2009-09-03
Well I have the Dell Studio 1555 and do get the same error sometimes but it never messes up my computing experience like it does in ur case. Moreover I am able to fiddle with Brightness and all. Ur problem has struck me as a warning now so will look into it and report back here if get to somewhere.

---

### Post by xtremesupremacy3 on 2009-09-03
Don't get me wrong, I am able to change the brightness settings manually but usually it darkens up when you unplug the adaptor. Here it doesn't

---

### Post by xtremesupremacy3 on 2009-09-03
Just to make things a little easier for those who know more, here is the result of my dmesg:

```
[    5.160616] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *0, disabled.
[    5.161011] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    5.161406] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    5.161805] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    5.162199] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    5.162593] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    5.162989] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    5.163386] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    5.163788] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *15
[    5.164195] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    5.164591] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    5.164988] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    5.165385] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    5.165782] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    5.166178] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    5.166576] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    5.166977] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7
[    5.167381] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    5.167781] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *9
[    5.168192] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    5.168594] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *9
[    5.168993] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *15
[    5.169396] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *14
[    5.169802] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    5.170266] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    5.170661] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *0, disabled.
[    5.171057] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *0, disabled.
[    5.171454] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *0, disabled.
[    5.171851] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    5.172260] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    5.172659] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *10
[    5.173056] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *0, disabled.
[    5.173455] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *11
[    5.173852] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *0, disabled.
[    5.174291] ACPI: WMI: Mapper loaded
[    5.174344] SCSI subsystem initialized
[    5.174344] libata version 3.00 loaded.
[    5.174344] usbcore: registered new interface driver usbfs
[    5.174344] usbcore: registered new interface driver hub
[    5.174344] usbcore: registered new device driver usb
[    5.174344] PCI: Using ACPI for IRQ routing
[    5.180018] Bluetooth: Core ver 2.13
[    5.180034] NET: Registered protocol family 31
[    5.180034] Bluetooth: HCI device and connection manager initialized
[    5.180034] Bluetooth: HCI socket layer initialized
[    5.180034] NET: Registered protocol family 8
[    5.180034] NET: Registered protocol family 20
[    5.180043] NetLabel: Initializing
[    5.180045] NetLabel:  domain hash size = 128
[    5.180047] NetLabel:  protocols = UNLABELED CIPSOv4
[    5.180061] NetLabel:  unlabeled traffic allowed by default
[    5.180077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    5.180083] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    5.184077] AppArmor: AppArmor Filesystem Enabled
[    5.188018] Switched to high resolution mode on CPU 0
[    5.188484] Switched to high resolution mode on CPU 1
[    5.192010] pnp: PnP ACPI init
[    5.192021] ACPI: bus type pnp registered
[    5.692005] ACPI: EC: input buffer is not empty, aborting transaction
[    6.192005] ACPI: EC: input buffer is not empty, aborting transaction
[    6.692005] ACPI: EC: input buffer is not empty, aborting transaction
[    6.692060] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[    6.692066] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[    6.692127] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[    6.698883] pnp: PnP ACPI: found 12 devices
[    6.698886] ACPI: ACPI bus type pnp unregistered
[    6.698890] PnPBIOS: Disabled by ACPI PNP
[    6.698902] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    6.698904] system 00:04: ioport range 0x800-0x80f has been reserved
[    6.698907] system 00:04: ioport range 0x4000-0x407f has been reserved
[    6.698910] system 00:04: ioport range 0x4080-0x40ff has been reserved
[    6.698913] system 00:04: ioport range 0x4400-0x447f has been reserved
[    6.698916] system 00:04: ioport range 0x4480-0x44ff has been reserved
[    6.698918] system 00:04: ioport range 0x4800-0x487f has been reserved
[    6.698921] system 00:04: ioport range 0x4880-0x48ff has been reserved
[    6.698925] system 00:04: iomem range 0xfefe2000-0xfefe3fff has been reserved
[    6.698928] system 00:04: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    6.698931] system 00:04: iomem range 0xfee01000-0xfeefffff has been reserved
[    6.698938] system 00:07: iomem range 0xfec00000-0xfec00fff has been reserved
[    6.698941] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    6.698948] system 00:0a: iomem range 0xfc000000-0xfdffffff has been reserved
[    6.698955] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    6.698957] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    6.698960] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    6.698963] system 00:0b: iomem range 0x100000-0xbfffffff could not be reserved
[    6.698966] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    6.733698] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    6.733700] pci 0000:00:09.0:   IO window: disabled
[    6.733705] pci 0000:00:09.0:   MEM window: disabled
[    6.733709] pci 0000:00:09.0:   PREFETCH window: disabled
[    6.733715] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    6.733718] pci 0000:00:10.0:   IO window: 0xd000-0xdfff
[    6.733722] pci 0000:00:10.0:   MEM window: 0xfaf00000-0xfbffffff
[    6.733726] pci 0000:00:10.0:   PREFETCH window: 0x000000e0000000-0x000000f7ffffff
[    6.733732] pci 0000:00:15.0: PCI bridge, secondary bus 0000:03
[    6.733737] pci 0000:00:15.0:   IO window: 0xe000-0xefff
[    6.733749] pci 0000:00:15.0:   MEM window: 0xfe000000-0xfeafffff
[    6.733757] pci 0000:00:15.0:   PREFETCH window: 0x000000f8000000-0x000000f9ffffff
[    6.733771] pci 0000:00:17.0: PCI bridge, secondary bus 0000:06
[    6.733773] pci 0000:00:17.0:   IO window: disabled
[    6.733784] pci 0000:00:17.0:   MEM window: 0xfeb00000-0xfebfffff
[    6.733792] pci 0000:00:17.0:   PREFETCH window: disabled
[    6.733812] pci 0000:00:09.0: setting latency timer to 64
[    6.733819] pci 0000:00:10.0: setting latency timer to 64
[    6.734359] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 23
[    6.734366] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 23 (level, low) -> IRQ 23
[    6.734375] pci 0000:00:15.0: setting latency timer to 64
[    6.734906] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 22
[    6.734911] pci 0000:00:17.0: PCI INT A -> Link[LRP5] -> GSI 22 (level, low) -> IRQ 22
[    6.734920] pci 0000:00:17.0: setting latency timer to 64
[    6.734926] bus: 00 index 0 io port: [0x00-0xffff]
[    6.734928] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    6.734931] bus: 01 index 0 mmio: [0x0-0x0]
[    6.734933] bus: 01 index 1 mmio: [0x0-0x0]
[    6.734934] bus: 01 index 2 mmio: [0x0-0x0]
[    6.734936] bus: 01 index 3 io port: [0x00-0xffff]
[    6.734939] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    6.734941] bus: 02 index 0 io port: [0xd000-0xdfff]
[    6.734943] bus: 02 index 1 mmio: [0xfaf00000-0xfbffffff]
[    6.734945] bus: 02 index 2 mmio: [0xe0000000-0xf7ffffff]
[    6.734947] bus: 02 index 3 mmio: [0x0-0x0]
[    6.734950] bus: 03 index 0 io port: [0xe000-0xefff]
[    6.734952] bus: 03 index 1 mmio: [0xfe000000-0xfeafffff]
[    6.734954] bus: 03 index 2 mmio: [0xf8000000-0xf9ffffff]
[    6.734956] bus: 03 index 3 mmio: [0x0-0x0]
[    6.734958] bus: 06 index 0 mmio: [0x0-0x0]
[    6.734960] bus: 06 index 1 mmio: [0xfeb00000-0xfebfffff]
[    6.734962] bus: 06 index 2 mmio: [0x0-0x0]
[    6.734964] bus: 06 index 3 mmio: [0x0-0x0]
[    6.734974] NET: Registered protocol family 2
[    6.748059] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    6.748324] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    6.748711] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    6.748974] TCP: Hash tables configured (established 131072 bind 65536)
[    6.748977] TCP reno registered
[    6.756124] NET: Registered protocol family 1
[    6.756243] checking if image is initramfs... it is
[    7.661658] Freeing initrd memory: 9919k freed
[    7.661869] cpufreq: No nForce2 chipset.
[    7.662009] audit: initializing netlink socket (disabled)
[    7.662032] type=2000 audit(1251997175.660:1): initialized
[    7.670213] highmem bounce pool size: 64 pages
[    7.670219] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    7.671638] VFS: Disk quotas dquot_6.5.1
[    7.671701] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.672340] fuse init (API version 7.10)
[    7.672428] msgmni has been set to 1672
[    7.672613] alg: No test for stdrng (krng)
[    7.672625] io scheduler noop registered
[    7.672627] io scheduler anticipatory registered
[    7.672629] io scheduler deadline registered
[    7.672644] io scheduler cfq registered (default)
[    7.695235] pci 0000:02:00.0: Boot video device
[    8.196505] ACPI: EC: input buffer is not empty, aborting transaction
[    8.696505] ACPI: EC: input buffer is not empty, aborting transaction
[    9.196505] ACPI: EC: input buffer is not empty, aborting transaction
[    9.196559] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[    9.196566] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[    9.196626] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[    9.700505] ACPI: EC: input buffer is not empty, aborting transaction
[   10.200505] ACPI: EC: input buffer is not empty, aborting transaction
[   10.700505] ACPI: EC: input buffer is not empty, aborting transaction
[   10.700559] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[   10.700565] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[   10.700624] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[   10.706985] pcieport-driver 0000:00:15.0: setting latency timer to 64
[   10.707151] pcieport-driver 0000:00:15.0: found MSI capability
[   10.707244] pcieport-driver 0000:00:15.0: irq 2303 for MSI/MSI-X
[   10.707282] pci_express 0000:00:15.0:pcie00: allocate port service
[   10.707465] pcieport-driver 0000:00:17.0: setting latency timer to 64
[   10.707629] pcieport-driver 0000:00:17.0: found MSI capability
[   10.707717] pcieport-driver 0000:00:17.0: irq 2302 for MSI/MSI-X
[   10.707754] pci_express 0000:00:17.0:pcie00: allocate port service
[   10.707909] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.707919] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   11.204505] ACPI: EC: input buffer is not empty, aborting transaction
[   11.704505] ACPI: EC: input buffer is not empty, aborting transaction
[   12.204505] ACPI: EC: input buffer is not empty, aborting transaction
[   12.204559] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[   12.204565] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.ADP1._PSR] (Node f6c15750), AE_TIME
[   12.204625] ACPI Exception (ac-0135): AE_TIME, Error reading AC Adapter state [20080926]
[   12.204761] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[   12.204765] ACPI: Power Button (FF) [PWRF]
[   12.204816] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00/PNP0C0D:00/input/input1
[   12.704505] ACPI: EC: input buffer is not empty, aborting transaction
[   13.204505] ACPI: EC: input buffer is not empty, aborting transaction
[   13.704505] ACPI: EC: input buffer is not empty, aborting transaction
[   13.704567] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[   13.704574] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.LID0._LID] (Node f6c158e8), AE_TIME
[   13.704633] ACPI: Lid Switch [LID0]
[   13.704684] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00/PNP0C0E:00/input/input2
[   13.704688] ACPI: Sleep Button (CM) [SLPB]
[   13.704737] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   13.704740] ACPI: Power Button (CM) [PWRB]
[   13.705454] ACPI: SSDT AFFAE3E0, 0594 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[   13.706092] Monitor-Mwait will be used to enter C-1 state
[   13.706095] Monitor-Mwait will be used to enter C-2 state
[   13.706098] Monitor-Mwait will be used to enter C-3 state
[   13.706113] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.706140] processor ACPI_CPU:00: registered as cooling_device0
[   13.706144] ACPI: Processor [P001] (supports 8 throttling states)
[   13.706489] ACPI: SSDT AFFAE350, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[   13.707187] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   13.707208] processor ACPI_CPU:01: registered as cooling_device1
[   13.707212] ACPI: Processor [P002] (supports 8 throttling states)
[   14.204505] ACPI: EC: input buffer is not empty, aborting transaction
[   14.704505] ACPI: EC: input buffer is not empty, aborting transaction
[   15.204505] ACPI: EC: input buffer is not empty, aborting transaction
[   15.204568] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[   15.204574] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[   15.204634] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._STA] (Node f6c15810), AE_TIME
[   15.712505] ACPI: EC: input buffer is not empty, aborting transaction
[   16.212505] ACPI: EC: input buffer is not empty, aborting transaction
[   16.712505] ACPI: EC: input buffer is not empty, aborting transaction
[   16.712566] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080926]
[   16.712572] ACPI Error (psparse-0524): Method parse/execution failed [\_TZ_.THRM._TMP] (Node f6c14e40), AE_TIME
[   16.712700] isapnp: Scanning for PnP cards...
[   17.065663] isapnp: No Plug & Play device found
[   17.076805] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   17.077908] brd: module loaded
[   17.078237] loop: module loaded
[   17.078311] Fixed MDIO Bus: probed
[   17.078317] PPP generic driver version 2.4.2
[   17.078384] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[   17.078416] Driver 'sd' needs updating - please use bus_type methods
[   17.078426] Driver 'sr' needs updating - please use bus_type methods
[   17.078471] ahci 0000:00:0b.0: version 3.0
[   17.079017] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[   17.079026] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 21 (level, low) -> IRQ 21
[   17.079071] ahci 0000:00:0b.0: irq 2301 for MSI/MSI-X
[   17.079113] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl IDE mode
[   17.079116] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pmp pio slum part 
[   17.079120] ahci 0000:00:0b.0: setting latency timer to 64
[   17.079303] scsi0 : ahci
[   17.079400] scsi1 : ahci
[   17.079471] ata1: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 2301
[   17.079474] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 2301
[   17.964010] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   18.015824] ata1.00: ATA-8: WDC WD3200BEVT-00ZCT0, 11.01A11, max UDMA/133
[   18.015827] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   18.017560] ata1.00: configured for UDMA/133
[   18.904010] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   18.919865] ata2.00: ATAPI: HL-DT-STDVDRAM GT10N, 1.01, max UDMA/100
[   18.922882] ata2.00: configured for UDMA/100
[   18.924177] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-0 11.0 PQ: 0 ANSI: 5
[   18.924279] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   18.924296] sd 0:0:0:0: [sda] Write Protect is off
[   18.924299] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.924326] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.924392] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   18.924408] sd 0:0:0:0: [sda] Write Protect is off
[   18.924410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.924435] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.924439]  sda: sda1 sda2 sda3 < sda5 sda6 >
[   18.966857] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.966907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.981915] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT10N     1.01 PQ: 0 ANSI: 5
[   18.989583] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.989586] Uniform CD-ROM driver Revision: 3.20
[   18.989690] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   18.989731] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   18.990428] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   18.991003] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[   18.991011] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 20 (level, low) -> IRQ 20
[   18.991029] ehci_hcd 0000:00:04.1: setting latency timer to 64
[   18.991032] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   18.991094] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[   18.991120] ehci_hcd 0000:00:04.1: debug port 1
[   18.991126] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[   18.991142] ehci_hcd 0000:00:04.1: irq 20, io mem 0xfae7ec00
[   19.000015] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[   19.000084] usb usb1: configuration #1 chosen from 1 choice
[   19.000113] hub 1-0:1.0: USB hub found
[   19.000120] hub 1-0:1.0: 9 ports detected
[   19.000236] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.000786] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   19.000790] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[   19.000803] ohci_hcd 0000:00:04.0: setting latency timer to 64
[   19.000806] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   19.000853] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[   19.000878] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfae7f000
[   19.058053] usb usb2: configuration #1 chosen from 1 choice
[   19.058080] hub 2-0:1.0: USB hub found
[   19.058088] hub 2-0:1.0: 9 ports detected
[   19.058187] uhci_hcd: USB Universal Host Controller Interface driver
[   19.058276] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   19.085225] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.085231] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.088040] mice: PS/2 mouse device common for all mice
[   19.108079] rtc_cmos 00:06: RTC can wake from S4
[   19.108115] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[   19.108165] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[   19.108225] device-mapper: uevent: version 1.0.3
[   19.108317] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   19.108393] device-mapper: multipath: version 1.0.5 loaded
[   19.108396] device-mapper: multipath round-robin: version 1.0.0 loaded
[   19.108476] EISA: Probing bus 0 at eisa.0
[   19.108489] Cannot allocate resource for EISA slot 4
[   19.108502] EISA: Detected 0 cards.
[   19.108618] cpuidle: using governor ladder
[   19.108740] cpuidle: using governor menu
[   19.109286] TCP cubic registered
[   19.109388] NET: Registered protocol family 10
[   19.109842] lo: Disabled Privacy Extensions
[   19.110199] NET: Registered protocol family 17
[   19.110218] Bluetooth: L2CAP ver 2.11
[   19.110220] Bluetooth: L2CAP socket layer initialized
[   19.110223] Bluetooth: SCO (Voice Link) ver 0.6
[   19.110224] Bluetooth: SCO socket layer initialized
[   19.110257] Bluetooth: RFCOMM socket layer initialized
[   19.110264] Bluetooth: RFCOMM TTY layer initialized
[   19.110266] Bluetooth: RFCOMM ver 1.10
[   19.110296] Marking TSC unstable due to TSC halts in idle
[   19.110323] Using IPI No-Shortcut mode
[   19.110404] registered taskstats version 1
[   19.110523]   Magic number: 9:382:994
[   19.110625] rtc_cmos 00:06: setting system clock to 2009-09-03 16:59:47 UTC (1251997187)
[   19.110629] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.110631] EDD information not available.
[   19.110905] Freeing unused kernel memory: 532k freed
[   19.111056] Write protecting the kernel text: 4116k
[   19.111106] Write protecting the kernel read-only data: 1528k
[   19.127958] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   19.199481] compcache: Compressed swap size set to: 708656 KB
[   19.200256] TLSF: pool: f7de9000, init_size=16384, max_size=0, grow_size=16384
[   19.443772] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   19.444430] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[   19.444435] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[   19.444442] forcedeth 0000:00:0a.0: setting latency timer to 64
[   19.572348] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:24:21:69:ec:25
[   19.572353] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[   19.719144] Adding 708652k swap on /dev/ramzswap0.  Priority:100 extents:1 across:708652k
[   20.033695] PM: Starting manual resume from disk
[   20.033699] PM: Resume from partition 8:6
[   20.033701] PM: Checking hibernation image.
[   20.033885] PM: Resume from disk failed.
[   20.078531] kjournald starting.  Commit interval 5 seconds
[   20.078563] EXT3-fs: mounted filesystem with ordered data mode.
[   20.500071] Clocksource tsc unstable (delta = -147255462 ns)
[   26.897873] udev: starting version 141
[   27.164340] cfg80211: Using static regulatory domain info
[   27.164343] cfg80211: Regulatory domain: US
[   27.164345] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.164348] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   27.164351] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   27.164353] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   27.164355] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   27.164358] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   27.164360] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   27.164435] cfg80211: Calling CRDA for country: US
[   27.199644] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.375537] ACPI: PCI Interrupt Link [LN5A] enabled at IRQ 19
[   27.375549] ath9k 0000:06:00.0: PCI INT A -> Link[LN5A] -> GSI 19 (level, low) -> IRQ 19
[   27.375561] ath9k 0000:06:00.0: setting latency timer to 64
[   27.377359] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   27.397526] Linux agpgart interface v0.103
[   27.426413] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   27.617179] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   27.704858] nvidia: module license 'NVIDIA' taints kernel.
[   27.843397] cfg80211: Regulatory domain changed to country: US
[   27.843401] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.843404] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   27.843407] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   27.843409] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.843411] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.843414] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   27.899796] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   27.900339] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   27.900344] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   27.900477] HDA Intel 0000:00:08.0: setting latency timer to 64
[   27.945117] Registered led device: ath9k-phy0::radio
[   27.945160] Registered led device: ath9k-phy0::assoc
[   27.945212] Registered led device: ath9k-phy0::tx
[   27.945252] Registered led device: ath9k-phy0::rx
[   27.945271] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8080000, irq=19
[   27.960658] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   27.960665] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   27.960674] nvidia 0000:02:00.0: setting latency timer to 64
[   27.960867] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.16  Sat Jan 24 19:42:59 PST 2009
[   28.292072] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   28.712631] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04711/0x200000
[   28.797261] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   29.240986] lp: driver loaded but no devices found
[   29.353062] Adding 6562512k swap on /dev/sda6.  Priority:-1 extents:1 across:6562512k
[   29.894708] EXT3 FS on sda5, internal journal
[   31.082716] type=1505 audit(1251989999.469:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2030
[   31.132779] type=1505 audit(1251989999.521:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2034
[   31.132901] type=1505 audit(1251989999.521:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2034
[   31.132945] type=1505 audit(1251989999.521:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2034
[   31.132985] type=1505 audit(1251989999.521:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2034
[   31.161744] type=1505 audit(1251989999.549:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2039
[   31.298924] type=1505 audit(1251989999.685:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2043
[   31.299123] type=1505 audit(1251989999.685:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2043
[   31.328245] type=1505 audit(1251989999.713:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2047
[   36.803888] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.803891] Bluetooth: BNEP filters: protocol multicast
[   36.818257] Bridge firewalling registered
[   38.565946] ppdev: user-space parallel port driver
[   42.610730] eth0: no link during initialization.
[   42.611208] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.633872] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.163934] CPU0 attaching NULL sched-domain.
[   73.163941] CPU1 attaching NULL sched-domain.
[   73.176245] CPU0 attaching sched-domain:
[   73.176249]  domain 0: span 0-1 level MC
[   73.176252]   groups: 0 1
[   73.176259] CPU1 attaching sched-domain:
[   73.176261]  domain 0: span 0-1 level MC
[   73.176263]   groups: 1 0
[   73.253316] wlan0: authenticate with AP f5d0f6b8
[   73.255500] wlan0: authenticated
[   73.255505] wlan0: associate with AP f5d0f6b8
[   73.258128] wlan0: RX AssocResp from f5cfa04a (capab=0x411 status=0 aid=1)
[   73.258132] wlan0: associated
[   73.258935] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   84.032053] wlan0: no IPv6 routers present
[  647.120073] wlan0: beacon loss from AP f5d0f6b8 - sending probe request
[  649.120120] wlan0: no probe response from AP f5d0f6b8 - disassociating
[  650.695556] wlan0: authenticate with AP f5d0f6b8
[  650.697500] wlan0: authenticated
[  650.697503] wlan0: associate with AP f5d0f6b8
[  650.700286] wlan0: RX ReassocResp from f58c804a (capab=0x411 status=0 aid=1)
[  650.700289] wlan0: associated
[ 4957.758502] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 4958.256580] ACPI: EC: input buffer is not empty, aborting transaction
[ 6037.432330] atkbd.c: Unknown key pressed (translated set 2, code 0xf2 on isa0060/serio0).
[ 6037.432334] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.
[ 6037.438811] atkbd.c: Unknown key released (translated set 2, code 0xf2 on isa0060/serio0).
[ 6037.438815] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.

```

I hope this helps

---

### Post by xtremesupremacy3 on 2009-09-04
Okay, need some guidance here:
After scouring Google extensively, I have found a workaround...this is what was posted elsewhere:
```
Hi

on my new Dell Studio 1555 I got the following issue:

On a fresh boot I'm able to change brightness via brightnesskeys and ac-adapter
is detected properly, but as soon as the following error appears:

ACPI: EC: input buffer is not empty, aborting transaction

brightness control is no longer possible. Even the detection whether an
ac-adapter or not is attached fails.

I found that commenting the "goto end;" in ec.c (see below) workarounds this
problem. It may be something similar like the MSI Force-Polling. Maybe you
could find some better fix for that issue (I'm not that kernel-specialist at
all :) )

Best Regards
Norman Haag

static int acpi_ec_transaction(struct acpi_ec *ec, struct transaction *t,
                               int force_poll)                           
{                                                                        
        int status;                                                      
        u32 glk;                                                         
        if (!ec || (!t) || (t->wlen && !t->wdata) || (t->rlen && !t->rdata))
                return -EINVAL;                                             
        if (t->rdata)                                                       
                memset(t->rdata, 0, t->rlen);                               
        mutex_lock(&ec->lock);                                              
        if (ec->global_lock) {                                              
                status = acpi_acquire_global_lock(ACPI_EC_UDELAY_GLK, &glk);
                if (ACPI_FAILURE(status)) {                                 
                        status = -ENODEV;                                   
                        goto unlock;                                        
                }                                                           
        }                                                                   
        if (ec_wait_ibf0(ec)) {                                             
                pr_err(PREFIX "input buffer is not empty, "                 
                                "aborting transaction--\n");                
                status = -ETIME;                                            
                //goto end;                                                 

        }
        status = acpi_ec_transaction_unlocked(ec, t, force_poll);
end:                                                             
        if (ec->global_lock)                                     
                acpi_release_global_lock(glk);                   
unlock:                                                          
        mutex_unlock(&ec->lock);                                 
        return status;                                           
}

```

The thing I find interesting is the code. 
How do I apply it? Do I edit it in a file somewhere(if so where would I find it), do i need to type it out?

I don't know what to do here

Please help

---

### Post by Timo1992 on 2009-09-04
Hi there,
I just got a Dell 1555 Studio.. I'm having the same problems:
I downloaded Backtrack 4, after booting up the same error (ACPI: EC: input buffer is not empty, aborting transaction).. I also cannot login with root and toor, it says incorrect.
cheers

---

### Post by xtremesupremacy3 on 2009-09-06
As you already know, I'm unable to help with the ACPI error, but I do have some new info on it for you and those who have the same problem:

The ACPI error is referring (for me at least) to a battery condition, where my battery is not detected in the kernel. So if you also notice that when you remove your adaptor cable and run on the battery yet the laptop still says your running on mains, then that's the reason.
The only fix to that would be messing with the kernel, which I'm not going to do because I prefer stable-ish kernels than custom ones. So make sure you keep updating.

As for the root problem and 'toor'(?):
Ubuntu comes as standard without root enabled. At Ubuntu you use the command ```
sudo
``` to enable root access. It is possible to enable root but my argument to that would be, why do that if you can use sudo, which also stops you from making any bad mistakes.

Arthur

---

### Post by exjinn on 2009-09-21
I'm having the same issue on an Acer Aspire 6530, when I turn off the monitor using the Fn-F6 keys and then turn it back on, the keyboard and touchpad is disabled. Only a reboot seems to bring them back to life.

---

### Post by xtremesupremacy3 on 2009-09-24
I cannot confirm due to the fact that I do not encounter FN problems on my laptop, however, there have been mention of a few ideas in regards to them problems which might be worth trying out.

Some people claim that the ACPI error is able to be disabled by logging into Windows (that's if you dual boot), and then restarting into Ubuntu. However, I have tried and tested this and at least on my laptop this is not the case, but who knows, it's worth a try.
The same can be said for the Fn key problems.

It's worth checking in the Ubuntu repositories to see if you have a package that may be added to your type of laptop which will cease the problems, and there is always the option to put your monitor to sleep inside Ubuntu without the need to use the Fn keys.

---

### Post by exjinn on 2009-09-30
xset dpms force off

works awesome on my acer. does what the fn combo used to do without causing issues.

---

### Post by suchliang on 2009-10-09
It is system BIOS issue. There is ECDT ACPI table in BIOS. but the EC command port and  data port in incorrect. the correct command port is 0x66 and data port 0x62. but the CR700 is not.
now the BIOS engineer of CR700 has known this issue. please wait new BIOS from Micro star. and you can get the new BIOS from MSI web when the new BIOS been released.

---

### Post by xtremesupremacy3 on 2009-10-31
Well I have really good news.
The amazing guys that provide us with the latest Ubuntu every 6 months, did a fantastic job as per usual, for me anyway. Only minor glitches for me, but thats only seriously minor.
ACPI problem is solved out the box with the battery recognised, the fn combo's work perfectly too.

I can only rate this as solved due to the fact it can be fixed by an upgrade to 9.10

---

### Post by maykelmoya on 2010-11-02
Please see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578506](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578506)

---

