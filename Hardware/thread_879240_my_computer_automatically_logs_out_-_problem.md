---
title: "my computer automatically logs out - problem"
date: 2008-08-03
forum: Hardware
---

### Post by spandanj on 2008-08-03
I have ubuntu 8.04 installed on dell 6400. Until recently it was fine. But, recently, I have got a major problem. My computer automatically logs out on me when I am doing work. initially, it was occasionaly. lately, it has become a habit of ubuntu. it occurs few minutes or hours of uptime. So far I havent noticed any trigger that seems to cause it.

while its logging out, I get the prompt, saying:

starting samba daemon
.........
.......
........

I didnt get a chance to copy the whole message.

---

### Post by phidia on 2008-08-03
> My computer automatically logs out on me
Is it logging out or shuting down? I'm just trying to determine if it's a hardware issue like overheating. If you are sure it's not a hardware problem then checking (or even if it is) /var/log/messages -the most recent logs- may provide more detail.

---

### Post by spandanj on 2008-08-03
its logging out. 

I dont know what to read in var/log/messages. I am a noob.

I guess next time I will try to write down more what it reads on the prompt (black screen) before it logs out.

anything you think I should do to find out?

---

### Post by phidia on 2008-08-03
> dmesg (in a terminal) will often provide some system information.
You could send the dmesg output to a file by entering this:
> dmesg > /home/youruser/dmesg-output
**use your actual user name not "youruser" Still you are going to maybe have trouble retrieving that depending on how frequent these logouts are. 
You may need to use a livecd?

---

### Post by gligurski on 2008-10-25
I have similar problem. I'm a little new to Ubuntu, a month or so, and untill now it was just the beauty of th system that I got. But now it's making me very angry.
Right in the middle of work, X is shutting down, there is something that I cannot even read, and then it's back to the log screen again. Sometimes in a 5minutes, sometimes hours pass, sometimes 2-3 times ina a minute. Grrrrrr. ;-)
I have a prime suspect, Samba - I'm using it to get files from Win machine, because my HDD is only 10Gb, probably I did't configure something right, I dont know.
Here is the dump I got from the 

dmesg > /home/youruser/dmesg-output

