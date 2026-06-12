---
title: "Very sudden random shutdowns in compaq nx9600"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by Filladdar on 2008-04-13
I've been having problems with my compaq nx9600 very suddenly shutting down. Shutting down isn't even necessarily a good word for it, it occurs almost as if my computer got unplugged, and very suddenly powers down. I never keep a battery in it and always run it on AC power. It seems to happen randomly and it doesn't seem to matter what I'm doing with my computer. It's happened while just browsing the web, and so it seems odd that it'd be due to overheating or something like that.

I'm pretty new to Ubuntu, so I'm not really sure what info to give. It's happened a couple of times while I've been trying to update, and once I had trouble starting back up afterwards and had to start in terminal and to the dpkg or whatever thing.

Any help would be greatly appreciated. I never know when it's going to turn off next, and I'm trying to switch from windows. This problem never happens when I'm booted into XP, only with Ubuntu.

Also, incase it's relevent, cpu usage is in the single digits right now.

---

### Post by stuart brogan on 2008-04-13
I don't have the answer, however, maybe I could get you headed in the right direction.

If you open a terminal and run dmesg then copy and paste it here maybe some of the gurus can help better. 

Also if it is an Intel board there is a utility called powertop 
$ sudo apt-get powertop
This unique little utility might give you some insights as it will tell you how to fix some problems.

If no one answers after pasting your dmesg, I would look in there for errors and do a Google search.

---

### Post by Filladdar on 2008-04-16
Thanks... I'll try those things.
I've been paying a bit more attention, and I notice that it seems to do it much more frequently when I'm trying to update. In fact I think every time lately that I've tried to download or update programs, it's shut down. I noticed that when I was updating, my cpu was working pretty hard.

---

### Post by Filladdar on 2008-04-16
Heres as much as it showed me... seems like the beginning got cut off. I tried to do sudo apt-get powertop, but it seemed like it couldn't find the application. I did a search for it in the add-remove utility and couldn't find it either.

