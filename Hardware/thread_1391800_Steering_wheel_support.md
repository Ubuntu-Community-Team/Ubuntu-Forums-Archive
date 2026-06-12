---
title: "Steering wheel support?"
date: 2010-01-27
forum: Hardware
---

### Post by Omri16 on 2010-01-27
Hello all,

I just bought a new digital steering wheel for racing games. The manufacturer is not so well-known (it's called "andGame"). I took a photo of the wheel so that you may try to recognize it:
[http://img69.imageshack.us/img69/6856/steeringwheelb.jpg]("http://img69.imageshack.us/img69/6856/steeringwheelb.jpg")
It works well with Windows and with Sony PlayStation, but when I plug it in to my Ubuntu 8.04, nothing happens (it does get electricity though - the lights are on; it uses standard USB connection). I tried it on TORCS and ManiaDrive, but the system just doesn't seem to recognize it. I don't know how to check if the system "knows" I plugged anything in.
I don't really need the sophisticated force-feedback stuff, just the basics - steering right/left, using the gas and brakes pedals (connected to the wheel), that's about it.
Can you please help me?

Thanks!!

---

### Post by Omri16 on 2010-01-28
Anyone please...?

Here's dmesg's output:

```
[    0.000000] Kernel command line: root=UUID=51200e1a-20a1-40ee-987c-fedd9b01e3aa ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   16.083290] Marking TSC unstable due to TSCs unsynchronized
[   16.083292] time.c: Detected 2000.186 MHz processor.
[   16.086659] Console: colour VGA+ 80x25
[   16.086662] console [tty0] enabled
[   16.086679] Checking aperture...
[   16.086681] CPU 0: aperture @ 380000000 size 32 MB
[   16.086683] Aperture too small (32 MB)
[   16.092850] No AGP bridge found
[   16.129161] Memory: 3023876k/3079488k available (2494k kernel code, 55220k reserved, 1318k data, 320k init)
[   16.129204] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.129222] Calibrating delay loop (skipped), using tsc calculated value.. 4000.37 BogoMIPS (lpj=8000744)
[   16.129255] Security Framework initialized
[   16.129260] SELinux:  Disabled at boot.
[   16.129273] AppArmor: AppArmor initialized
[   16.129276] Failure registering capabilities with primary security module.
[   16.129588] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   16.132919] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   16.134501] Mount-cache hash table entries: 256
[   16.134633] Initializing cgroup subsys ns
[   16.134637] Initializing cgroup subsys cpuacct
[   16.134649] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.134651] CPU: L2 Cache: 512K (64 bytes/line)
[   16.134653] CPU 0/0 -> Node 0
[   16.134655] CPU: Physical Processor ID: 0
[   16.134656] CPU: Processor Core ID: 0
[   16.134680] SMP alternatives: switching to UP code
[   16.135260] Early unpacking initramfs... done
[   16.476234] ACPI: Core revision 20070126
[   16.476301] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.925689] Using local APIC timer interrupts.
[   16.975595] APIC timer calibration result 12501160
[   16.975596] Detected 12.501 MHz APIC timer.
[   16.975696] SMP alternatives: switching to SMP code
[   16.976175] Booting processor 1/2 APIC 0x1
[   16.985194] Initializing CPU#1
[   17.062394] Calibrating delay using timer specific routine.. 4000.38 BogoMIPS (lpj=8000763)
[   17.062400] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.062402] CPU: L2 Cache: 512K (64 bytes/line)
[   17.062405] CPU 1/1 -> Node 0
[   17.062406] CPU: Physical Processor ID: 0
[   17.062407] CPU: Processor Core ID: 1
[   17.062509] AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[   17.062523] AMD C1E detected late. Force timer broadcast.
[   17.063651] Brought up 2 CPUs
[   17.063760] CPU0 attaching sched-domain:
[   17.063763]  domain 0: span 03
[   17.063765]   groups: 01 02
[   17.063768]   domain 1: span 03
[   17.063769]    groups: 03
[   17.063771] CPU1 attaching sched-domain:
[   17.063773]  domain 0: span 03
[   17.063774]   groups: 02 01
[   17.063777]   domain 1: span 03
[   17.063778]    groups: 03
[   17.064010] net_namespace: 120 bytes
[   17.064419] Time: 16:50:13  Date: 01/28/10
[   17.064453] NET: Registered protocol family 16
[   17.064637] ACPI: bus type pci registered
[   17.064707] PCI: Using configuration type 1
[   17.065816] ACPI: EC: Look up EC in DSDT
[   17.067681] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   17.068241] ACPI: Interpreter enabled
[   17.068244] ACPI: (supports S0 S3 S4 S5)
[   17.068258] ACPI: Using IOAPIC for interrupt routing
[   17.067763] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.077864] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   17.077868] ACPI: EC: driver started in interrupt mode
[   17.077932] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.078827] PCI: Transparent bridge - 0000:00:08.0
[   17.079005] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.079094] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   17.079114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   17.079150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   17.109648] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[   17.109839] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[   17.110026] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[   17.110211] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[   17.110397] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   17.110582] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   17.110769] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   17.110955] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   17.111141] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[   17.111326] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[   17.111516] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[   17.111702] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[   17.111889] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[   17.112079] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[   17.112268] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[   17.112456] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[   17.112645] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[   17.112833] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[   17.113022] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[   17.113156] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.113185] pnp: PnP ACPI init
[   17.113193] ACPI: bus type pnp registered
[   17.116666] pnp: PnP ACPI: found 12 devices
[   17.116668] ACPI: ACPI bus type pnp unregistered
[   17.116942] PCI: Using ACPI for IRQ routing
[   17.116945] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.126427] NET: Registered protocol family 8
[   17.126429] NET: Registered protocol family 20
[   17.126526] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   17.126529] hpet0: 3 32-bit timers, 25000000 Hz
[   17.127584] AppArmor: AppArmor Filesystem Enabled
[   17.131455] Time: hpet clocksource has been installed.
[   17.131459] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   17.131461] Could not switch to high resolution mode on CPU 0
[   17.134405] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   17.134408] Could not switch to high resolution mode on CPU 1
[   17.142420] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.142425] system 00:03: ioport range 0x1000-0x107f has been reserved
[   17.142427] system 00:03: ioport range 0x1080-0x10ff has been reserved
[   17.142430] system 00:03: ioport range 0x1400-0x147f has been reserved
[   17.142432] system 00:03: ioport range 0x1480-0x14ff has been reserved
[   17.142434] system 00:03: ioport range 0x1800-0x187f has been reserved
[   17.142437] system 00:03: ioport range 0x1880-0x18ff has been reserved
[   17.142442] system 00:04: ioport range 0x360-0x361 has been reserved
[   17.142444] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   17.142453] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[   17.142455] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.142458] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[   17.142460] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[   17.142463] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   17.142465] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[   17.142890] PCI: Bridge: 0000:00:08.0
[   17.142892]   IO window: disabled.
[   17.142894]   MEM window: f6100000-f61fffff
[   17.142897]   PREFETCH window: disabled.
[   17.142899] PCI: Bridge: 0000:00:0c.0
[   17.142901]   IO window: 4000-4fff
[   17.142903]   MEM window: f2000000-f3ffffff
[   17.142905]   PREFETCH window: f0000000-f1ffffff
[   17.142907] PCI: Bridge: 0000:00:0d.0
[   17.142908]   IO window: disabled.
[   17.142911]   MEM window: f6000000-f60fffff
[   17.142912]   PREFETCH window: disabled.
[   17.142922] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.142930] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.142936] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.142998] NET: Registered protocol family 2
[   17.186451] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.187940] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   17.194453] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   17.195228] TCP: Hash tables configured (established 524288 bind 65536)
[   17.195231] TCP reno registered
[   17.210403] checking if image is initramfs... it is
[   17.906101] Freeing initrd memory: 7982k freed
[   17.911826] Simple Boot Flag at 0x36 set to 0x1
[   17.913672] audit: initializing netlink socket (disabled)
[   17.913683] audit(1264697413.388:1): initialized
[   17.915627] VFS: Disk quotas dquot_6.5.1
[   17.915706] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   17.915828] io scheduler noop registered
[   17.915830] io scheduler anticipatory registered
[   17.915832] io scheduler deadline registered
[   17.915931] io scheduler cfq registered (default)
[   17.915960] pci 0000:00:00.0: Enabling HT MSI Mapping
[   17.917448] pci 0000:00:07.0: Enabling HT MSI Mapping
[   17.917465] pci 0000:00:08.0: Enabling HT MSI Mapping
[   17.917479] pci 0000:00:09.0: Enabling HT MSI Mapping
[   17.917494] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   17.917507] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   17.917521] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   17.917534] Boot video device is 0000:00:12.0
[   17.917712] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.917733] assign_interrupt_mode Found MSI capability
[   17.917752] Allocate Port Service[0000:00:0c.0:pcie00]
[   17.917815] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.917836] assign_interrupt_mode Found MSI capability
[   17.917851] Allocate Port Service[0000:00:0d.0:pcie00]
[   17.945269] Real Time Clock Driver v1.12ac
[   17.945461] hpet_resources: 0xfed00000 is busy
[   17.945494] Linux agpgart interface v0.102
[   17.945497] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.947156] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.947226] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.947322] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   17.974910] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.974914] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.985882] mice: PS/2 mouse device common for all mice
[   17.985918] cpuidle: using governor ladder
[   17.985920] cpuidle: using governor menu
[   17.986064] NET: Registered protocol family 1
[   17.986167] registered taskstats version 1
[   17.986306]   Magic number: 10:557:844
[   17.986391]   hash matches device ptyrd
[   17.986439] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   17.986442] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.986444] EDD information not available.
[   17.986451] Freeing unused kernel memory: 320k freed
[   17.987015] Write protecting the kernel read-only data: 1036k
[   18.021806] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.211710] fuse init (API version 7.9)
[   19.229605] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.229613] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.228800] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   19.228807] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.231806] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   19.568824] SCSI subsystem initialized
[   19.567982] usbcore: registered new interface driver usbfs
[   19.568009] usbcore: registered new interface driver hub
[   19.575589] libata version 3.00 loaded.
[   19.574677] usbcore: registered new device driver usb
[   19.577054] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   19.577408] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   19.577419] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 23
[   19.577447] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   19.577454] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[   19.577428] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.577808] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[   19.577819] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 18 (level, low) -> IRQ 18
[   19.577992] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   19.577998] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   19.578248] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   19.578270] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[   19.639793] usb usb1: configuration #1 chosen from 1 choice
[   19.639824] hub 1-0:1.0: USB hub found
[   19.639833] hub 1-0:1.0: 7 ports detected
[   19.745898] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[   19.745905] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z018] -> GSI 18 (level, low) -> IRQ 18
[   19.746112] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   19.746119] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   19.746184] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[   19.746199] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[   19.807450] usb usb2: configuration #1 chosen from 1 choice
[   19.807475] hub 2-0:1.0: USB hub found
[   19.807485] hub 2-0:1.0: 2 ports detected
[   19.909684] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   19.909697] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 22
[   19.909894] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   19.909901] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   19.909957] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[   19.909987] ehci_hcd 0000:00:02.1: debug port 1
[   19.909991] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   19.910003] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[   20.049872] usb 1-4: new low speed USB device using ohci_hcd and address 2
[   20.064846] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.064972] usb usb3: configuration #1 chosen from 1 choice
[   20.064995] hub 3-0:1.0: USB hub found
[   20.065002] hub 3-0:1.0: 7 ports detected
[   20.169114] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[   20.169120] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z019] -> GSI 22 (level, low) -> IRQ 22
[   20.169312] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   20.169319] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   20.169377] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[   20.169407] ehci_hcd 0000:00:04.1: debug port 1
[   20.169411] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   20.169418] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[   20.180639] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.180761] usb usb4: configuration #1 chosen from 1 choice
[   20.180784] hub 4-0:1.0: USB hub found
[   20.180791] hub 4-0:1.0: 2 ports detected
[   20.289518] pata_amd 0000:00:06.0: version 0.3.10
[   20.289571] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   20.290521] scsi0 : pata_amd
[   20.290902] scsi1 : pata_amd
[   20.291211] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   20.291214] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   20.624971] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632N, 0503, max MWDMA2
[   20.736455] usb 1-4: new low speed USB device using ohci_hcd and address 3
[   20.812507] ata1.00: configured for MWDMA2
[   20.812541] ata2: port disabled. ignoring.
[   20.815341] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632N  0503 PQ: 0 ANSI: 5
[   20.816344] ahci 0000:00:09.0: version 3.0
[   20.816358] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 23
[   20.950272] usb 1-4: configuration #1 chosen from 1 choice
[   21.818244] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   21.818249] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   21.818254] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   21.818549] scsi2 : ahci
[   21.818621] scsi3 : ahci
[   21.818662] scsi4 : ahci
[   21.818704] scsi5 : ahci
[   21.818774] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 509
[   21.818777] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 509
[   21.818779] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 509
[   21.818782] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 509
[   22.456925] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.457009] ata3.00: ATA-7: ST9160821AS, 3.BHE, max UDMA/100
[   22.457013] ata3.00: 312581808 sectors, multi 16: LBA48 
[   22.457984] ata3.00: configured for UDMA/100
[   22.776276] ata4: SATA link down (SStatus 0 SControl 300)
[   23.095622] ata5: SATA link down (SStatus 0 SControl 300)
[   23.414961] ata6: SATA link down (SStatus 0 SControl 300)
[   23.415076] scsi 2:0:0:0: Direct-Access     ATA      ST9160821AS      3.BH PQ: 0 ANSI: 5
[   23.415324] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   23.415677] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   23.415687] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 20
[   23.415693] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   23.422653] Driver 'sd' needs updating - please use bus_type methods
[   23.422757] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   23.422769] sd 2:0:0:0: [sda] Write Protect is off
[   23.422772] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.422788] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.422833] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   23.422841] sd 2:0:0:0: [sda] Write Protect is off
[   23.422843] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.422857] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.422861]  sda: sda1 sda2 sda3 sda4
[   23.442556] sd 2:0:0:0: [sda] Attached SCSI disk
[   23.447197] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   23.447219] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   23.934375] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1e:68:32:6d:f0
[   23.934380] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   23.934552] PCI: Enabling device 0000:02:05.0 (0100 -> 0102)
[   23.934886] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   23.934897] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   23.986949] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.992772] usbcore: registered new interface driver hiddev
[   24.000437] input: HID 1241:1111 as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input2
[   24.009931] Driver 'sr' needs updating - please use bus_type methods
[   24.028470] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.028476] Uniform CD-ROM driver Revision: 3.20
[   24.028529] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.031351] input,hidraw0: USB HID v1.00 Mouse [HID 1241:1111] on usb-0000:00:02.0-4
[   24.031370] usbcore: registered new interface driver usbhid
[   24.031373] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.157467] kjournald starting.  Commit interval 5 seconds
[   24.157478] EXT3-fs: mounted filesystem with ordered data mode.
[   25.286823] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00caebc900]
[   34.093341] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   34.505896] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.541004] input: Power Button (FF) as /devices/virtual/input/input4
[   34.596745] ACPI: Power Button (FF) [PWRF]
[   34.596805] input: Sleep Button (CM) as /devices/virtual/input/input5
[   34.612581] shpchp: Unknown symbol acpi_run_oshp
[   34.612680] shpchp: Unknown symbol pci_hp_change_slot_info
[   34.612753] shpchp: Unknown symbol pci_hp_register
[   34.612942] shpchp: Unknown symbol pci_hp_deregister
[   34.613086] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   34.643573] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.669984] ACPI: Sleep Button (CM) [SLPB]
[   34.670052] input: Lid Switch as /devices/virtual/input/input6
[   34.679126] nvidia: module license 'NVIDIA' taints kernel.
[   34.809253] ACPI: Lid Switch [LID]
[   34.809343] input: Power Button (CM) as /devices/virtual/input/input7
[   34.995840] ACPI: Power Button (CM) [PWRB]
[   35.050661] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   35.050674] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 16 (level, low) -> IRQ 16
[   35.050682] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   35.050855] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   35.275138] ACPI: Battery Slot [BAT0] (battery present)
[   35.520874] ricoh-mmc: Ricoh MMC Controller disabling driver
[   35.520879] ricoh-mmc: Copyright(c) Philip Langdale
[   35.520931] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   35.520940] ricoh-mmc: Controller is now disabled.
[   35.540492] ACPI: AC Adapter [ACAD] (on-line)
[   35.568947] ACPI: WMI-Acer: Mapper loaded
[   35.594256] sdhci: Secure Digital Host Controller Interface driver
[   35.594261] sdhci: Copyright(c) Pierre Ossman
[   35.594317] sdhci: SDHCI controller found at 0000:02:05.1 [1180:0822] (rev 22)
[   35.594669] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   35.594680] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNK2] -> GSI 7 (level, low) -> IRQ 7
[   35.594866] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   35.594962] mmc0: SDHCI at 0xf6100800 irq 7 DMA
[   35.655724] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   35.706688] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   35.951732] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   35.951745] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   35.952005] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   36.061599] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   36.143227] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   37.510369] lp: driver loaded but no devices found
[   37.571006] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   37.690621] wlan: 0.9.4
[   37.728458] ath_pci: 0.9.4
[   37.728907] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   37.728918] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   37.728928] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   37.756735] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   37.756756] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   38.352598] EXT3 FS on sda3, internal journal
[   38.494021] device-mapper: uevent: version 1.0.3
[   38.494068] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   39.329567] kjournald starting.  Commit interval 5 seconds
[   39.329846] EXT3 FS on sda4, internal journal
[   39.329853] EXT3-fs: mounted filesystem with ordered data mode.
[   40.383548] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.953567] No dock devices found.
[   41.208096] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[   41.207944] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[   41.207949] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[   41.207951] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   41.207953] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   42.253523] ppdev: user-space parallel port driver
[   42.414593] audit(1264690239.087:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5359 profile="/usr/sbin/cupsd" namespace="default"
[   42.898540] Clocksource tsc unstable (delta = -98369436 ns)
[   44.221196] Bluetooth: Core ver 2.11
[   44.221554] NET: Registered protocol family 31
[   44.221557] Bluetooth: HCI device and connection manager initialized
[   44.221561] Bluetooth: HCI socket layer initialized
[   44.234239] Bluetooth: L2CAP ver 2.9
[   44.234244] Bluetooth: L2CAP socket layer initialized
[   44.280178] Bluetooth: RFCOMM socket layer initialized
[   44.280196] Bluetooth: RFCOMM TTY layer initialized
[   44.280198] Bluetooth: RFCOMM ver 1.8
[   45.096214] NET: Registered protocol family 17
[   48.135593] NET: Registered protocol family 10
[   48.135937] lo: Disabled Privacy Extensions
[   53.033347] eth0: no IPv6 routers present
[   62.875040] CPU0 attaching NULL sched-domain.
[   62.875051] CPU1 attaching NULL sched-domain.
[   62.892339] CPU0 attaching sched-domain:
[   62.892344]  domain 0: span 03
[   62.892347]   groups: 01 02
[   62.892351]   domain 1: span 03
[   62.892353]    groups: 03
[   62.892356] CPU1 attaching sched-domain:
[   62.892359]  domain 0: span 03
[   62.892361]   groups: 02 01
[   62.892365]   domain 1: span 03
[   62.892368]    groups: 03
[   86.048684] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   86.137014] usb 1-2: configuration #1 chosen from 1 choice
[   86.142198] input: GreenAsia Inc.    USB Joystick      as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input10
[   86.162120] input,hidraw1: USB HID v1.10 Joystick [GreenAsia Inc.    USB Joystick     ] on usb-0000:00:02.0-2

```

---