command. Please Help Me Please!
Thank You !

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008 (Ubuntu 2.6.24-21.42-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff40000 (usable)
[    0.000000]  BIOS-e820: 000000001ff40000 - 000000001ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff50000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffbc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130880) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130880
[    0.000000]   HighMem    130880 ->   130880
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130880
[    0.000000] On node 0 totalpages: 130880
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125794 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAAD0 checksum 0
[    0.000000] ACPI: RSDP 000FAAD0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FF40000, 0030 (r1 A M I  OEMRSDT   6000501 MSFT       97)
[    0.000000] ACPI: FACP 1FF40200, 0081 (r2 A M I  OEMFACP   6000501 MSFT       97)
[    0.000000] ACPI: DSDT 1FF40370, 3B22 (r1  75i6E 75i6E140      140 INTL  2002026)
[    0.000000] ACPI: FACS 1FF50000, 0040
[    0.000000] ACPI: APIC 1FF40300, 006C (r1 A M I  OEMAPIC   6000501 MSFT       97)
[    0.000000] ACPI: OEMB 1FF50040, 003F (r1 A M I  OEMBIOS   6000501 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129858
[    0.000000] Kernel command line: root=UUID=4ec145a0-fb7b-4eb5-8f92-ff8f8f714d57 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2530.192 MHz processor.
[   24.518706] Console: colour VGA+ 80x25
[   24.518711] console [tty0] enabled
[   24.518993] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.519283] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.528684] Memory: 507012k/523520k available (2177k kernel code, 15952k reserved, 1006k data, 368k init, 0k highmem)
[   24.528692] virtual kernel memory layout:
[   24.528694]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.528695]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.528696]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   24.528697]     lowmem  : 0xc0000000 - 0xdff40000   ( 511 MB)
[   24.528698]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   24.528699]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
[   24.528701]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
[   24.528704] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.528747] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.608629] Calibrating delay using timer specific routine.. 5064.70 BogoMIPS (lpj=10129410)
[   24.608658] Security Framework initialized
[   24.608664] SELinux:  Disabled at boot.
[   24.608679] AppArmor: AppArmor initialized
[   24.608685] Failure registering capabilities with primary security module.
[   24.608695] Mount-cache hash table entries: 512
[   24.608839] Initializing cgroup subsys ns
[   24.608846] Initializing cgroup subsys cpuacct
[   24.608861] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000451d 00000000 00000000 00000000
[   24.608872] monitor/mwait feature present.
[   24.608874] using mwait in idle threads.
[   24.608881] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   24.608884] CPU: L2 cache: 256K
[   24.608887] CPU: Hyper-Threading is disabled
[   24.608890] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043180 0000451d 00000000 00000000 00000000
[   24.608902] Compat vDSO mapped to ffffe000.
[   24.608922] Checking 'hlt' instruction... OK.
[   24.625121] SMP alternatives: switching to UP code
[   24.627277] Freeing SMP alternatives: 11k freed
[   24.627447] Early unpacking initramfs... done
[   24.980676] ACPI: Core revision 20070126
[   24.980744] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.983093] CPU0: Intel(R) Celeron(R) CPU 2.53GHz stepping 01
[   24.983136] Total of 1 processors activated (5064.70 BogoMIPS).
[   24.983273] ENABLING IO-APIC IRQs
[   24.983458] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.127789] Brought up 1 CPUs
[   25.127816] CPU0 attaching sched-domain:
[   25.127821]  domain 0: span 01
[   25.127823]   groups: 01
[   25.128095] net_namespace: 64 bytes
[   25.128106] Booting paravirtualized kernel on bare hardware
[   25.128804] Time:  2:07:14  Date: 10/26/08
[   25.128843] NET: Registered protocol family 16
[   25.129212] EISA bus registered
[   25.129249] ACPI: bus type pci registered
[   25.129466] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   25.129470] PCI: Using configuration type 1
[   25.129482] Setting up standard PCI resources
[   25.142532] ACPI: EC: Look up EC in DSDT
[   25.146805] ACPI: Interpreter enabled
[   25.146811] ACPI: (supports S0 S1 S3 S4 S5)
[   25.146832] ACPI: Using IOAPIC for interrupt routing
[   25.155918] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.156527] Force enabled HPET at base address 0xfed00000
[   25.156535] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   25.156539] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   25.157164] PCI: Transparent bridge - 0000:00:1e.0
[   25.157206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.157357] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   25.165241] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   25.165371] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   25.165495] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   25.165619] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   25.165744] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.165869] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.165993] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   25.166117] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   25.166334] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.166391] pnp: PnP ACPI init
[   25.166406] ACPI: bus type pnp registered
[   25.170371] pnp: PnP ACPI: found 11 devices
[   25.170377] ACPI: ACPI bus type pnp unregistered
[   25.170382] PnPBIOS: Disabled by ACPI PNP
[   25.170812] PCI: Using ACPI for IRQ routing
[   25.170818] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.183700] NET: Registered protocol family 8
[   25.183703] NET: Registered protocol family 20
[   25.183877] hpet clockevent registered
[   25.183884] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   25.183890] hpet0: 3 64-bit timers, 14318180 Hz
[   25.184946] AppArmor: AppArmor Filesystem Enabled
[   25.187619] Time: tsc clocksource has been installed.
[   25.195697] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[   25.195702] system 00:05: ioport range 0x800-0x87f has been reserved
[   25.195705] system 00:05: ioport range 0x480-0x4bf has been reserved
[   25.195711] system 00:05: iomem range 0xfed20000-0xfed8ffff has been reserved
[   25.195714] system 00:05: iomem range 0xffb00000-0xffbfffff could not be reserved
[   25.195721] system 00:06: iomem range 0xfec00000-0xfec00fff has been reserved
[   25.195725] system 00:06: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.195733] system 00:09: ioport range 0x680-0x6ff has been reserved
[   25.195736] system 00:09: ioport range 0x295-0x296 has been reserved
[   25.195744] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   25.195747] system 00:0a: iomem range 0xc0000-0xdffff could not be reserved
[   25.195750] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   25.195753] system 00:0a: iomem range 0x100000-0x1fffffff could not be reserved
[   25.195756] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
[   25.226432] PCI: Bridge: 0000:00:01.0
[   25.226438]   IO window: a000-afff
[   25.226444]   MEM window: fe900000-fe9fffff
[   25.226449]   PREFETCH window: bff00000-dfefffff
[   25.226455] PCI: Bridge: 0000:00:1e.0
[   25.226459]   IO window: b000-bfff
[   25.226465]   MEM window: fea00000-feafffff
[   25.226469]   PREFETCH window: disabled.
[   25.226489] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.226508] NET: Registered protocol family 2
[   25.263585] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   25.263888] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   25.263981] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   25.264074] TCP: Hash tables configured (established 16384 bind 16384)
[   25.264078] TCP reno registered
[   25.275696] checking if image is initramfs... it is
[   25.686744] Switched to high resolution mode on CPU 0
[   25.960890] Freeing initrd memory: 7319k freed
[   25.961895] audit: initializing netlink socket (disabled)
[   25.961916] audit(1224986834.328:1): initialized
[   25.964956] VFS: Disk quotas dquot_6.5.1
[   25.965093] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.965317] io scheduler noop registered
[   25.965321] io scheduler anticipatory registered
[   25.965323] io scheduler deadline registered
[   25.965346] io scheduler cfq registered (default)
[   25.965438] Boot video device is 0000:01:00.0
[   25.965921] isapnp: Scanning for PnP cards...
[   26.317314] isapnp: No Plug & Play device found
[   26.411117] Real Time Clock Driver v1.12ac
[   26.411261] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.413735] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.413850] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.414019] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   26.416512] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.416518] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.421608] mice: PS/2 mouse device common for all mice
[   26.421821] EISA: Probing bus 0 at eisa.0
[   26.421862] EISA: Detected 0 cards.
[   26.421867] cpuidle: using governor ladder
[   26.421870] cpuidle: using governor menu
[   26.421976] NET: Registered protocol family 1
[   26.422013] Using IPI No-Shortcut mode
[   26.422060] registered taskstats version 1
[   26.422171]   Magic number: 12:252:107
[   26.422331] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.422333] EDD information not available.
[   26.422716] Freeing unused kernel memory: 368k freed
[   26.453367] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.732281] fuse init (API version 7.9)
[   27.762353] ACPI: Processor [CPU1] (supports 8 throttling states)
[   27.762376] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.762390] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.762403] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.576762] usbcore: registered new interface driver usbfs
[   28.576794] usbcore: registered new interface driver hub
[   28.585513] usbcore: registered new device driver usb
[   28.601497] USB Universal Host Controller Interface driver v3.0
[   28.601587] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.601603] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   28.601607] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   28.601969] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   28.602008] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[   28.602191] usb usb1: configuration #1 chosen from 1 choice
[   28.602229] hub 1-0:1.0: USB hub found
[   28.602238] hub 1-0:1.0: 2 ports detected
[   28.673600] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   28.705408] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   28.705425] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   28.705430] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   28.705470] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   28.705500] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e400
[   28.705651] usb usb2: configuration #1 chosen from 1 choice
[   28.705684] hub 2-0:1.0: USB hub found
[   28.705692] hub 2-0:1.0: 2 ports detected
[   28.706029] SCSI subsystem initialized
[   28.763284] libata version 3.00 loaded.
[   28.809243] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.809259] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   28.809264] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   28.809300] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   28.809331] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   28.809483] usb usb3: configuration #1 chosen from 1 choice
[   28.809522] hub 3-0:1.0: USB hub found
[   28.809530] hub 3-0:1.0: 2 ports detected
[   28.913034] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   28.913050] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   28.913055] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   28.913093] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   28.913122] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[   28.913274] usb usb4: configuration #1 chosen from 1 choice
[   28.913311] hub 4-0:1.0: USB hub found
[   28.913322] hub 4-0:1.0: 2 ports detected
[   29.017064] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   29.017085] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.017089] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.017143] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   29.021063] ehci_hcd 0000:00:1d.7: debug port 1
[   29.021071] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   29.021083] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebffc00
[   29.036681] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.036848] usb usb5: configuration #1 chosen from 1 choice
[   29.036883] hub 5-0:1.0: USB hub found
[   29.036893] hub 5-0:1.0: 8 ports detected
[   29.140771] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   29.140779] 8139cp 0000:02:01.0: Try the "8139too" driver instead.
[   29.140791] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   29.140794] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
[   29.143111] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   29.143171] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   29.143187] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   29.144927] 8139too Fast Ethernet driver 0.9.28
[   29.145018] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 20
[   29.145725] eth0: RealTek RTL8139 at 0xb800, 00:02:44:7e:0e:f5, IRQ 20
[   29.145729] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   29.145756] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 20
[   29.146473] eth1: RealTek RTL8139 at 0xb400, 00:13:8f:48:c8:8d, IRQ 20
[   29.146476] eth1:  Identified 8139 chip type 'RTL-8101'
[   29.152276] ata_piix 0000:00:1f.1: version 2.12
[   29.152302] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   29.152362] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   29.154723] scsi0 : ata_piix
[   29.155983] scsi1 : ata_piix
[   29.157713] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   29.157717] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   29.320764] ata1.00: ATA-5: Maxtor 91021U2, FA520S60, max UDMA/66
[   29.320770] ata1.00: 20010816 sectors, multi 16: LBA 
[   29.336646] ata1.00: configured for UDMA/66
[   29.655861] ata2.00: ATAPI: E-IDE CD-ROM Max 54X, Ver7.32K, max UDMA/33
[   29.819461] ata2.00: configured for UDMA/33
[   29.819641] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 91021U2   FA52 PQ: 0 ANSI: 5
[   29.820513] scsi 1:0:0:0: CD-ROM            E-IDE    CD-ROM Max 54X   7.32 PQ: 0 ANSI: 5
[   29.838978] Driver 'sd' needs updating - please use bus_type methods
[   29.839102] sd 0:0:0:0: [sda] 20010816 512-byte hardware sectors (10246 MB)
[   29.839122] sd 0:0:0:0: [sda] Write Protect is off
[   29.839126] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.839234] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.839324] sd 0:0:0:0: [sda] 20010816 512-byte hardware sectors (10246 MB)
[   29.839341] sd 0:0:0:0: [sda] Write Protect is off
[   29.839345] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.839371] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.839377]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   29.857914]  sda1 sda2 < sda5 sda6 sda7 >
[   29.899612] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.909720] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   29.909728] Uniform CD-ROM driver Revision: 3.20
[   29.909805] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.910903] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.910931] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   30.908592] Attempting manual resume
[   30.908598] swsusp: Resume From Partition 8:7
[   30.908601] PM: Checking swsusp image.
[   30.908863] PM: Resume from disk failed.
[   30.955682] kjournald starting.  Commit interval 5 seconds
[   30.955703] EXT3-fs: mounted filesystem with ordered data mode.
[   46.648586] intel_rng: FWH not detected
[   46.764402] Linux agpgart interface v0.102
[   46.964097] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.033388] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.095904] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   47.144673] agpgart: Detected an Intel 865 Chipset.
[   47.159659] agpgart: AGP aperture is 256M @ 0xe0000000
[   47.280523] iTCO_vendor_support: vendor-support=0
[   47.330481] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   47.330607] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   47.330650] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   47.399374] input: Power Button (FF) as /devices/virtual/input/input3
[   47.415213] ACPI: Power Button (FF) [PWRF]
[   47.415353] input: Power Button (CM) as /devices/virtual/input/input4
[   47.427158] ACPI: Power Button (CM) [PWRB]
[   48.982967] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   49.142731] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   49.211819] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   49.868324] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   49.868358] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   50.190134] intel8x0_measure_ac97_clock: measured 54332 usecs
[   50.190140] intel8x0: clocking to 48000
[   50.192609] NET: Registered protocol family 10
[   50.192928] lo: Disabled Privacy Extensions
[   51.829799] lp: driver loaded but no devices found
[   52.044032] Adding 787144k swap on /dev/sda7.  Priority:-1 extents:1 across:787144k
[   52.614975] EXT3 FS on sda5, internal journal
[   60.646538] ReiserFS: sda6: found reiserfs format "3.6" with standard journal
[   60.646556] ReiserFS: sda6: using ordered data mode
[   60.657053] ReiserFS: sda6: journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   60.658362] ReiserFS: sda6: checking transaction log (sda6)
[   60.700710] ReiserFS: sda6: Using r5 hash to sort names
[   60.942571] eth0: no IPv6 routers present
[   60.986492] eth1: no IPv6 routers present
[   62.134981] ip_tables: (C) 2000-2006 Netfilter Core Team
[   62.752533] No dock devices found.
[   64.589573] apm: BIOS not found.
[   64.803649] ppdev: user-space parallel port driver
[   65.151902] audit(1224976073.526:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5048 profile="/usr/sbin/cupsd" namespace="default"
[   68.590137] Bluetooth: Core ver 2.11
[   68.591046] NET: Registered protocol family 31
[   68.591053] Bluetooth: HCI device and connection manager initialized
[   68.591058] Bluetooth: HCI socket layer initialized
[   68.640667] Bluetooth: L2CAP ver 2.9
[   68.640674] Bluetooth: L2CAP socket layer initialized
[   68.747551] Bluetooth: RFCOMM socket layer initialized
[   68.747574] Bluetooth: RFCOMM TTY layer initialized
[   68.747577] Bluetooth: RFCOMM ver 1.8
[   71.048558] [drm] Initialized drm 1.1.0 20060810
[   71.076502] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   71.076767] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   72.953093] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   72.953517] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   72.953834] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   73.336514] [drm] Setting GART location based on new memory map
[   73.336530] [drm] Loading R200 Microcode
[   73.336585] [drm] writeback test succeeded in 1 usecs
[ 1013.463449] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 2474.988588] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 2474.989034] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 2474.989261] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 2475.341924] [drm] Setting GART location based on new memory map
[ 2475.341942] [drm] Loading R200 Microcode
[ 2475.341997] [drm] writeback test succeeded in 1 usecs
[ 2797.383279] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 2797.383648] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 2797.383942] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 2797.736528] [drm] Setting GART location based on new memory map
[ 2797.736545] [drm] Loading R200 Microcode
[ 2797.736600] [drm] writeback test succeeded in 1 usecs
[ 3230.989846] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 3230.990304] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 3230.990533] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 3231.343200] [drm] Setting GART location based on new memory map
[ 3231.343218] [drm] Loading R200 Microcode
[ 3231.343274] [drm] writeback test succeeded in 1 usecs
[ 3876.666847] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 3876.667273] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 3876.667495] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 3877.020128] [drm] Setting GART location based on new memory map
[ 3877.020145] [drm] Loading R200 Microcode
[ 3877.020199] [drm] writeback test succeeded in 1 usecs
[ 4435.129619] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 4435.130069] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 4435.130295] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 4435.482871] [drm] Setting GART location based on new memory map
[ 4435.482888] [drm] Loading R200 Microcode
[ 4435.482944] [drm] writeback test succeeded in 1 usecs
[ 4565.766719] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 4565.767089] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[ 4565.767383] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 4566.120052] [drm] Setting GART location based on new memory map
[ 4566.120068] [drm] Loading R200 Microcode
[ 4566.120123] [drm] writeback test succeeded in 1 usecs

