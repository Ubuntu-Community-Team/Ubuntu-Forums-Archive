---
title: "Diagnosing Ubuntu Problems"
date: 2008-09-09
forum: Hardware
---

### Post by deamon_knight on 2008-09-09
I have a customer that has installed Ubuntu 8.04 on his ACER 1690 as his only OS. He reports this has worked for a while, but now the OS will not boot with the Battery installed, the system boots to the splash screen with the progress bar but the progress indicator stops and Ubuntu will not load. With the battery removed, the system will load to the login window and will allow the user to log in, will play the Ubunutu startup music, but the shut off. This is also true when trying to boot to an Ubuntu or Xubuntu 8.04 live CD. However, the unit will boot normally in recovery mode. 

All my diagnostic utilities indicate there is no hardware problem with this system, so I think there may be some power management settings that has gone wrong in Ubuntu. Any suggestions on how I can Identify this?

Thanks

---

### Post by in-dust-rial on 2008-09-09
hi,
i am not a pro... but
try to run the kernel without acpi and post a bug report.
[https://launchpad.net/ubuntu/+bugs]("https://launchpad.net/ubuntu/+bugs")
(i get the feeling, that this bug is known)

because i guess these ppl help you to find out if this is a known bug. and normally the ppl there also know techniques to find out what is wrong!
and maybe there is a solution to the problem allready.

```
dmesg
``` would be the first place to look - if i am correct.(and enable verbouse boot)

i hope you will get better help

good luck

---

### Post by deamon_knight on 2008-09-09
Well, my confusion is that my customer claims the system ran for about a month normally. If something had changed in Ubuntu, I had hoped to identify this by booting a LiveCD. Since neither work, I'm back to square one, with no idea if this is a hardware failure or a software problem.

---

### Post by in-dust-rial on 2008-09-10
bump

---

### Post by deamon_knight on 2008-09-10
Well, I got back into the shop today and tried to boot the system in Recovery mode and now it won't, it stopped with something along the lines of "host controller not responding, something bad has happened", and after a reboot it still stops with

ata2 PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15

---

### Post by deamon_knight on 2008-09-10
I did get the system to boot to safe mode eventually, however I do think there may be a hardware failure. Here is dmesg:

[    8.069772] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.149797] Calibrating delay using timer specific routine.. 3993.28 BogoMIPS (lpj=7986575)
[    8.149893] Security Framework initialized
[    8.149935] SELinux:  Disabled at boot.
[    8.149982] AppArmor: AppArmor initialized
[    8.150021] Failure registering capabilities with primary security module.
[    8.150066] Mount-cache hash table entries: 512
[    8.150209] Initializing cgroup subsys ns
[    8.150249] Initializing cgroup subsys cpuacct
[    8.150294] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[    8.150303] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.150368] CPU: L2 cache: 2048K
[    8.150405] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000 00000000
[    8.150413] Compat vDSO mapped to ffffe000.
[    8.150458] Checking 'hlt' instruction... OK.
[    8.166160] SMP alternatives: switching to UP code
[    8.167811] Freeing SMP alternatives: 11k freed
[    8.167938] Early unpacking initramfs... done
[    8.474905] ACPI: Core revision 20070126
[    8.475009] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.478943] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
[    8.479053] Total of 1 processors activated (3993.28 BogoMIPS).
[    8.480493] ENABLING IO-APIC IRQs
[    8.480711] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.625607] Brought up 1 CPUs
[    8.625677] CPU0 attaching sched-domain:
[    8.625679]  domain 0: span 01
[    8.625681]   groups: 01
[    8.625819] net_namespace: 64 bytes
[    8.625861] Booting paravirtualized kernel on bare hardware
[    8.626281] Time: 16:26:37  Date: 09/10/08
[    8.626338] NET: Registered protocol family 16
[    8.626533] EISA bus registered
[    8.626587] ACPI: bus type pci registered
[    8.626993] PCI: PCI BIOS revision 2.10 entry at 0xfd7be, last bus=7
[    8.627032] PCI: Using configuration type 1
[    8.627076] Setting up standard PCI resources
[    8.631823] ACPI: EC: Look up EC in DSDT
[    8.997572] ACPI: Interpreter enabled
[    8.997610] ACPI: (supports S0 S3 S4 S5)
[    8.997761] ACPI: Using IOAPIC for interrupt routing
[    8.998581] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.022422] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    9.022462] ACPI: EC: driver started in interrupt mode
[    9.022531] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.023086] Force enabled HPET at base address 0xfed00000
[    9.023091] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.023132] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.023832] PCI: Transparent bridge - 0000:00:1e.0
[    9.023933] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.024200] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    9.024310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.024417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.024536] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.028273] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.028706] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.029168] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.029649] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.030079] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.030545] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.031034] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.031523] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.031974] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.032036] pnp: PnP ACPI init
[    9.032076] ACPI: bus type pnp registered
[    9.034221] pnp: PnP ACPI: found 9 devices
[    9.034258] ACPI: ACPI bus type pnp unregistered
[    9.034297] PnPBIOS: Disabled by ACPI PNP
[    9.034517] PCI: Using ACPI for IRQ routing
[    9.034555] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.034604] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    9.034643] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    9.034683] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[    9.034722] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[    9.034761] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[    9.034801] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[    9.034840] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    9.034879] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    9.034919] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[    9.061351] NET: Registered protocol family 8
[    9.061389] NET: Registered protocol family 20
[    9.061557] hpet clockevent registered
[    9.061562] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.061706] hpet0: 3 64-bit timers, 14318180 Hz
[    9.062771] AppArmor: AppArmor Filesystem Enabled
[    9.065343] Time: tsc clocksource has been installed.
[    9.073369] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.073416] system 00:01: iomem range 0xf0000000-0xf0003fff could not be reserved
[    9.073462] system 00:01: iomem range 0xf0004000-0xf0004fff could not be reserved
[    9.073509] system 00:01: iomem range 0xf0005000-0xf0005fff could not be reserved
[    9.073555] system 00:01: iomem range 0xf0008000-0xf000bfff could not be reserved
[    9.073601] system 00:01: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    9.073650] system 00:04: ioport range 0x680-0x6ff has been reserved
[    9.073690] system 00:04: ioport range 0x800-0x80f has been reserved
[    9.073729] system 00:04: ioport range 0x1000-0x107f has been reserved
[    9.073769] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    9.073808] system 00:04: ioport range 0x1600-0x167f has been reserved
[    9.104175] PCI: Bridge: 0000:00:01.0
[    9.104213]   IO window: 3000-3fff
[    9.104250]   MEM window: c8100000-c81fffff
[    9.104288]   PREFETCH window: d0000000-d7ffffff
[    9.104326] PCI: Bridge: 0000:00:1c.0
[    9.105022]   IO window: disabled.
[    9.105060]   MEM window: disabled.
[    9.105098]   PREFETCH window: disabled.
[    9.105136] PCI: Bridge: 0000:00:1c.1
[    9.105172]   IO window: disabled.
[    9.105210]   MEM window: disabled.
[    9.105248]   PREFETCH window: disabled.
[    9.105286] PCI: Bridge: 0000:00:1c.2
[    9.105323]   IO window: disabled.
[    9.105362]   MEM window: disabled.
[    9.105399]   PREFETCH window: disabled.
[    9.105441] PCI: Bus 7, cardbus bridge: 0000:06:01.0
[    9.105479]   IO window: 00001400-000014ff
[    9.105518]   IO window: 00002800-000028ff
[    9.105556]   PREFETCH window: 50000000-53ffffff
[    9.105596]   MEM window: 54000000-57ffffff
[    9.105634] PCI: Bridge: 0000:00:1e.0
[    9.105670]   IO window: disabled.
[    9.105709]   MEM window: c8200000-c82fffff
[    9.105747]   PREFETCH window: disabled.
[    9.105795] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.105870] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.105884] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    9.105959] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.105973] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    9.106048] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.106062] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.106137] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.106145] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.106156] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 18 (level, low) -> IRQ 18
[    9.106237] NET: Registered protocol family 2
[    9.145354] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.145584] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.146333] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.146805] TCP: Hash tables configured (established 131072 bind 65536)
[    9.146846] TCP reno registered
[    9.157434] checking if image is initramfs... it is
[    9.565094] Switched to high resolution mode on CPU 0
[    9.759846] Freeing initrd memory: 7322k freed
[    9.760225] Simple Boot Flag at 0x36 set to 0x1
[    9.760631] audit: initializing netlink socket (disabled)
[    9.760683] audit(1221063997.520:1): initialized
[    9.760873] highmem bounce pool size: 64 pages
[    9.762538] VFS: Disk quotas dquot_6.5.1
[    9.762640] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.762800] io scheduler noop registered
[    9.762838] io scheduler anticipatory registered
[    9.762875] io scheduler deadline registered
[    9.762920] io scheduler cfq registered (default)
[    9.763035] Boot video device is 0000:01:00.0
[    9.763144] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.763170] assign_interrupt_mode Found MSI capability
[    9.763231] Allocate Port Service[0000:00:01.0:pcie00]
[    9.763300] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.763333] assign_interrupt_mode Found MSI capability
[    9.763396] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.763425] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.763491] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.763524] assign_interrupt_mode Found MSI capability
[    9.763587] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.763615] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.763680] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.763718] assign_interrupt_mode Found MSI capability
[    9.763781] Allocate Port Service[0000:00:1c.2:pcie00]
[    9.763812] Allocate Port Service[0000:00:1c.2:pcie02]
[    9.764011] isapnp: Scanning for PnP cards...
[   10.117050] isapnp: No Plug & Play device found
[   10.140314] Real Time Clock Driver v1.12ac
[   10.140452] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.140664] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   10.141441] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 19
[   10.141519] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   10.142079] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.142187] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.142310] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.144497] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.144537] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.152767] mice: PS/2 mouse device common for all mice
[   10.152897] EISA: Probing bus 0 at eisa.0
[   10.152938] Cannot allocate resource for EISA slot 1
[   10.152976] Cannot allocate resource for EISA slot 2
[   10.153014] Cannot allocate resource for EISA slot 3
[   10.153064] EISA: Detected 0 cards.
[   10.153102] cpuidle: using governor ladder
[   10.153139] cpuidle: using governor menu
[   10.153255] NET: Registered protocol family 1
[   10.153313] Using IPI No-Shortcut mode
[   10.153377] registered taskstats version 1
[   10.153502]   Magic number: 8:839:438
[   10.153627] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.153665] EDD information not available.
[   10.153875] Freeing unused kernel memory: 368k freed
[   10.192688] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   10.304346] fuse init (API version 7.9)
[   10.319998] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   10.320173] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.320274] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   10.323316] ACPI: Thermal Zone [THRM] (64 C)
[   10.860348] usbcore: registered new interface driver usbfs
[   10.860412] usbcore: registered new interface driver hub
[   10.872303] usbcore: registered new device driver usb
[   10.880320] USB Universal Host Controller Interface driver v3.0
[   10.880417] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   10.880497] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.880501] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.880859] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.880930] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[   10.881087] usb usb1: configuration #1 chosen from 1 choice
[   10.881145] hub 1-0:1.0: USB hub found
[   10.881185] hub 1-0:1.0: 2 ports detected
[   10.989072] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   10.989158] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.989161] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.989219] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.989290] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[   10.989423] usb usb2: configuration #1 chosen from 1 choice
[   10.989482] hub 2-0:1.0: USB hub found
[   10.989522] hub 2-0:1.0: 2 ports detected
[   11.019215] SCSI subsystem initialized
[   11.058842] libata version 3.00 loaded.
[   11.092247] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.092334] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.092337] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.092395] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.092466] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   11.092595] usb usb3: configuration #1 chosen from 1 choice
[   11.092651] hub 3-0:1.0: USB hub found
[   11.092691] hub 3-0:1.0: 2 ports detected
[   11.196198] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   11.196285] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.196289] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.196345] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.196416] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   11.196549] usb usb4: configuration #1 chosen from 1 choice
[   11.196606] hub 4-0:1.0: USB hub found
[   11.196650] hub 4-0:1.0: 2 ports detected
[   11.300230] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   11.300317] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.300321] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.300381] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   11.304347] ehci_hcd 0000:00:1d.7: debug port 1
[   11.304388] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.304394] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xc8000000
[   11.320022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.320162] usb usb5: configuration #1 chosen from 1 choice
[   11.320220] hub 5-0:1.0: USB hub found
[   11.320261] hub 5-0:1.0: 8 ports detected
[   11.424134] tg3.c:v3.86 (November 9, 2007)
[   11.424201] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.517100] eth0: Tigon3 [partno(BCM95705A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:c0:9f:e8:db:77
[   11.517315] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[   11.517361] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[   11.517428] ACPI: PCI Interrupt 0000:06:01.2[A] -> GSI 18 (level, low) -> IRQ 18
[   11.567233] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c8217000-c82177ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   11.568130] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   11.568231] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.568242] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   11.574516] ata_piix 0000:00:1f.1: version 2.12
[   11.574528] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   11.574621] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.575154] scsi0 : ata_piix
[   11.575435] scsi1 : ata_piix
[   11.575700] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
[   11.575741] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
[   11.904113] ata1.00: ATA-6: HTS541010G9AT00, MBZOA60A, max UDMA/100
[   11.904155] ata1.00: 195371568 sectors, multi 16: LBA48 
[   11.904214] ata1.01: ATAPI: Slimtype DVDRW SLW-831S, WRS1, max UDMA/33
[   11.920047] ata1.00: configured for UDMA/100
[   12.059590] Clocksource tsc unstable (delta = -47435434289 ns)
[   12.063655] Time: hpet clocksource has been installed.
[   12.064366] ata1.01: configured for UDMA/33
[   12.064429] ata2: port disabled. ignoring.
[   12.064544] scsi 0:0:0:0: Direct-Access     ATA      HTS541010G9AT00  MBZO PQ: 0 ANSI: 5
[   12.065063] scsi 0:0:1:0: CD-ROM            Slimtype DVDRW SLW-831S   WRS1 PQ: 0 ANSI: 5
[   12.072264] Driver 'sd' needs updating - please use bus_type methods
[   12.072365] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   12.072414] sd 0:0:0:0: [sda] Write Protect is off
[   12.072452] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.072466] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.072550] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   12.072596] sd 0:0:0:0: [sda] Write Protect is off
[   12.072634] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.072647] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.072695]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   12.080960]  sda1 sda2 < sda5 >
[   12.081344] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.086459] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.086516] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   12.089622] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   12.089666] Uniform CD-ROM driver Revision: 3.20
[   12.089740] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   12.174747] Attempting manual resume
[   12.174786] swsusp: Resume From Partition 8:5
[   12.174787] PM: Checking swsusp image.
[   12.174916] PM: Resume from disk failed.
[   12.188333] kjournald starting.  Commit interval 5 seconds
[   12.188383] EXT3-fs: mounted filesystem with ordered data mode.
[   12.204199] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000070d4d5]
[   14.017787] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.037793] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.895289] Linux agpgart interface v0.102
[   14.987121] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.039128] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.320442] input: Power Button (FF) as /devices/virtual/input/input2
[   15.330872] ACPI: Power Button (FF) [PWRF]
[   15.331021] input: Lid Switch as /devices/virtual/input/input3
[   15.331140] ACPI: Lid Switch [LID]
[   15.331226] input: Power Button (CM) as /devices/virtual/input/input4
[   15.342858] ACPI: Power Button (CM) [PWRB]
[   15.342951] input: Sleep Button (CM) as /devices/virtual/input/input5
[   15.358850] ACPI: Sleep Button (CM) [SLPB]
[   15.365602] ACPI: AC Adapter [ACAD] (on-line)
[   15.502623] ACPI: Battery Slot [BAT1] (battery present)
[   15.502710] ACPI: Battery Slot [BAT2] (battery absent)
[   16.087664] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6
[   16.098452] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.169829] iTCO_vendor_support: vendor-support=0
[   17.237722] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.237865] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.237941] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.397684] intel_rng: FWH not detected
[   17.617705] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   17.693447] ieee80211_crypt: registered algorithm 'NULL'
[   17.769435] Yenta: CardBus bridge found at 0000:06:01.0 [1025:0066]
[   17.769494] Yenta: Enabling burst memory read transactions
[   17.769534] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.769573] Yenta: Routing CardBus interrupts to PCI
[   17.769613] Yenta TI: socket 0000:06:01.0, mfunc 0x01c21b22, devctl 0x64
[   17.849201] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.849247] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.002370] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   18.002414] Socket status: 30000006
[   18.002452] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #08
[   18.002500] pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[   18.038789] ACPI: PCI Interrupt 0000:06:01.3[A] -> GSI 18 (level, low) -> IRQ 18
[   18.068429] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   18.068479] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.068592] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.097975] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.459391] irda_init()
[   18.459405] NET: Registered protocol family 23
[   18.520983] ACPI: WMI-Acer: Mapper loaded
[   18.567243] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   18.567297] acer_acpi: No or unsupported WMI interface, unable to load.
[   18.604366] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   18.647806] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.671359] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   18.671378] nsc-ircc, chip->init
[   18.671426] nsc-ircc, Found chip at base=0x164e
[   18.671490] nsc-ircc, driver loaded (Dag Brattli)
[   18.671530] nsc_ircc_open(), can't get iobase of 0x2f8
[   18.671597] nsc-ircc, Found chip at base=0x164e
[   18.671660] nsc-ircc, driver loaded (Dag Brattli)
[   18.671698] nsc_ircc_open(), can't get iobase of 0x2f8
[   18.671939] nsc-ircc 00:06: disabled
[   19.583809] ipw2200: Radio Frequency Kill Switch is On:
[   19.583811] Kill switch must be turned off for wireless networking to work.
[   19.606685] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   19.606776] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[   19.606865] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   19.634615] cs: IO port probe 0x100-0x3af: clean.
[   19.635831] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.636436] cs: IO port probe 0x820-0x8ff: clean.
[   19.636914] cs: IO port probe 0xc00-0xcf7: clean.
[   19.637503] cs: IO port probe 0xa00-0xaff: clean.
[   19.646638] intel8x0_measure_ac97_clock: measured 54021 usecs
[   19.646679] intel8x0: clocking to 48000
[   19.740242] lp: driver loaded but no devices found
[   19.901941] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
[   19.974500] EXT3 FS on sda1, internal journal
[   20.670791] ACPI: ACPI Dock Station Driver 
[   20.676704] ACPI: \_SB_.PCI0.PATA.PRID.BAY_: found ejectable bay
[   20.676709] ACPI: \_SB_.PCI0.PATA.PRID.BAY_: Adding notify handler
[   20.676734] ACPI: Error installing bay notify handler
[   20.676737] ACPI: Bay [\_SB_.PCI0.PATA.PRID.BAY_] Added
[   21.196127] NET: Registered protocol family 10
[   21.196525] lo: Disabled Privacy Extensions
[   21.568461] apm: BIOS not found.
[   21.640284] ppdev: user-space parallel port driver
[   21.672089] audit(1221064073.944:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5446 profile="/usr/sbin/cupsd" namespace="default"
[   54.349120] Marking TSC unstable due to: cpufreq changes.
[   41.366178] ttyS1: LSR safety check engaged!
[   22.396270] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.417458] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   33.698857] Bluetooth: Core ver 2.11
[   33.699401] NET: Registered protocol family 31
[   33.699405] Bluetooth: HCI device and connection manager initialized
[   33.699409] Bluetooth: HCI socket layer initialized
[   33.742447] Bluetooth: L2CAP ver 2.9
[   33.742452] Bluetooth: L2CAP socket layer initialized
[   22.566270] Bluetooth: RFCOMM socket layer initialized
[   22.566283] Bluetooth: RFCOMM TTY layer initialized
[   22.566284] Bluetooth: RFCOMM ver 1.8
[   22.881522] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   22.881526] tg3: eth0: Flow control is on for TX and on for RX.
[   22.882921] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   57.261162] [drm] Initialized drm 1.1.0 20060810
[   57.272295] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   57.272310] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   57.272432] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   57.535919] NET: Registered protocol family 17
[   57.575692] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   57.627388] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   57.629312] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:85:7a:ab:f6:08:00 SRC=10.105.1.106 DST=10.105.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3171 PROTO=UDP SPT=137 DPT=137 LEN=58 
[   57.630220] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.251 LEN=224 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=204 
[   57.632716] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.251 LEN=140 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=120 
[   57.646963] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.251 LEN=224 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=204 
[   57.650758] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   57.655287] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.251 LEN=224 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=204 
[   57.755172] IN= OUT=eth0 SRC=10.105.1.107 DST=224.0.0.251 LEN=206 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=186 
[   57.756091] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:85:7a:ab:f6:08:00 SRC=10.105.1.106 DST=10.105.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3175 PROTO=UDP SPT=137 DPT=137 LEN=58 
[   57.987201] [drm] Setting GART location based on new memory map
[   57.988051] [drm] Loading R300 Microcode
[   57.988101] [drm] writeback test succeeded in 1 usecs
[   23.953296] eth0: no IPv6 routers present
[   96.872804] synaptics: using relaxed packet validation

---

### Post by in-dust-rial on 2008-09-10
can't help you here...
> [ 15.365602] ACPI: AC Adapter [ACAD] (on-line)
[ 15.502623] ACPI: Battery Slot [BAT1] (battery present)
[ 15.502710] ACPI: Battery Slot [BAT2] (battery absent)
if its a single core, and you know what are youd oing, you might try acpi=no while booting! but i consider all activities on this machine risky - espacially these actions with battery connected...!

go IRC to #Ubuntu channel and find premium live aid!

GOOD LUCK

---

### Post by deamon_knight on 2008-09-10
Thanks for the help, but I don't know enough about Linux to understand what you are telling me here. Do those ACPI entries indicate something more than it detects the battery?

---

