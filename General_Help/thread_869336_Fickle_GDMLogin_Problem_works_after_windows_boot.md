---
title: "Fickle GDM/Login Problem: works after windows boot?"
date: 2008-07-24
forum: General Help
---

### Post by Viemexis on 2008-07-24
I'll try to be as clear as possible. Please read the whole thing before posting.

I've recently encountered an odd problem. I'm running a dual-boot machine with Ubuntu and XP. Whenever I boot into Ubuntu, after the USplash (loading screen) the login screen screen does not show up. Black screen instead. No cursor or anything, and keyboard commands such as CTRL+ALT+F1 or F2 do nothing. This first happened after I changed the GDM theme, and after searching on these forums I "fixed" it by reinstalling the GDM from the shell:

```
sudo aptitude purge gdm
sudo aptitude install gdm
reboot
``` 

And for the first time, it brought me to the login screen. But a similar problem remains, conditionally. It will boot into the Ubuntu login properly ONLY if I have booted to Windows on the previous boot. At first **I thought this was merely a coincidence, but I have confirmed this quirk repeatedly.** No matter how many times I try booting into Ubuntu it doesn't work, but if I boot into windows and then restart, GDM comes up without a fuss. It's not exactly a crippling problem, but it's annoying to boot twice just to use linux. Frankly I'm at a loss. I'm looking for suggestions on what might be causing it and how to fix it.

Thanks in advance.

---

### Post by Viemexis on 2008-07-25
I see this was viewed about ten times... but can no one help? (bump.)

---

### Post by beren.olvar on 2008-07-28
I am just guessing here, but could it be related to some missing hibernated session? do you use that feature, or have you in the past? 
may be just hibernating once and then rebooting could fix it.
If that doesnt work try looking at "dmesg" command.
the numbers in the left, between [] are a time meassure from the last boot, so should be easy to recognize the consecutive boots.
What seems to fail? may be you should post the result here.

again, your problem seems very odd, but hope we can solve it :P

cheers

---