---

### Post by cham93086 on 2008-10-25
I likewise am having this problem.  I also recently installed samba, it seems the problem started since then.  I have tried uninstalling it-- we'll see if it fixes it. the pertinent lines of my log file (right before the crash) look alot like yours:

(abridged)...

[   71.940039] Clocksource tsc unstable (delta = -271622414 ns)
[   73.744371] eth0: link up, 10Mbps, full-duplex, lpa 0x4061
[   75.063910] NET: Registered protocol family 17
[   75.414517] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   76.696500] [fglrx] GART Table is not in FRAME_BUFFER range 
[   76.696511] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   76.696514] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
[   76.872902] [fglrx] interrupt source 20008000 successfully enabled
[   76.872909] [fglrx] enable ID = 0x00000004
[   76.873344] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   78.501247] NET: Registered protocol family 10
[   78.502542] lo: Disabled Privacy Extensions
[   78.503376] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.997368] eth0: no IPv6 routers present
[  180.280776] gvfs-fuse-daemo[6019] general protection rip:7f18b9948423 rsp:7fffc35733c0 error:0
[  180.563663] [fglrx] interrupt source 20008000 successfully disabled!
[  180.563671] [fglrx] enable ID = 0x00000000
[  180.563674] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
[  183.221000] [fglrx] PCIe has already been initialized. Reinitializing ...
[  183.227511] [fglrx] GART Table is not in FRAME_BUFFER range 
[  183.227522] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  183.227525] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
[  183.330736] [fglrx] interrupt source 20008000 successfully enabled
[  183.330743] [fglrx] enable ID = 0x00000004
[  183.331072] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[ 2452.786125] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 2452.792526] [fglrx] GART Table is not in FRAME_BUFFER range 
[ 2452.792537] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[ 2452.792540] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
[ 2452.899416] [fglrx] interrupt source 20008000 successfully enabled
[ 2452.899424] [fglrx] enable ID = 0x00000004
[ 2452.899725] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000

