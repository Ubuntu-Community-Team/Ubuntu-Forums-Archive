---
title: "PCMCIA card no longer works with LTS"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by AdamL on 2006-07-26
A card that used to work fine stopped working when I upgraded to LTS:

[17231677.280000] cs: pcmcia_socket0: unable to apply power.
[17231677.952000] pccard: PCMCIA card inserted into slot 0
[17231677.952000] pcmcia: registering new device pcmcia0.0

This is an ACG RFID reader and it should come up as device /dev/ttyS1 using built in serial drivers.

I've looked at the various threads and support pages which seem relevant but I don't think they apply in this case... e.g.:

  [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/powerbugs.html#1](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/powerbugs.html#1)

However, here are the various debug output they mention:

[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000002fef0000 - 000000002feff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002feff000 - 000000002ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000002ff00000 - 000000002ff80000 (usable)
[17179569.184000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 767MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 196480
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 192384 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f69a0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x2fef9238
[17179569.184000] ACPI: FADT (v001 MATBIO CF72-4   0x06040000 MAT  0x00000001) @ 0x2fefef64
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x2fefefd8
[17179569.184000] ACPI: DSDT (v001 MATBIO   CF72-4 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cf800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/mapper/Ubuntu-root ro quiet splash pci=routeirq
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01704000)
[17179569.184000] Using pmtmr for high-res timesource
[17179572.692000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.692000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.716000] Memory: 766952k/785920k available (2110k kernel code, 18316k reserved, 595k data, 332k init, 0k highmem)
[17179572.716000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.796000] Calibrating delay using timer specific routine.. 3594.33 BogoMIPS (lpj=7188673)
[17179572.796000] Mount-cache hash table entries: 512
[17179572.796000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.796000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.796000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.796000] CPU: L2 cache: 512K
[17179572.796000] CPU: Hyper-Threading is disabled
[17179572.796000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00000000 00000000 00000000
[17179572.796000] mtrr: v2.0 (20020519)
[17179572.796000] Enabling fast FPU save and restore... done.
[17179572.796000] Enabling unmasked SIMD FPU exception support... done.
[17179572.812000] SMP alternatives: switching to UP code
[17179573.544000] ACPI: Looking for DSDT ... not found!
[17179573.608000] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz stepping 07
[17179573.608000] Local APIC not detected. Using dummy APIC emulation.
[17179573.612000] ACPI: bus type pci registered
[17179573.612000] PCI: PCI BIOS revision 2.10 entry at 0xfd98e, last bus=2
[17179573.612000] PCI: Using configuration type 1
[17179573.612000] ACPI: Subsystem revision 20051216
[17179573.612000] ACPI: Interpreter enabled
[17179573.612000] ACPI: Using PIC for interrupt routing
[17179573.616000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.616000] PCI: Probing PCI hardware (bus 00)
[17179573.652000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179573.652000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179573.652000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.656000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.656000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.656000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179573.664000] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[17179573.664000] ACPI: PCI Interrupt Link [LNKB] (IRQs *9)
[17179573.664000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9)
[17179573.664000] ACPI: PCI Interrupt Link [LNKD] (IRQs 9) *0, disabled.
[17179573.664000] ACPI: PCI Interrupt Link [LNKE] (IRQs *9)
[17179573.664000] ACPI: PCI Interrupt Link [LNKF] (IRQs *9)
[17179573.664000] ACPI: PCI Interrupt Link [LNKG] (IRQs 9) *0, disabled.
[17179573.664000] ACPI: PCI Interrupt Link [LNKH] (IRQs *9)
[17179573.716000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179573.720000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.720000] pnp: PnP ACPI init
[17179573.812000] pnp: PnP ACPI: found 17 devices
[17179573.812000] PnPBIOS: Disabled by ACPI PNP
[17179573.812000] PCI: Using ACPI for IRQ routing
[17179573.812000] PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified
[17179573.812000] **** SET: Misaligned resource pointer: c17da242 Type 07 Len 0
[17179573.812000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[17179573.812000] PCI: setting IRQ 9 as level-triggered
[17179573.812000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179573.812000] **** SET: Misaligned resource pointer: c17da242 Type 07 Len 0
[17179573.812000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[17179573.812000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179573.812000] **** SET: Misaligned resource pointer: c17da242 Type 07 Len 0
[17179573.812000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[17179573.812000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179573.812000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179573.812000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179573.812000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179573.812000] **** SET: Misaligned resource pointer: c17da242 Type 07 Len 0
[17179573.812000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[17179573.812000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179573.812000] **** SET: Misaligned resource pointer: c17da242 Type 07 Len 0
[17179573.812000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[17179573.812000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[17179573.820000] PCI: Bridge: 0000:00:01.0
[17179573.820000]   IO window: 2000-2fff
[17179573.820000]   MEM window: e8100000-e81fffff
[17179573.820000]   PREFETCH window: f0000000-f7ffffff
[17179573.820000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[17179573.820000]   IO window: 00003000-000030ff
[17179573.820000]   IO window: 00003800-000038ff
[17179573.820000]   PREFETCH window: 40000000-41ffffff
[17179573.820000]   MEM window: 44000000-45ffffff
[17179573.820000] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[17179573.820000]   IO window: 00003c00-00003cff
[17179573.820000]   IO window: 00001400-000014ff
[17179573.820000]   PREFETCH window: 42000000-43ffffff
[17179573.820000]   MEM window: 46000000-47ffffff
[17179573.820000] PCI: Bridge: 0000:00:1e.0
[17179573.820000]   IO window: 3000-3fff
[17179573.820000]   MEM window: e8200000-e82fffff
[17179573.820000]   PREFETCH window: 40000000-43ffffff
[17179573.820000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.820000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179573.820000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179573.820000] Simple Boot Flag at 0x39 set to 0x1
[17179573.820000] io scheduler noop registered
[17179573.820000] io scheduler anticipatory registered
[17179573.820000] io scheduler deadline registered
[17179573.820000] io scheduler cfq registered
[17179573.820000] isapnp: Scanning for PnP cards...
[17179574.176000] isapnp: No Plug & Play device found
[17179574.200000] PNP: PS/2 Controller [PNP0303:K101,PNP0f13:MOU1] at 0x60,0x64 irq 1,12
[17179574.204000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.204000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.204000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.204000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.208000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.208000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.248000] Using IPI No-Shortcut mode
[17179574.248000] ACPI wakeup devices: 
[17179574.248000] MPCA CDB0 CDB1  LAN USBA PWRB  LID 
[17179574.248000] ACPI: (supports S0 S3 S4 S5)
[17179574.248000] Freeing unused kernel memory: 332k freed
[17179574.316000] vga16fb: mapped to 0xc00a0000
[17179574.456000] fb0: VGA16 VGA frame buffer device
[17179575.584000] Capability LSM initialized
[17179575.640000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.640000] ACPI: Processor [CPU0] (supports 4 throttling states)
[17179575.644000] ACPI: Thermal Zone [TZC] (67 C)
[17179576.500000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179576.500000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.500000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179576.500000] ICH3M: chipset revision 2
[17179576.500000] ICH3M: not 100% native mode: will probe irqs later
[17179576.500000]     ide0: BM-DMA at 0x1820-0x1827, BIOS settings: hda:DMA, hdb:pio
[17179576.500000]     ide1: BM-DMA at 0x1828-0x182f, BIOS settings: hdc:DMA, hdd:pio
[17179579.336000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179579.336000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.336000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.336000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.336000] uhci_hcd 0000:00:1d.0: irq 9, io base 0x00001800
[17179579.336000] hub 1-0:1.0: USB hub found
[17179579.336000] hub 1-0:1.0: 2 ports detected
[17179579.524000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179579.880000] input: USB OpticalWheel Mouse as /class/input/input1
[17179579.880000] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:1d.0-1
[17179579.880000] usbcore: registered new driver usbhid
[17179579.880000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179604.488000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179604.508000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179604.784000] input: PC Speaker as /class/input/input2
[17179605.192000] hw_random: RNG not detected
[17179605.364000] Linux agpgart interface v0.101 (c) Dave Jones
[17179605.440000] agpgart: Detected an Intel i845 Chipset.
[17179605.448000] agpgart: AGP aperture is 64M @ 0xec000000
[17179605.612000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[17179605.612000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179605.612000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179605.840000] Floppy drive(s): fd0 is 1.44M
[17179605.856000] FDC 0 is a National Semiconductor PC87306
[17179605.928000] intel8x0_measure_ac97_clock: measured 54954 usecs
[17179605.928000] intel8x0: clocking to 48000
[17179605.928000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179605.928000] Yenta: CardBus bridge found at 0000:02:00.0 [10f7:8338]
[17179606.056000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[17179606.056000] Socket status: 30000006
[17179606.056000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179606.056000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179606.056000] cs: IO port probe 0x3000-0x3fff: clean.
[17179606.056000] pcmcia: parent PCI bridge Memory window: 0xe8200000 - 0xe82fffff
[17179606.056000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[17179606.056000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179606.056000] Yenta: CardBus bridge found at 0000:02:00.1 [10f7:8338]
[17179606.092000] input: PS/2 Generic Mouse as /class/input/input3
[17179606.112000] 8139too Fast Ethernet driver 0.9.27
[17179606.160000] parport: PnPBIOS parport detected.
[17179606.160000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179606.184000] Yenta: ISA IRQ mask 0x0c38, PCI irq 9
[17179606.184000] Socket status: 30000820
[17179606.184000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179606.184000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179606.184000] cs: IO port probe 0x3000-0x3fff: clean.
[17179606.184000] pcmcia: parent PCI bridge Memory window: 0xe8200000 - 0xe82fffff
[17179606.184000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[17179606.212000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[17179606.212000] eth0: RealTek RTL8139 at 0xf0a24400, 00:80:45:12:bc:0a, IRQ 9
[17179606.212000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179606.224000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179606.260000] parport: PnPBIOS parport detected.
[17179606.260000] pnp: Device 00:0e disabled.
[17179606.516000] pcc_acpi: loading...
[17179606.520000] input: PCC Extra Driver as /class/input/input4
[17179606.868000] pccard: CardBus card inserted into slot 1
[17179606.904000] ath_hal: module license 'Proprietary' taints kernel.
[17179606.904000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179607.016000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179607.028000] ath_rate_sample: 1.2
[17179607.036000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179607.036000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[17179607.036000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179607.148000] cs: IO port probe 0x100-0x4ff: excluding 0x338-0x33f 0x4d0-0x4d7
[17179607.152000] cs: IO port probe 0xc00-0xcf7: clean.
[17179607.152000] cs: IO port probe 0xa00-0xaff: clean.
[17179607.152000] cs: IO port probe 0x100-0x4ff: excluding 0x338-0x33f 0x4d0-0x4d7
[17179607.156000] cs: IO port probe 0xc00-0xcf7: clean.
[17179607.156000] cs: IO port probe 0xa00-0xaff: clean.
[17179607.288000] Build date: Jul 10 2006
[17179607.288000] Debugging version (IEEE80211)
[17179607.288000] ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179607.288000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179607.288000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179607.288000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179607.288000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179607.288000] Debugging version (ATH)
[17179607.288000] ath0: Atheros 5212: mem=0x46000000, irq=9
[17179607.724000] ppdev: user-space parallel port driver
[17179607.852000] Adding 1605624k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1 across:1605624k
[17179608.036000] EXT3 FS on dm-0, internal journal
[17179608.288000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179608.288000] md: bitmap version 4.39
[17179611.264000] cdrom: open failed.
[17179612.132000] kjournald starting.  Commit interval 5 seconds
[17179612.132000] EXT3 FS on hda1, internal journal
[17179612.132000] EXT3-fs: mounted filesystem with ordered data mode.
[17179616.668000] ACPI: AC Adapter [AC] (on-line)
[17179616.680000] ACPI: Battery Slot [BATA] (battery present)
[17179616.680000] ACPI: Battery Slot [BATB] (battery absent)
[17179616.792000] ACPI: Power Button (FF) [PWRF]
[17179616.792000] ACPI: Power Button (CM) [PWRB]
[17179616.792000] ACPI: Lid Switch [LID]
[17179616.964000] ibm_acpi: ec object not found
[17179626.480000] lp0: using parport0 (interrupt-driven).
[17179627.988000] [drm] Initialized drm 1.0.1 20051102
[17179628.020000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179628.024000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179628.932000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179628.932000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179628.932000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179629.400000] [drm] Setting GART location based on new memory map
[17179629.400000] [drm] writeback test succeeded in 2 usecs
[17179632.464000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179632.464000] apm: overridden by ACPI.
[17179650.624000] /dev/vmmon[4999]: Module vmmon: registered with major=10 minor=165
[17179650.624000] /dev/vmmon[4999]: Module vmmon: initialized
[17179652.036000] /dev/vmnet: open called by PID 5032 (vmnet-bridge)
[17179652.036000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179652.036000] /dev/vmnet: port on hub 0 successfully opened
[17179652.036000] bridge-eth0: peer interface eth0 not found, will wait for it to come up
[17179652.036000] bridge-eth0: attached
[17179652.048000] /dev/vmnet: open called by PID 5041 (vmnet-bridge)
[17179652.048000] /dev/vmnet: hub 2 does not exist, allocating memory.
[17179652.052000] /dev/vmnet: port on hub 2 successfully opened
[17179652.052000] bridge-ath0: peer interface ath0 not found, will wait for it to come up
[17179652.052000] bridge-ath0: attached
[17179698.280000] fuse init (API version 7.3)
[17179787.804000] cs: pcmcia_socket0: unable to apply power.
[17179788.476000] pccard: PCMCIA card inserted into slot 0
[17179788.476000] cs: memory probe 0xe8200000-0xe82fffff: excluding 0xe8200000-0xe820ffff
[17179788.480000] pcmcia: registering new device pcmcia0.0
[17179808.920000] bridge-ath0: enabling the bridge
[17179808.920000] bridge-ath0: up
[17179819.040000] ath0: no IPv6 routers present
[17180379.328000] pccard: card ejected from slot 0
[17180379.336000] AK4117 ready timeout (read)
[17231677.280000] cs: pcmcia_socket0: unable to apply power.
[17231677.952000] pccard: PCMCIA card inserted into slot 0
[17231677.952000] pcmcia: registering new device pcmcia0.0

(note the ATH0 card is working fine).
also, i had to delete some stuff to fit in forum limits.

#  lspci -vv
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [e4] #09 [d104]
        Capabilities: [a0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x1

0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e8100000-e81fffff
        Prefetchable memory behind bridge: f0000000-f7ffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02) (prog-if 00 [UHCI])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 9
        Region 4: I/O ports at 1800 [size=32]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=0a, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e8200000-e82fffff
        Prefetchable memory behind bridge: 40000000-43ffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 9
        Region 0: I/O ports at <ignored>
        Region 1: I/O ports at <ignored>
        Region 2: I/O ports at <ignored>
        Region 3: I/O ports at <ignored>
        Region 4: I/O ports at 1820 [size=16]
        Region 5: Memory at e8000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 9
        Region 4: I/O ports at 1840 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8346
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 9
        Region 0: I/O ports at 1c00 [size=256]
        Region 1: I/O ports at 1880 [size=64]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA])
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR+ FastB2B+
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 2000 [size=256]
        Region 2: Memory at e8100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at e8120000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
                Status: RQ=48 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x1
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at e8201000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 40000000-41fff000 (prefetchable)
        Memory window 1: 44000000-45fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003800-000038ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0000:02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin B routed to IRQ 9
        Region 0: Memory at e8202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 42000000-43fff000 (prefetchable)
        Memory window 1: 46000000-47fff000
        I/O window 0: 00003c00-00003cff
        I/O window 1: 00001400-000014ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
        16-bit legacy interface ports at 0001

0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Matsushita Electric Industrial Co., Ltd.: Unknown device 8338
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 9
        Region 0: I/O ports at 3400 [size=256]
        Region 1: Memory at e8200400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc: Unknown device 3a07
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at 46000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

any ideas?

thanks,
Adam

---

### Post by svenna on 2006-07-26
This actually happend to me too, when I upgraded the kernel to 2.6.15-26. What I did was to reinstall the pcmcia-cs package with Synaptic, and everything started working again.

---

### Post by AdamL on 2006-07-26
Thanks for the reply but that didn't work... I tried reinstalling both pcmcia-cs and pcmciautils (as that's what's used on LTS), as well as removing pcmcia-cs altogether  and then re-installing pcmciautils but without joy.

---