### Post by Viemexis on 2008-08-19
I just now noticed this post because I thought all hope of getting a response was lost. Thanks. Hybernating and then rebooting didn't solve the problem. It did allow me to get into ubuntu and restore the session without booting into windows first, but the next regular shutdown and reboot yielded the same broken results. As you asked, here's the dmesg info.```
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000001f7f0000 - 000000001f7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7f3000 - 000000001f800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5ea0
[    0.000000] Entering add_active_range(0, 0, 129008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   129008
[    0.000000]   HighMem    129008 ->   129008
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   129008
[    0.000000] On node 0 totalpages: 129008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7D40 checksum 0
[    0.000000] ACPI: RSDP 000F7D40, 1F7F3000 (r2 IntelR)
[    0.000000] ACPI Warning (tbutils-0453): BIOS XSDT has NULL entry, using RSDT [20070126]
[    0.000000] ACPI: RSDT 1F7F3000, 002C (r1 IntelR AWRDACPI 30302E32 AWRD        1)
[    0.000000] ACPI: FACP 1F7F3040, 0084 (r2 IntelR AWRDACPI 30302E32 AWRD        1)
[    0.000000] ACPI: DSDT 1F7F3100, 3995 (r1 INTELR AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1F7F0000, 0040
[    0.000000] ACPI: APIC 1F7F6AC0, 0068 (r1 IntelR AWRDACPI 30302E32 AWRD        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:df400000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 128001
[    0.000000] Kernel command line: root=UUID=ede224ec-6743-4f31-980b-d5569d6c49d9 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2600.165 MHz processor.
[   24.508952] Console: colour VGA+ 80x25
[   24.508956] console [tty0] enabled
[   24.509489] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.509943] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.523228] Memory: 499076k/516032k available (2177k kernel code, 16308k reserved, 1006k data, 368k init, 0k highmem)
[   24.523239] virtual kernel memory layout:
[   24.523240]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.523242]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.523243]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   24.523244]     lowmem  : 0xc0000000 - 0xdf7f0000   ( 503 MB)
[   24.523245]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   24.523246]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   24.523247]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   24.523250] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.523293] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.603151] Calibrating delay using timer specific routine.. 5205.45 BogoMIPS (lpj=10410918)
[   24.603179] Security Framework initialized
[   24.603187] SELinux:  Disabled at boot.
[   24.603202] AppArmor: AppArmor initialized
[   24.603208] Failure registering capabilities with primary security module.
[   24.603217] Mount-cache hash table entries: 512
[   24.603365] Initializing cgroup subsys ns
[   24.603371] Initializing cgroup subsys cpuacct
[   24.603384] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   24.603398] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   24.603401] CPU: L2 cache: 512K
[   24.603404] CPU: Hyper-Threading is disabled
[   24.603406] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   24.603420] Compat vDSO mapped to ffffe000.
[   24.603436] Checking 'hlt' instruction... OK.
[   24.619544] SMP alternatives: switching to UP code
[   24.621278] Freeing SMP alternatives: 11k freed
[   24.621436] Early unpacking initramfs... done
[   24.963080] ACPI: Core revision 20070126
[   24.963143] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.966498] CPU0: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[   24.966543] Total of 1 processors activated (5205.45 BogoMIPS).
[   24.966687] ENABLING IO-APIC IRQs
[   24.966877] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.114154] Brought up 1 CPUs
[   25.114182] CPU0 attaching sched-domain:
[   25.114185]  domain 0: span 01
[   25.114188]   groups: 01
[   25.114418] net_namespace: 64 bytes
[   25.114430] Booting paravirtualized kernel on bare hardware
[   25.115013] Time: 14:33:17  Date: 08/19/08
[   25.115050] NET: Registered protocol family 16
[   25.115305] EISA bus registered
[   25.115331] ACPI: bus type pci registered
[   25.143494] PCI: PCI BIOS revision 2.10 entry at 0xfb970, last bus=1
[   25.143497] PCI: Using configuration type 1
[   25.143512] Setting up standard PCI resources
[   25.154027] ACPI: EC: Look up EC in DSDT
[   25.157990] ACPI: Interpreter enabled
[   25.157993] ACPI: (supports S0 S1 S3 S4 S5)
[   25.158050] ACPI: Using IOAPIC for interrupt routing
[   25.162230] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.162713] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   25.162714] * this clock source is slow. If you are sure your timer does not have
[   25.162716] * this bug, please use "acpi_pm_good" to disable the workaround
[   25.162764] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   25.162768] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   25.163285] PCI: Transparent bridge - 0000:00:1e.0
[   25.163309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.163458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   25.169766] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   25.169867] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   25.169965] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   25.170113] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   25.170210] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   25.170313] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   25.170410] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   25.170507] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   25.170702] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.170741] pnp: PnP ACPI init
[   25.170752] ACPI: bus type pnp registered
[   25.173498] pnp: PnP ACPI: found 14 devices
[   25.173502] ACPI: ACPI bus type pnp unregistered
[   25.173508] PnPBIOS: Disabled by ACPI PNP
[   25.173792] PCI: Using ACPI for IRQ routing
[   25.173796] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.193985] NET: Registered protocol family 8
[   25.193988] NET: Registered protocol family 20
[   25.194076] AppArmor: AppArmor Filesystem Enabled
[   25.197923] Time: tsc clocksource has been installed.
[   25.205953] system 00:01: ioport range 0xb78-0xb7b has been reserved
[   25.205956] system 00:01: ioport range 0xf78-0xf7b has been reserved
[   25.205959] system 00:01: ioport range 0xa78-0xa7b has been reserved
[   25.205962] system 00:01: ioport range 0xe78-0xe7b has been reserved
[   25.205964] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[   25.205967] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[   25.205970] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   25.205972] system 00:01: ioport range 0x294-0x297 has been reserved
[   25.205991] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[   25.236447] PCI: Bridge: 0000:00:1e.0
[   25.236451]   IO window: c000-cfff
[   25.236456]   MEM window: ec000000-edffffff
[   25.236461]   PREFETCH window: disabled.
[   25.236477] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.236492] NET: Registered protocol family 2
[   25.273884] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   25.274161] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   25.274285] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   25.274407] TCP: Hash tables configured (established 16384 bind 16384)
[   25.274411] TCP reno registered
[   25.285902] checking if image is initramfs... it is
[   25.736801] Switched to high resolution mode on CPU 0
[   25.959911] Freeing initrd memory: 7732k freed
[   25.960675] audit: initializing netlink socket (disabled)
[   25.960697] audit(1219156397.336:1): initialized
[   25.963158] VFS: Disk quotas dquot_6.5.1
[   25.963255] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.963432] io scheduler noop registered
[   25.963435] io scheduler anticipatory registered
[   25.963437] io scheduler deadline registered
[   25.963451] io scheduler cfq registered (default)
[   25.963469] Boot video device is 0000:00:02.0
[   25.963872] isapnp: Scanning for PnP cards...
[   26.317295] isapnp: No Plug & Play device found
[   26.353333] Real Time Clock Driver v1.12ac
[   26.353453] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.353584] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.354504] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.355534] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.355618] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.355752] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   26.358104] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.358109] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.359724] mice: PS/2 mouse device common for all mice
[   26.359870] EISA: Probing bus 0 at eisa.0
[   26.359910] EISA: Detected 0 cards.
[   26.359913] cpuidle: using governor ladder
[   26.359916] cpuidle: using governor menu
[   26.360036] NET: Registered protocol family 1
[   26.360075] Using IPI No-Shortcut mode
[   26.360115] registered taskstats version 1
[   26.360230]   Magic number: 4:952:586
[   26.360293]   hash matches device ptyc4
[   26.360372] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.360374] EDD information not available.
[   26.360949] Freeing unused kernel memory: 368k freed
[   26.387409] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.617278] fuse init (API version 7.9)
[   27.642561] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.012031] usbcore: registered new interface driver usbfs
[   28.012064] usbcore: registered new interface driver hub
[   28.023948] usbcore: registered new device driver usb
[   28.039904] USB Universal Host Controller Interface driver v3.0
[   28.040008] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.040024] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   28.040028] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   28.040421] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   28.040457] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   28.040647] usb usb1: configuration #1 chosen from 1 choice
[   28.040675] hub 1-0:1.0: USB hub found
[   28.040683] hub 1-0:1.0: 2 ports detected
[   28.143787] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   28.143805] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   28.143809] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   28.143838] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   28.143871] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   28.144025] usb usb2: configuration #1 chosen from 1 choice
[   28.144052] hub 2-0:1.0: USB hub found
[   28.144060] hub 2-0:1.0: 2 ports detected
[   28.247552] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.247570] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   28.247574] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   28.247610] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   28.247642] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   28.247778] usb usb3: configuration #1 chosen from 1 choice
[   28.247807] hub 3-0:1.0: USB hub found
[   28.247814] hub 3-0:1.0: 2 ports detected
[   28.352046] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   28.352073] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   28.352077] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   28.352112] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   28.356042] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   28.356054] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xee080000
[   28.360248] SCSI subsystem initialized
[   28.383162] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   28.395074] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.395225] usb usb4: configuration #1 chosen from 1 choice
[   28.395255] hub 4-0:1.0: USB hub found
[   28.395263] hub 4-0:1.0: 6 ports detected
[   28.431769] libata version 3.00 loaded.
[   28.446987] 8139too Fast Ethernet driver 0.9.28
[   28.499247] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 23 (level, low) -> IRQ 19
[   28.499959] eth0: RealTek RTL8139 at 0xc800, 00:0c:76:db:ea:8a, IRQ 19
[   28.499963] eth0:  Identified 8139 chip type 'RTL-8101'
[   28.502232] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   28.502302] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.502320] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   28.502668] ACPI: PCI Interrupt 0000:01:0d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   28.555450] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[ed022000-ed0227ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   28.578723] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   28.621658] Floppy drive(s): fd0 is 2.88M AMI BIOS
[   28.641043] FDC 0 is a post-1991 82077
[   28.661711] ata_piix 0000:00:1f.1: version 2.12
[   28.661742] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   28.661822] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.668046] scsi0 : ata_piix
[   28.682465] scsi1 : ata_piix
[   28.683203] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   28.683206] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   28.902496] ata1.00: ATA-6: ST3160021A, 3.06, max UDMA/100
[   28.902502] ata1.00: 312581808 sectors, multi 16: LBA48 
[   28.918425] ata1.00: configured for UDMA/100
[   29.401530] ata2.00: ATAPI: HP  DVD Writer 400, Bh04, max UDMA/33
[   29.401559] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-148A, B401, max UDMA/33
[   29.573073] ata2.00: configured for UDMA/33
[   29.652368] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   29.744448] ata2.01: configured for UDMA/33
[   29.744619] scsi 0:0:0:0: Direct-Access     ATA      ST3160021A       3.06 PQ: 0 ANSI: 5
[   29.747208] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 400c  Bh04 PQ: 0 ANSI: 5
[   29.747719] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B401 PQ: 0 ANSI: 5
[   29.761934] Driver 'sd' needs updating - please use bus_type methods
[   29.762054] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   29.762070] sd 0:0:0:0: [sda] Write Protect is off
[   29.762074] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.762097] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.762156] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   29.762169] sd 0:0:0:0: [sda] Write Protect is off
[   29.762173] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.762194] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.762199]  sda:<3>usb 1-1: device descriptor read/64, error -71
[   29.773006] Driver 'sr' needs updating - please use bus_type methods
[   29.775476]  sda1 sda2 sda3 sda4
[   29.782967] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.791955] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.791981] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   29.792026] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   29.801605] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   29.801613] Uniform CD-ROM driver Revision: 3.20
[   29.801687] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.803975] sr1: scsi3-mmc drive: 32x/48x cd/rw xa/form2 cdda tray
[   29.804019] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   29.923943] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00005f4b77]
[   29.995643] usb 1-1: device descriptor read/64, error -71
[   30.211202] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   30.250824] Attempting manual resume
[   30.250829] swsusp: Resume From Partition 8:2
[   30.250831] PM: Checking swsusp image.
[   30.251098] PM: Resume from disk failed.
[   30.269868] EXT3-fs: INFO: recovery required on readonly filesystem.
[   30.269874] EXT3-fs: write access will be enabled during recovery.
[   30.330928] usb 1-1: device descriptor read/64, error -71
[   30.554433] usb 1-1: device descriptor read/64, error -71
[   30.720904] kjournald starting.  Commit interval 5 seconds
[   30.720930] EXT3-fs: sda1: orphan cleanup on readonly fs
[   30.720940] ext3_orphan_cleanup: deleting unreferenced inode 881448
[   30.720974] EXT3-fs: sda1: 1 orphan inode deleted
[   30.720976] EXT3-fs: recovery complete.
[   30.735963] EXT3-fs: mounted filesystem with ordered data mode.
[   30.769983] usb 1-1: new full speed USB device using uhci_hcd and address 5
[   31.177099] usb 1-1: device not accepting address 5, error -71
[   31.288870] usb 1-1: new full speed USB device using uhci_hcd and address 6
[   31.695983] usb 1-1: device not accepting address 6, error -71
[   31.935471] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   32.106915] usb 2-1: configuration #1 chosen from 1 choice
[   32.362559] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   32.535926] usb 3-1: configuration #1 chosen from 1 choice
[   39.818709] Linux agpgart interface v0.102
[   39.934384] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.982408] agpgart: Detected an Intel 830M Chipset.
[   39.982542] agpgart: Detected 8060K stolen memory.
[   39.998513] agpgart: AGP aperture is 128M @ 0xe0000000
[   40.114063] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.169846] iTCO_vendor_support: vendor-support=0
[   40.222074] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   40.222192] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   40.222232] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   40.290035] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   40.454210] intel_rng: FWH not detected
[   40.617149] input: Power Button (FF) as /devices/virtual/input/input2
[   40.628841] ACPI: Power Button (FF) [PWRF]
[   40.628964] input: Power Button (CM) as /devices/virtual/input/input3
[   40.640817] ACPI: Power Button (CM) [PWRB]
[   41.040104] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   42.321487] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   42.321524] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   42.644491] intel8x0_measure_ac97_clock: measured 53533 usecs
[   42.644497] intel8x0: clocking to 48000
[   43.093221] usbcore: registered new interface driver hiddev
[   43.114525] input: SAITEK P220 as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input5
[   43.114600] input,hidraw0: USB HID v1.00 Joystick [SAITEK P220] on usb-0000:00:1d.1-1
[   43.114626] usbcore: registered new interface driver usbhid
[   43.114630] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   43.183387] usbcore: registered new interface driver libusual
[   43.243237] Initializing USB Mass Storage driver...
[   43.301061] scsi2 : SCSI emulation for USB Mass Storage devices
[   43.331061] usbcore: registered new interface driver usb-storage
[   43.331070] USB Mass Storage support registered.
[   43.331227] usb-storage: device found at 2
[   43.331230] usb-storage: waiting for device to settle before scanning
[   43.464744] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   43.493755] parport_pc 00:08: reported by Plug and Play ACPI
[   43.493855] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   45.809354] lp0: using parport0 (interrupt-driven).
[   45.898290] Adding 1052248k swap on /dev/sda2.  Priority:-1 extents:1 across:1052248k
[   46.474346] EXT3 FS on sda1, internal journal
[   46.619358] device-mapper: uevent: version 1.0.3
[   46.619401] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   48.321397] usb-storage: device scan complete
[   48.324380] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   48.327364] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   48.330349] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   48.333342] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   48.380527] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   48.380624] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   48.424251] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   48.424316] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   48.471125] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   48.471184] sd 2:0:0:2: Attached scsi generic sg5 type 0
[   48.515053] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   48.515113] sd 2:0:0:3: Attached scsi generic sg6 type 0
[   50.785907] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.237742] No dock devices found.
[   52.677518] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   52.677525] apm: overridden by ACPI.
[   52.839125] ppdev: user-space parallel port driver
[   53.092310] audit(1219170825.433:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5089 profile="/usr/sbin/cupsd" namespace="default"
[   53.291383] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   53.291391] vboxdrv: Successfully done.
[   53.291941] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   53.291945] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[   57.248985] eth0: link down
[   57.365942] Bluetooth: Core ver 2.11
[   57.366973] NET: Registered protocol family 31
[   57.366979] Bluetooth: HCI device and connection manager initialized
[   57.366984] Bluetooth: HCI socket layer initialized
[   57.396904] Bluetooth: L2CAP ver 2.9
[   57.396910] Bluetooth: L2CAP socket layer initialized
[   57.457289] Bluetooth: RFCOMM socket layer initialized
[   57.457618] Bluetooth: RFCOMM TTY layer initialized
[   57.457622] Bluetooth: RFCOMM ver 1.8
[   57.512649] usb 1-1: new full speed USB device using uhci_hcd and address 7
[   57.636321] usb 1-1: device descriptor read/64, error -71
[   57.863816] usb 1-1: device descriptor read/64, error -71
[   58.079352] usb 1-1: new full speed USB device using uhci_hcd and address 8
[   58.199095] usb 1-1: device descriptor read/64, error -71
[   58.422615] usb 1-1: device descriptor read/64, error -71
[   58.638172] usb 1-1: new full speed USB device using uhci_hcd and address 9
[   59.045284] usb 1-1: device not accepting address 9, error -71
[   59.157057] usb 1-1: new full speed USB device using uhci_hcd and address 10
[   59.564168] usb 1-1: device not accepting address 10, error -71
[   60.188220] [drm] Initialized drm 1.1.0 20060810
[   60.203365] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   60.203378] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   60.203485] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   61.125889] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   61.212389] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[   61.213210] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 21 (level, low) -> IRQ 21
[   61.216360] ndiswrapper: using IRQ 21
[   61.481043] wlan0: ethernet device 00:18:4d:70:3c:ee using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   61.481570] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   61.494785] usbcore: registered new interface driver ndiswrapper
[  228.597323] NET: Registered protocol family 10
[  228.598047] lo: Disabled Privacy Extensions
[  228.598824] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  228.599304] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.761520] NET: Registered protocol family 17
[  244.915233] UDF-fs: No VRS found
[  244.932399] ISO 9660 Extensions: Microsoft Joliet Level 1
[  244.941508] ISOFS: changing to secondary root
[  245.350968] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  262.485030] wlan0: no IPv6 routers present

```

Does that tell you anything useful?

---