---

### Post by gligurski on 2008-10-26
Probably we'll just have to wait few more days for the new Ubuntu, but untill then, I've been fondling with the smb.conf file and It's been a day now without the problem. I don't know what I did but it could happen again.

---

### Post by zerubbabel on 2008-11-23
I wonder whether you found a solution for this problem. I'm experiencing apparently random logouts on Intrepid. I did not have this problem on Hardy. It only started after I did a clean install of 8.10. There doesn't seem to be any connection with what I'm doing at the time. Sometimes it happens when I'm away from my desk and the system is idle. Sometimes it happens in the middle of what I'm doing, but with no obvious pattern. The screen goes black, no message is visible, and the login screen appears. I'm guessing it's an X-windows problem. If I wanted to try a re-install of X, how would I go about doing that?

---

### Post by spandanj on 2008-11-23
It doesn't happen to me anymore. I don't know why.

However, 8.10 really sucks, atleast on my computer. In 8.10, my computer froze within 5 minutes after login/boot every time. So, I am back to 8.04. Log out problem hasn't occurred.

---

### Post by Tr!p on 2008-11-23
I get this problem as well as screen freezing at the login window. 8.10 Intrepid? 8.04 might be a temp fix.

---

### Post by spandanj on 2008-11-23
if by 8.04 as temp solution you mean a temporary solution till next LTS release, I will take it. But, I can't believe a system breaking by moving forward, ie. installing a new version! If any changes, I expect newer system versions be better....