[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F79C0 checksum 0
[    0.000000] ACPI: RSDP 000F79C0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 3FEF1AEE, 0034 (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: FACP 3FEF8EC0, 0074 (r1 HP     3082      6040000 PTL         3)
[    0.000000] ACPI: DSDT 3FEF1B22, 739E (r1 HP     3082      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEF9FC0, 0040
[    0.000000] ACPI: MCFG 3FEF8F34, 003C (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: APIC 3FEF8F70, 0068 (r1 HP     3082      6040000  LTP        0)
[    0.000000] ACPI: BOOT 3FEF8FD8, 0028 (r1     HP 3082      6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 259827
[    0.000000] Kernel command line: root=UUID=7095c3c9-6739-480e-a205-e40a048aee69 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3591.307 MHz processor.
[   23.115425] Console: colour VGA+ 80x25
[   23.115735] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.116035] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.135847] Memory: 1026872k/1047488k available (2015k kernel code, 19956k reserved, 915k data, 364k init, 129984k highmem)
[   23.135856] virtual kernel memory layout:
[   23.135857]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   23.135858]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.135859]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.135859]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.135860]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   23.135861]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   23.135862]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   23.135865] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.135900] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   23.215884] Calibrating delay using timer specific routine.. 7188.39 BogoMIPS (lpj=14376783)
[   23.215907] Security Framework v1.0.0 initialized
[   23.215911] SELinux:  Disabled at boot.
[   23.215922] Mount-cache hash table entries: 512
[   23.216036] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000451d 00000000 00000000
[   23.216044] monitor/mwait feature present.
[   23.216046] using mwait in idle threads.
[   23.216052] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.216054] CPU: L2 cache: 1024K
[   23.216056] CPU: Physical Processor ID: 0
[   23.216058] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000451d 00000000 00000000
[   23.216067] Compat vDSO mapped to ffffe000.
[   23.216081] Checking 'hlt' instruction... OK.
[   23.231975] SMP alternatives: switching to UP code
[   23.232379] Early unpacking initramfs... done
[   23.467908] ACPI: Core revision 20070126
[   23.467962] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.484419] CPU0: Intel(R) Pentium(R) 4 CPU 3.60GHz stepping 01
[   23.484435] SMP alternatives: switching to SMP code
[   23.484535] Booting processor 1/1 eip 3000
[   23.494712] Initializing CPU#1
[   23.571706] Calibrating delay using timer specific routine.. 7182.55 BogoMIPS (lpj=14365113)
[   23.571714] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000451d 00000000 00000000
[   23.571720] monitor/mwait feature present.
[   23.571727] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.571729] CPU: L2 cache: 1024K
[   23.571732] CPU: Physical Processor ID: 0
[   23.571734] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000451d 00000000 00000000
[   23.572081] CPU1: Intel(R) Pentium(R) 4 CPU 3.60GHz stepping 01
[   23.572117] Total of 2 processors activated (14370.94 BogoMIPS).
[   23.572262] ENABLING IO-APIC IRQs
[   23.572438] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.719735] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.739738] Brought up 2 CPUs
[   23.834616] migration_cost=90
[   23.834776] Booting paravirtualized kernel on bare hardware
[   23.834839] Time: 22:14:20  Date: 03/16/108
[   23.834861] NET: Registered protocol family 16
[   23.834944] EISA bus registered
[   23.834949] ACPI: bus type pci registered
[   23.875705] PCI: PCI BIOS revision 2.10 entry at 0xfd95e, last bus=11
[   23.875707] PCI: Using configuration type 1
[   23.875708] Setting up standard PCI resources
[   23.884758] ACPI: EC: Look up EC in DSDT
[   23.885319] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   23.904470] ACPI: Interpreter enabled
[   23.904474] ACPI: (supports S0 S3 S4 S5)
[   23.904488] ACPI: Using IOAPIC for interrupt routing
[   23.908901] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   23.908946] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.908958] PCI: Probing PCI hardware (bus 00)
[   23.909490] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   23.909494] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   23.910151] PCI: Transparent bridge - 0000:00:1e.0
[   23.910246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.910481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[   23.910583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   23.910683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   23.915952] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *10 11 14 15)
[   23.916027] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 10 11 14 15) *5
[   23.916101] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 10 *11 14 15)
[   23.916173] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 10 11 14 15) *7
[   23.916249] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 10 11 14 15) *7
[   23.916325] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 10 11 14 15) *0, disabled.
[   23.916401] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 10 *11 14 15)
[   23.916476] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 10 11 14 15) *7
[   23.916571] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.916581] pnp: PnP ACPI init
[   23.916590] ACPI: bus type pnp registered
[   23.918156] pnp: PnP ACPI: found 9 devices
[   23.918158] ACPI: ACPI bus type pnp unregistered
[   23.918162] PnPBIOS: Disabled by ACPI PNP
[   23.918642] PCI: Using ACPI for IRQ routing
[   23.918646] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.918651] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   23.918688] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   23.918722] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   23.937544] NET: Registered protocol family 8
[   23.937546] NET: Registered protocol family 20
[   23.937608] pnp: 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[   23.937615] pnp: 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[   23.937617] pnp: 00:02: iomem range 0xfed13000-0xfed13fff has been reserved
[   23.937620] pnp: 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[   23.937622] pnp: 00:02: iomem range 0xfed20000-0xfed8ffff has been reserved
[   23.939600] Time: tsc clocksource has been installed.
[   23.967934] PCI: Bridge: 0000:00:01.0
[   23.967937]   IO window: 4000-4fff
[   23.967941]   MEM window: c8100000-c81fffff
[   23.967945]   PREFETCH window: d0000000-d7ffffff
[   23.967948] PCI: Bridge: 0000:00:1c.0
[   23.967950]   IO window: disabled.
[   23.967954]   MEM window: disabled.
[   23.967957]   PREFETCH window: disabled.
[   23.967968] PCI: Bus 12, cardbus bridge: 0000:0b:00.0
[   23.967970]   IO window: 00005400-000054ff
[   23.967974]   IO window: 00005800-000058ff
[   23.967979]   PREFETCH window: 50000000-53ffffff
[   23.967983]   MEM window: 58000000-5bffffff
[   23.967987] PCI: Bridge: 0000:00:1e.0
[   23.967990]   IO window: 5000-5fff
[   23.967994]   MEM window: c8200000-c82fffff
[   23.967998]   PREFETCH window: 50000000-55ffffff
[   23.968015] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.968020] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.968037] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   23.968043] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.968053] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.968066] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.968078] NET: Registered protocol family 2
[   24.007686] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.007763] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   24.008548] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.008800] TCP: Hash tables configured (established 131072 bind 65536)
[   24.008802] TCP reno registered
[   24.019832] checking if image is initramfs... it is
[   24.471368] Switched to high resolution mode on CPU 0
[   24.471441] Switched to high resolution mode on CPU 1
[   24.485898] Freeing initrd memory: 7051k freed
[   24.485992] Simple Boot Flag at 0x36 set to 0x1
[   24.486401] audit: initializing netlink socket (disabled)
[   24.486413] audit(1208384060.160:1): initialized
[   24.486497] highmem bounce pool size: 64 pages
[   24.488454] VFS: Disk quotas dquot_6.5.1
[   24.488505] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.488594] io scheduler noop registered
[   24.488596] io scheduler anticipatory registered
[   24.488598] io scheduler deadline registered
[   24.488611] io scheduler cfq registered (default)
[   24.488698] Boot video device is 0000:01:00.0
[   24.488779] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.488815] assign_interrupt_mode Found MSI capability
[   24.488818] Allocate Port Service[0000:00:01.0:pcie00]
[   24.488894] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.488933] assign_interrupt_mode Found MSI capability
[   24.488936] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.488970] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.489117] isapnp: Scanning for PnP cards...
[   24.840541] isapnp: No Plug & Play device found
[   24.862968] Real Time Clock Driver v1.12ac
[   24.863053] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.863683] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 18
[   24.863690] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   24.864235] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.864407] input: Macintosh mouse button emulation as /class/input/input0
[   24.864482] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   24.867052] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.867058] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.867242] mice: PS/2 mouse device common for all mice
[   24.867356] EISA: Probing bus 0 at eisa.0
[   24.867363] Cannot allocate resource for EISA slot 1
[   24.867368] Cannot allocate resource for EISA slot 3
[   24.867370] Cannot allocate resource for EISA slot 4
[   24.867371] Cannot allocate resource for EISA slot 5
[   24.867382] EISA: Detected 0 cards.
[   24.867454] TCP cubic registered
[   24.867464] NET: Registered protocol family 1
[   24.867484] Using IPI No-Shortcut mode
[   24.867621]   Magic number: 4:691:249
[   24.867660]   hash matches device ttyw5
[   24.867974] Freeing unused kernel memory: 364k freed
[   24.896832] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.047837] AppArmor: AppArmor initialized<5>audit(1208384061.660:2):  type=1505 info="AppArmor initialized" pid=1203
[   26.053753] fuse init (API version 7.8)
[   26.058206] Failure registering capabilities with primary security module.
[   26.082374] ACPI: Processor [CPU0] (supports 8 throttling states)
[   26.082397] ACPI: Processor [CPU1] (supports 8 throttling states)
[   26.084094] ACPI: Thermal Zone [THRM] (47 C)
[   26.601853] usbcore: registered new interface driver usbfs
[   26.601884] usbcore: registered new interface driver hub
[   26.601914] usbcore: registered new device driver usb
[   26.603015] USB Universal Host Controller Interface driver v3.0
[   26.603078] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   26.603090] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.603095] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.603230] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.603261] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[   26.603399] usb usb1: configuration #1 chosen from 1 choice
[   26.603432] hub 1-0:1.0: USB hub found
[   26.603440] hub 1-0:1.0: 2 ports detected
[   26.706328] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   26.706341] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.706346] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.706376] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.706407] uhci_hcd 0000:00:1d.1: irq 20, io base 0x000038c0
[   26.706531] usb usb2: configuration #1 chosen from 1 choice
[   26.706570] hub 2-0:1.0: USB hub found
[   26.706578] hub 2-0:1.0: 2 ports detected
[   26.729304] SCSI subsystem initialized
[   26.737953] libata version 2.21 loaded.
[   26.810258] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   26.810273] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.810278] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.810309] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.810339] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000038e0
[   26.810464] usb usb3: configuration #1 chosen from 1 choice
[   26.810500] hub 3-0:1.0: USB hub found
[   26.810508] hub 3-0:1.0: 2 ports detected
[   26.914164] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   26.914176] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   26.914181] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   26.914212] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   26.914242] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003c00
[   26.914362] usb usb4: configuration #1 chosen from 1 choice
[   26.914398] hub 4-0:1.0: USB hub found
[   26.914405] hub 4-0:1.0: 2 ports detected
[   27.018880] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   27.018897] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.018903] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.018944] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   27.018986] ehci_hcd 0000:00:1d.7: debug port 1
[   27.018995] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.019005] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xc8000000
[   27.022903] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.023052] usb usb5: configuration #1 chosen from 1 choice
[   27.023092] hub 5-0:1.0: USB hub found
[   27.023103] hub 5-0:1.0: 8 ports detected
[   27.126130] ACPI: PCI Interrupt 0000:0b:00.2[C] -> GSI 22 (level, low) -> IRQ 18
[   27.175950] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c8208000-c82087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   27.176107] ata_piix 0000:00:1f.1: version 2.11
[   27.176124] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[   27.176156] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.176355] scsi0 : ata_piix
[   27.176410] scsi1 : ata_piix
[   27.176436] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00013c40 irq 14
[   27.176439] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00013c48 irq 15
[   27.502196] ata1.00: ATA-6: FUJITSU MHU2100AT, 00000008, max UDMA/100
[   27.502201] ata1.00: 195371568 sectors, multi 16: LBA 
[   27.502207] ata1.01: ATAPI: HL-DT-ST DVD-RW GWA-4080N, 0C09, max MWDMA2
[   27.518187] ata1.00: configured for UDMA/100
[   27.689886] ata1.01: configured for MWDMA2
[   27.689917] ata2: port disabled. ignoring.
[   27.690050] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHU2100A 0000 PQ: 0 ANSI: 5
[   27.693778] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GWA-4080N 0C09 PQ: 0 ANSI: 5
[   27.694145] r8169 Gigabit Ethernet driver 2.2LK loaded
[   27.694174] ACPI: PCI Interrupt 0000:0b:02.0[A] -> GSI 20 (level, low) -> IRQ 22
[   27.694482] eth0: RTL8169sb/8110sb at 0xf8844400, 00:c0:9f:7d:bd:0a, XID 10000000 IRQ 22
[   27.703509] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   27.703530] sd 0:0:0:0: [sda] Write Protect is off
[   27.703535] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.703599] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.703678] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   27.703693] sd 0:0:0:0: [sda] Write Protect is off
[   27.703696] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.703720] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.703725]  sda: sda1 sda2 sda3
[   27.761603] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   27.775614] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.779207] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[   27.779213] Uniform CD-ROM driver Revision: 3.20
[   27.779505] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.779531] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   27.780701] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   27.945839] usb 4-1: configuration #1 chosen from 1 choice
[   27.958001] usbcore: registered new interface driver hiddev
[   27.970956] input: Microsoft Microsoft IntelliMouse &#65533; with IntelliEye as /class/input/input2
[   27.971061] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse &#65533; with IntelliEye] on usb-0000:00:1d.3-1
[   27.971079] usbcore: registered new interface driver usbhid
[   27.971083] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.039348] Attempting manual resume
[   28.039351] swsusp: Resume From Partition 8:2
[   28.039353] PM: Checking swsusp image.
[   28.039568] PM: Resume from disk failed.
[   28.049970] EXT3-fs: INFO: recovery required on readonly filesystem.
[   28.049975] EXT3-fs: write access will be enabled during recovery.
[   28.445387] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800285600076375]
[   31.816966] kjournald starting.  Commit interval 5 seconds
[   31.816984] EXT3-fs: sda3: orphan cleanup on readonly fs
[   31.816992] ext3_orphan_cleanup: deleting unreferenced inode 1025289
[   31.817030] EXT3-fs: sda3: 1 orphan inode deleted
[   31.817032] EXT3-fs: recovery complete.
[   31.843242] EXT3-fs: mounted filesystem with ordered data mode.
[   41.407425] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.423481] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.540634] iTCO_vendor_support: vendor-support=0
[   41.587903] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   41.587996] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x1060)
[   41.588049] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   41.686411] Linux agpgart interface v0.102 (c) Dave Jones
[   41.748957] intel_rng: FWH not detected
[   41.891779] Yenta: CardBus bridge found at 0000:0b:00.0 [103c:3082]
[   41.891800] Yenta: Enabling burst memory read transactions
[   41.891806] Yenta: Using CSCINT to route CSC interrupts to PCI
[   41.891809] Yenta: Routing CardBus interrupts to PCI
[   41.891815] Yenta TI: socket 0000:0b:00.0, mfunc 0x01a01b22, devctl 0x64
[   42.011938] input: PC Speaker as /class/input/input3
[   42.083254] ieee80211_crypt: registered algorithm 'NULL'
[   42.085887] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   42.085891] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   42.122817] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   42.122822] Socket status: 30000006
[   42.122827] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   42.122831] cs: IO port probe 0x5000-0x5fff: clean.
[   42.123159] pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[   42.123163] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x55ffffff
[   42.134679] PCI: Enabling device 0000:0b:00.3 (0000 -> 0002)
[   42.134690] ACPI: PCI Interrupt 0000:0b:00.3[A] -> GSI 16 (level, low) -> IRQ 16
[   42.162125] bcm43xx driver
[   42.162226] PCI: Enabling device 0000:0b:03.0 (0000 -> 0002)
[   42.162235] ACPI: PCI Interrupt 0000:0b:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   42.216388] sdhci: Secure Digital Host Controller Interface driver
[   42.216392] sdhci: Copyright(c) Pierre Ossman
[   42.216451] sdhci: SDHCI controller found at 0000:0b:00.4 [104c:8034] (rev 0)
[   42.216468] PCI: Enabling device 0000:0b:00.4 (0000 -> 0002)
[   42.216476] ACPI: PCI Interrupt 0000:0b:00.4[A] -> GSI 16 (level, low) -> IRQ 16
[   42.216563] mmc0: SDHCI at 0xc8209000 irq 16 DMA
[   42.220750] mmc1: SDHCI at 0xc8208c00 irq 16 DMA
[   42.220814] mmc2: SDHCI at 0xc8208800 irq 16 DMA
[   42.498370] cs: IO port probe 0x100-0x3af: clean.
[   42.499651] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   42.500190] cs: IO port probe 0x820-0x8ff: clean.
[   42.500624] cs: IO port probe 0xc00-0xcf7: clean.
[   42.501173] cs: IO port probe 0xa00-0xaff: clean.
[   42.695534] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 18
[   42.695556] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   42.774043] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x80b1, caps: 0xa04713/0x20040a
[   42.807292] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   43.013601] intel8x0_measure_ac97_clock: measured 54094 usecs
[   43.013605] intel8x0: clocking to 48000
[   44.171026] lp: driver loaded but no devices found
[   44.242955] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   44.625732] EXT3 FS on sda3, internal journal
[   45.857091] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   45.905498] ACPI: Battery Slot [BAT1] (battery absent)
[   45.988174] No dock devices found.
[   46.037828] input: Power Button (FF) as /class/input/input5
[   46.037855] ACPI: Power Button (FF) [PWRF]
[   46.037948] input: Lid Switch as /class/input/input6
[   46.037965] ACPI: Lid Switch [LID0]
[   46.038021] input: Power Button (CM) as /class/input/input7
[   46.038044] ACPI: Power Button (CM) [PWRB]
[   46.038097] input: Sleep Button (CM) as /class/input/input8
[   46.038119] ACPI: Sleep Button (CM) [SLPB]
[   46.161653] ACPI: AC Adapter [ACAD] (on-line)
[   47.211809] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 18
[   47.211831] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   47.412893] r8169: eth0: link up
[   47.567258] MC'97 0 converters and GPIO not ready (0x1)
[   49.391805] ppdev: user-space parallel port driver
[   49.534092] audit(1208398486.397:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4967 profile="/usr/sbin/cupsd"
[   49.621621] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   49.621627] apm: disabled - APM is not SMP safe.
[   50.178302] Failure registering capabilities with primary security module.
[   50.365952] Bluetooth: Core ver 2.11
[   50.366101] NET: Registered protocol family 31
[   50.366105] Bluetooth: HCI device and connection manager initialized
[   50.366109] Bluetooth: HCI socket layer initialized
[   50.375131] Bluetooth: L2CAP ver 2.8
[   50.375136] Bluetooth: L2CAP socket layer initialized
[   50.442078] Bluetooth: RFCOMM socket layer initialized
[   50.442212] Bluetooth: RFCOMM TTY layer initialized
[   50.442215] Bluetooth: RFCOMM ver 1.8
[   52.423623] [drm] Initialized drm 1.1.0 20060810
[   52.441453] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.441937] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   54.826807] NET: Registered protocol family 17
[   54.976163] [drm] Setting GART location based on new memory map
[   54.976547] [drm] Loading R300 Microcode
[   54.976593] [drm] writeback test succeeded in 1 usecs
[   68.670906] NET: Registered protocol family 10
[   68.671144] lo: Disabled Privacy Extensions
[   68.671401] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   79.382070] eth0: no IPv6 routers present
[ 1597.500198] bcm43xx: MAC suspend failed
[ 1863.470299] UDF-fs: Partition marked readonly; forcing readonly mount
[ 1863.522498] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DDO DVD', timestamp 2006/01/18 16:29 (1f10)
[ 3157.027186] bcm43xx: MAC suspend failed

---

### Post by drboz on 2008-06-13
The shutdowns are a result of your CPU over heating. One of the design flaws with the 9600 is that the fans are located on the bottom instead of the back, so if the unit is on a flat surface it simply blows the heat right back into the unit causing it to shutdown. This even happens on the docking station. Simply place a small object under the laptop to raise only the back of it about 1 inch. This will allow the air flow to exit from under the laptop. 
This should solve your problem.

DrBoz

---

### Post by MONODA on 2008-06-13
are you running with desktop effects enabled, if you are, disable them and see if that helps.

---