Stuff not working in a new version of ubuntu, which worked in the old version......is just WRONG. especially stuff as bad as ---- desktop freezing!!!...whatever the cause is.

atleast 8.04 works....

[I don't know if I am correct here: Ubuntu developers should learn to focus on user experience first and THEN on updating their softwares to new versions in ubuntu, eg. kernels, drivers---Not until it works perfectly with no glitch...Please do not test out new stuff on a RELEASE! that's what alpha/beta testing is for. Bringing a feature to an operating system FIRST, or as soon as possible should not take priority over user-friendliness and stability<--I thought that was Ubuntu's motto, but I am proven wrong with 8.10. If we should learn anything from leopard is stability <--it should just work whatever IS there to work with instead of making sure we have more features to work with.]

---

### Post by Palanthas on 2008-11-23
Easy there friend. Doesn't help to scream at folks.

Ok, so you know this is a new version, new versions are generally better but sometimes have bugs that haven't been completely worked out. Old programs that worked in 8.04 (or earlier) don't work in 8.10, and so on.

I installed 8.10 recently and haven't had an issue yet. (though I am moving over from windows and may not do as much on here yet as the rest of you) Not to say that it worked for me thus it should work for everyone else, but its as though you say this is common and it crashes on everyone.

If I were experiencing these problems here is what I would check.
Have you made sure you have compatible hardware for the new version? Has this issue been present since installation? If not then, what may have changed since? Personally changed settings or new software/hardware since install that could cause these issues? Or new updates that may have caused the problems. 

Just a few thoughts. I'll admit that I am new to Ubuntu and have only dabbled a bit in other flavours of linux so I may have this all wrong, if so I apologise for my mistake. You just have to step back sometimes when there is an issue and ask "is this my fault or theirs?" before going out and ranting.

---

### Post by spandanj on 2008-11-23
> **Palanthas said:**
> new versions are generally better but sometimes have bugs that haven't been completely worked out. Old programs that worked in 8.04 (or earlier) don't work in 8.10, and so on.
**First**, if you think that its ok for new versions to have some "unworked-out" bugs, and that certain old programs not working, how do you believe "new versions are generally better?"

**Secondly**, I (strongly) believe that new versions should NOT have unworked out bugs b/c you release new versions to solve problems, not create. Not only should new verions solve bugs of old version, It should also not give rise to new bugs. If your argument is that new bugs are meant to happen with new versions, then I say just take the time to solve (thoroughly) before making the new version a release. It is really (believe me) frustrating when every 6 months you get excited and look forward to new features, but are disappointed every time due to some new bugs...You will see; you're still new to ubuntu like you said.

> **Palanthas said:**
>  Not to say that it worked for me thus it should work for everyone else, but its as though you say this is common and it crashes on everyone.
It is common I think because this problem is a registered bug on launchpad. As to how common, I don't know. I would think it affects everyone with iwl3945 wireless card-watever that is.

> **Palanthas said:**
> If I were experiencing these problems here is what I would check. Have you made sure you have compatible hardware for the new version? Has this issue been present since installation? If not then, what may have changed since? Personally changed settings or new software/hardware since install that could cause these issues? Or new updates that may have caused the problems. 
This problem began with fresh install, no changes made. It disappeared when I turned off the wireless. THus, I know what's most likely causing it. If you suggest that the hardware might be incompatible, you are wrong because it was supported/worked in 8.04, no problems at all.  you might be right if they decided to take away support which they previously offered. and, I mentioned all this in my first post.

 > **Palanthas said:**
> You just have to step back sometimes when there is an issue and ask "is this my fault or theirs?" before going out and ranting.
...please stop lecturing. if you have concrete solutions to offer, do that instead. Unlike you I don't see it as 'my fault' or 'their fault'. I think its too simplistic to think of it that way. However, I do agree with you to give details about the user's actions prior to the problem if any are suspected. 

And finally, I have every right to rant if a new OS version, for which I spent useful time installing just "freezes" on me! I would be less agitated if the problem was a minor issue; I have had those of my share and have solved them, too. But, if a new system simply 'breaks' my computer,it's unacceptable.

IN the End, your post was more of a rant than a solution. You neither asked me for any pertinent information regarding the problem, nor did you offer any substantial help or solution. I hope you agree.

---

### Post by Palanthas on 2008-11-23
> **spandanj said:**
> I have ubuntu 8.04 installed on dell 6400. Until recently it was fine. But, recently, I have got a major problem. My computer automatically logs out on me when I am doing work. initially, it was occasionaly. lately, it has become a habit of ubuntu. it occurs few minutes or hours of uptime. So far I havent noticed any trigger that seems to cause it.

Interesting.... nothing in this post here says anything about 8.10 being freshly installed... says nothing about the fact that the wireless card causing issue. Also, you say at the end "So far I havent noticed any trigger that seems to cause it."

I did not mean to offend you. But you did say rather randomly > **spandanj said:**
> However, 8.10 really sucks, atleast on my computer. In 8.10, my computer froze within 5 minutes after login/boot every time. So, I am back to 8.04. Log out problem hasn't occurred.
Sounded to me like its not working for you so it must be their fault. Although I didn't mean that its ok for a new version of something to have bugs. I meant that sometimes new things have bugs... its not ok, but it happens. I wish it wasn't so either. Usually new things are better, I didn't say new things are ALWAYS better.

...please stop complaining. If you think 8.10 sucks, fine. But tell us why. (more then "it keeps freezing up...") Complaining that it sucks and that you are going to another version without telling us why doesn't make much sense. I went back and read everything on this thread. and this > **spandanj said:**
> However, 8.10 really sucks, atleast on my computer. In 8.10, my computer froze within 5 minutes after login/boot every time. So, I am back to 8.04. Log out problem hasn't occurred. is the only point you talk about 8.10

In the end I do agree with you that my post (and I guess this one too really) was more of a rant then help. I see that now. I offer my apologies, wish for your forgiveness, and hope to move on with no hurt feelings.

---

### Post by spandanj on 2008-11-23
> **Palanthas said:**
> If you think 8.10 sucks, fine. But tell us why

:mad:**OMG! You have got to be a very non-intelligent person. The name of the thread tells you why I think 8.10 sucks!**:mad:It freezes everytime! everytime--within 5 minutes of boot. Isn't that reason enough to say it sucks?????? 

How worse does it have to be than freezing every single time to claim that is sucks????? When would YOU say that it sucks?

Finally, [-o<please stop posting on this thread with your useless bickering without offering any real help, so that I can stop bickering about how your posts are useless and that you should stop posting. also, it would end stop my headache. 

I forgive you if you don't post anymore.[-X although, I will allow one last one to let you say that I am right all along, and that you are sorry. :)

---

### Post by spandanj on 2008-11-23
correction: 

I am wrong. name of the thread doesn't say that 8.10 kept freezing up. I created a seperate thread for that. and that is what I am referring to.

---

### Post by Palanthas on 2008-11-24
Sorry, did not know about the other thread, thus this one made little sense to me. I shall refrain from posting here (unless of course I find truely useful information, which currantly I doubt I will, but you never know)

With the addition of the other thread, you were right. and again, I am sorry.

*has also sent private message of appologie*

---

