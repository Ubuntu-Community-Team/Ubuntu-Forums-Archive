---
title: "logitech wireless usb keyboard doesnt work"
date: 2008-06-17
forum: Hardware
---

### Post by Jonomac on 2008-06-17
I have the USB keyboard turned on in the BIOS but i can not get the wireless keyboard to work. At the initial startup at the start of grub i can hit buttons and it beeps but doesn't actually do what the button should do like arrow or enter. anyway it would be nice if anyone could help me with this. This is what lsusb gives (so the thing is recognized but not used)
jon@home:~$ lsusb
Bus 004 Device 006: ID 13b1:0014 Linksys
Bus 004 Device 004: ID 1058:0901 Western Digital Technologies, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:3b11 Hewlett-Packard
Bus 001 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000


Thanks in advance for any info anyone can provide.

as a side note i kept searching posts and found how to change the keyboard you are using.
>>System>>Preferences>>keyboard....i have tried all the choices for logitech rebooting each time and still couldnt get the thing to work.  Any ideas?????

---

### Post by ukripper on 2008-06-17
> **Jonomac said:**
> I have the USB keyboard turned on in the BIOS but i can not get the wireless keyboard to work. At the initial startup at the start of grub i can hit buttons and it beeps but doesn't actually do what the button should do like arrow or enter. anyway it would be nice if anyone could help me with this. This is what lsusb gives (so the thing is recognized but not used)
jon@home:~$ lsusb
Bus 004 Device 006: ID 13b1:0014 Linksys
Bus 004 Device 004: ID 1058:0901 Western Digital Technologies, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:3b11 Hewlett-Packard
Bus 001 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000


Thanks in advance for any info anyone can provide.

as a side note i kept searching posts and found how to change the keyboard you are using.
>>System>>Preferences>>keyboard....i have tried all the choices for logitech rebooting each time and still couldnt get the thing to work.  Any ideas?????

Can you post output of the following:
```
dmesg | less
```

and ```
lsmod | grep usb
```

---

### Post by Jonomac on 2008-06-17
jon@home:~$ lsmod|grep usb
usblp                  15872  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
usb_storage            73664  4 
libusual               19108  1 usb_storage
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
usbcore               146028  8 usblp,ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd

the other is insanely long, Is there a way to save output of a terminal command to a file then i can copy past or do i have to just copy paste from terminal cause thats not working so  well cause when i hit enter the top skips a few lines and i wont be able to get all the output??

---

### Post by zoke on 2008-06-17
> **Jonomac said:**
> 
the other is insanely long, Is there a way to save output of a terminal command to a file then i can copy past or do i have to just copy paste from terminal cause thats not working so  well cause when i hit enter the top skips a few lines and i wont be able to get all the output??

sure just turn it into 
```
lsmod | grep usb > output.txt
```

then you can open up the file and paste the contents here.

---

### Post by Jonomac on 2008-06-18
thanks for that hint on saving output to a file : hope this helps 

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 4 16:35:01 UTC 2008 (Ubuntu 2.6.24-19.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff40000 (usable)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff50000 - 0000000040000000 (ACPI NVS)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261952) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261952
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261952
[    0.000000] On node 0 totalpages: 261952
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32322 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6CB0 checksum 0
[    0.000000] ACPI: RSDP 000F6CB0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF40000, 002C (r1 A M I  OEMRSDT   5000222 MSFT       97)
[    0.000000] ACPI: FACP 3FF40200, 0081 (r2 A M I  OEMFACP   5000222 MSFT       97)
[    0.000000] ACPI: DSDT 3FF40400, 39D5 (r1   DELL DIM 4500      10A MSFT  100000D)
[    0.000000] ACPI: FACS 3FF50000, 0040
[    0.000000] ACPI: APIC 3FF40300, 0054 (r1 A M I  OEMAPIC   5000222 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259906
[    0.000000] Kernel command line: root=UUID=402f177c-a242-4a84-91d9-663d9c87c31b ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1794.751 MHz processor.
[   24.025527] Console: colour VGA+ 80x25
[   24.025534] console [tty0] enabled
[   24.026330] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.027463] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.082481] Memory: 1026660k/1047808k available (2177k kernel code, 20452k reserved, 1006k data, 368k init, 130304k highmem)
[   24.082497] virtual kernel memory layout:
[   24.082498]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.082500]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.082502]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.082503]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.082505]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   24.082506]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   24.082507]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   24.082512] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.082587] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.162544] Calibrating delay using timer specific routine.. 3593.97 BogoMIPS (lpj=7187955)
[   24.162589] Security Framework initialized
[   24.162602] SELinux:  Disabled at boot.
[   24.162626] AppArmor: AppArmor initialized
[   24.162634] Failure registering capabilities with primary security module.
[   24.162647] Mount-cache hash table entries: 512
[   24.162876] Initializing cgroup subsys ns
[   24.162884] Initializing cgroup subsys cpuacct
[   24.162902] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   24.162924] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   24.162928] CPU: L2 cache: 256K
[   24.162932] CPU: Hyper-Threading is disabled
[   24.162935] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[   24.162956] Compat vDSO mapped to ffffe000.
[   24.162978] Checking 'hlt' instruction... OK.
[   24.179125] SMP alternatives: switching to UP code
[   24.181820] Freeing SMP alternatives: 11k freed
[   24.182023] Early unpacking initramfs... done
[   24.693670] ACPI: Core revision 20070126
[   24.693747] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.696435] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 02
[   24.696497] Total of 1 processors activated (3593.97 BogoMIPS).
[   24.696647] ENABLING IO-APIC IRQs
[   24.696839] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.841996] Brought up 1 CPUs
[   24.842028] CPU0 attaching sched-domain:
[   24.842033]  domain 0: span 01
[   24.842036]   groups: 01
[   24.842357] net_namespace: 64 bytes
[   24.842375] Booting paravirtualized kernel on bare hardware
[   24.843231] Time: 10:36:57  Date: 06/17/08
[   24.843272] NET: Registered protocol family 16
[   24.843644] EISA bus registered
[   24.843681] ACPI: bus type pci registered
[   24.843945] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   24.843948] PCI: Using configuration type 1
[   24.843980] Setting up standard PCI resources
[   24.860204] ACPI: EC: Look up EC in DSDT
[   24.865626] ACPI: Interpreter enabled
[   24.865634] ACPI: (supports S0 S1 S4 S5)
[   24.865658] ACPI: Using IOAPIC for interrupt routing
[   24.875071] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.875612] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   24.875615] * this clock source is slow. If you are sure your timer does not have
[   24.875617] * this bug, please use "acpi_pm_good" to disable the workaround
[   24.875681] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   24.875686] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   24.876386] PCI: Transparent bridge - 0000:00:1e.0
[   24.876423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.876584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   24.879184] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   24.879403] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   24.879610] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   24.880054] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   24.880261] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   24.880469] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   24.880678] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   24.880886] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   24.881140] ACPI: Power Resource [URP1] (off)
[   24.881190] ACPI: Power Resource [FDDP] (off)
[   24.881237] ACPI: Power Resource [LPTP] (off)
[   24.881347] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.881411] pnp: PnP ACPI init
[   24.881427] ACPI: bus type pnp registered
[   24.887340] pnp: PnP ACPI: found 13 devices
[   24.887347] ACPI: ACPI bus type pnp unregistered
[   24.887355] PnPBIOS: Disabled by ACPI PNP
[   24.887816] PCI: Using ACPI for IRQ routing
[   24.887822] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.905879] NET: Registered protocol family 8
[   24.905883] NET: Registered protocol family 20
[   24.906028] AppArmor: AppArmor Filesystem Enabled
[   24.909857] Time: tsc clocksource has been installed.
[   24.917953] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   24.917967] system 00:0b: ioport range 0x400-0x47f has been reserved
[   24.917971] system 00:0b: ioport range 0x680-0x6ff has been reserved
[   24.917975] system 00:0b: ioport range 0x480-0x4bf has been reserved
[   24.917982] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   24.917987] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[   24.917998] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   24.918003] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved
[   24.918007] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   24.918012] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[   24.918015] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   24.948790] PCI: Bridge: 0000:00:01.0
[   24.948796]   IO window: c000-cfff
[   24.948802]   MEM window: ff800000-ff8fffff
[   24.948808]   PREFETCH window: be900000-de9fffff
[   24.948814] PCI: Bridge: 0000:00:1e.0
[   24.948818]   IO window: d000-dfff
[   24.948826]   MEM window: ff900000-ff9fffff
[   24.948831]   PREFETCH window: dea00000-deafffff
[   24.948853] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.948878] NET: Registered protocol family 2
[   24.985912] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.986473] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.987980] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.988808] TCP: Hash tables configured (established 131072 bind 65536)
[   24.988815] TCP reno registered
[   24.998045] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   25.469672]  it is
[   25.993304] Freeing initrd memory: 7318k freed
[   25.994233] audit: initializing netlink socket (disabled)
[   25.994255] audit(1213699017.808:1): initialized
[   25.994529] highmem bounce pool size: 64 pages
[   25.997903] VFS: Disk quotas dquot_6.5.1
[   25.998055] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.998302] io scheduler noop registered
[   25.998306] io scheduler anticipatory registered
[   25.998309] io scheduler deadline registered
[   25.998335] io scheduler cfq registered (default)
[   25.998420] Boot video device is 0000:01:00.0
[   25.998940] isapnp: Scanning for PnP cards...
[   26.353032] isapnp: No Plug & Play device found
[   26.439141] Real Time Clock Driver v1.12ac
[   26.439305] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.439479] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.440976] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.442505] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.442637] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.442826] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.442831] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   26.443487] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.452531] mice: PS/2 mouse device common for all mice
[   26.452786] EISA: Probing bus 0 at eisa.0
[   26.452828] EISA: Detected 0 cards.
[   26.452833] cpuidle: using governor ladder
[   26.452836] cpuidle: using governor menu
[   26.452989] NET: Registered protocol family 1
[   26.453040] Using IPI No-Shortcut mode
[   26.453089] registered taskstats version 1
[   26.453234]   Magic number: 12:915:628
[   26.453393] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.453396] EDD information not available.
[   26.453948] Freeing unused kernel memory: 368k freed
[   26.488308] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.889017] fuse init (API version 7.9)
[   27.932004] ACPI: Processor [CPU1] (supports 8 throttling states)
[   29.097713] usbcore: registered new interface driver usbfs
[   29.097750] usbcore: registered new interface driver hub
[   29.133858] usbcore: registered new device driver usb
[   29.215551] SCSI subsystem initialized
[   29.226718] USB Universal Host Controller Interface driver v3.0
[   29.226829] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.226846] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.226852] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.227335] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   29.227379] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[   29.227615] usb usb1: configuration #1 chosen from 1 choice
[   29.227654] hub 1-0:1.0: USB hub found
[   29.227664] hub 1-0:1.0: 2 ports detected
[   29.329512] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   29.329530] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.329537] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.329576] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   29.329610] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880
[   29.329790] usb usb2: configuration #1 chosen from 1 choice
[   29.329830] hub 2-0:1.0: USB hub found
[   29.329840] hub 2-0:1.0: 2 ports detected
[   29.329936] 8139too Fast Ethernet driver 0.9.28
[   29.332348] libata version 3.00 loaded.
[   29.426330] Floppy drive(s): fd0 is 1.44M
[   29.434583] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   29.434602] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.434608] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.434648] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   29.434683] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[   29.434867] usb usb3: configuration #1 chosen from 1 choice
[   29.434909] hub 3-0:1.0: USB hub found
[   29.434920] hub 3-0:1.0: 2 ports detected
[   29.444976] FDC 0 is a post-1991 82077
[   29.537486] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   29.537512] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.537518] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.537572] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   29.541488] ehci_hcd 0000:00:1d.7: debug port 1
[   29.541497] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   29.541514] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffaffc00
[   29.569150] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   29.581085] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.581297] usb usb4: configuration #1 chosen from 1 choice
[   29.581337] hub 4-0:1.0: USB hub found
[   29.581347] hub 4-0:1.0: 6 ports detected
[   29.685319] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   29.686183] eth0: RealTek RTL8139 at 0xd800, 00:c0:a8:7e:f7:a2, IRQ 18
[   29.686188] eth0:  Identified 8139 chip type 'RTL-8139C'
[   29.689114] ata_piix 0000:00:1f.1: version 2.12
[   29.689139] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   29.689148] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   29.689215] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   29.694499] scsi0 : ata_piix
[   29.696205] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   29.697890] scsi1 : ata_piix
[   29.699701] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   29.699705] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   29.874319] ata1.00: HPA unlocked: 390719855 -> 390721968, native 390721968
[   29.874329] ata1.00: ATA-6: WDC WD2000JB-00GVA0, 08.02D08, max UDMA/100
[   29.874334] ata1.00: 390721968 sectors, multi 16: LBA48 
[   29.874359] ata1.00: limited to UDMA/33 due to 40-wire cable
[   29.890489] ata1.00: configured for UDMA/33
[   30.388704] ata2.00: ATAPI: SAMSUNG DVD-ROM SD-616T, F308, max UDMA/33
[   30.388745] ata2.01: ATAPI: _NEC CD-RW NR-7900A, 1.08, max UDMA/33
[   30.553690] ata2.00: configured for UDMA/33
[   30.724345] ata2.01: configured for UDMA/33
[   30.724546] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JB-00G 08.0 PQ: 0 ANSI: 5
[   30.725175] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  F308 PQ: 0 ANSI: 5
[   30.731098] scsi 1:0:1:0: CD-ROM            _NEC     NR-7900A         1.08 PQ: 0 ANSI: 5
[   30.787995] Driver 'sd' needs updating - please use bus_type methods
[   30.788133] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   30.788155] sd 0:0:0:0: [sda] Write Protect is off
[   30.788159] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.788192] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.788277] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   30.788297] sd 0:0:0:0: [sda] Write Protect is off
[   30.788301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.788333] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.788339]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   30.810438]  sda1 sda2 sda3
[   30.811841] usb 4-3: new high speed USB device using ehci_hcd and address 4
[   30.827663] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.840198] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   30.840206] Uniform CD-ROM driver Revision: 3.20
[   30.840296] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   30.842050] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   30.842146] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   30.842266] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.842296] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   30.842325] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   30.948498] usb 4-3: configuration #1 chosen from 1 choice
[   31.371265] usb 4-6: new high speed USB device using ehci_hcd and address 6
[   31.382201] Attempting manual resume
[   31.382208] swsusp: Resume From Partition 8:2
[   31.382211] PM: Checking swsusp image.
[   31.382516] PM: Resume from disk failed.
[   31.436834] kjournald starting.  Commit interval 5 seconds
[   31.436858] EXT3-fs: mounted filesystem with ordered data mode.
[   31.506085] usb 4-6: configuration #1 chosen from 1 choice
[   31.506483] usbcore: registered new interface driver libusual
[   31.518703] Initializing USB Mass Storage driver...
[   31.742854] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   31.919809] usb 2-2: configuration #1 chosen from 1 choice
[   31.933354] scsi2 : SCSI emulation for USB Mass Storage devices
[   31.933726] usbcore: registered new interface driver usb-storage
[   31.933734] USB Mass Storage support registered.
[   31.934017] usb-storage: device found at 4
[   31.934021] usb-storage: waiting for device to settle before scanning
[   32.170414] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   32.347973] usb 1-1: configuration #1 chosen from 1 choice
[   32.589990] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   32.790486] usb 1-2: configuration #1 chosen from 1 choice
[   32.793952] scsi3 : SCSI emulation for USB Mass Storage devices
[   32.794166] usb-storage: device found at 4
[   32.794169] usb-storage: waiting for device to settle before scanning
[   36.934186] usb-storage: device scan complete
[   36.966616] scsi 2:0:0:0: Direct-Access     WD       2500JB External  0107 PQ: 0 ANSI: 0
[   36.968190] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   36.969066] sd 2:0:0:0: [sdb] Write Protect is off
[   36.969070] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   36.969073] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   36.970077] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   36.970945] sd 2:0:0:0: [sdb] Write Protect is off
[   36.970950] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   36.970953] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   36.970961]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[   37.023114] sd 2:0:0:0: [sdb] Attached SCSI disk
[   37.023181] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   37.790527] usb-storage: device scan complete
[   37.793501] scsi 3:0:0:0: Direct-Access     HP                        1.00 PQ: 0 ANSI: 2
[   37.798865] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[   37.798931] sd 3:0:0:0: Attached scsi generic sg4 type 0
[   41.325175] Linux agpgart interface v0.102
[   41.436981] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.508997] agpgart: Detected an Intel 845G Chipset.
[   41.580192] agpgart: AGP aperture is 256M @ 0xe0000000
[   41.597844] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.073514] input: Power Button (FF) as /devices/virtual/input/input2
[   42.088254] ACPI: Power Button (FF) [PWRF]
[   42.088472] input: Sleep Button (CM) as /devices/virtual/input/input3
[   42.104218] ACPI: Sleep Button (CM) [SLPB]
[   42.125625] intel_rng: Firmware space is locked read-only. If you can't or
[   42.125629] intel_rng: don't want to disable this in firmware setup, and if
[   42.125632] intel_rng: you are certain that your system has a functional
[   42.125634] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   42.296429] iTCO_vendor_support: vendor-support=0
[   42.339457] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   42.339669] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   42.339740] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   43.742813] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   43.823795] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   44.497267] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   44.497327] [fglrx] ASYNCIO init succeed!
[   44.497461] [fglrx] PAT is enabled successfully!
[   44.505764] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   46.368426] parport_pc 00:07: reported by Plug and Play ACPI
[   46.368458] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   46.479960] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   46.580963] usbcore: registered new interface driver hiddev
[   46.599659] input: Wireless Mouse Wireless Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input5
[   46.611784] input,hidraw0: USB HID v1.10 Mouse [Wireless Mouse Wireless Mouse] on usb-0000:00:1d.1-2
[   46.624914] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   46.626025] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input6
[   46.635713] input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1
[   46.666218] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input7
[   46.687685] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[   46.687720] usbcore: registered new interface driver usbhid
[   46.687726] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   46.723645] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3B11
[   46.723678] usbcore: registered new interface driver usblp
[   47.035181] usb 4-6: reset high speed USB device using ehci_hcd and address 6
[   47.068814] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   47.068854] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   47.190444] ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded
[   47.438763] intel8x0_measure_ac97_clock: measured 54839 usecs
[   47.438769] intel8x0: clocking to 48000
[   47.617589] wlan0: ethernet device 00:16:b6:4f:93:a6 using NDIS driver: wusb54gsv2, version: 0x4011405, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter with SpeedBooster', 13B1:0014.F.conf
[   47.651555] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   47.670607] usbcore: registered new interface driver ndiswrapper
[   50.961605] lp0: using parport0 (interrupt-driven).
[   51.069765] Adding 10482404k swap on /dev/sda2.  Priority:-1 extents:1 across:10482404k
[   51.090895] Adding 10482404k swap on /dev/sdb2.  Priority:-2 extents:1 across:10482404k
[   51.106358] Adding 3036244k swap on /dev/sdb5.  Priority:-3 extents:1 across:3036244k
[   51.710562] EXT3 FS on sda1, internal journal
[   53.231774] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.852782] No dock devices found.
[   55.564054] apm: BIOS not found.
[   55.821643] ppdev: user-space parallel port driver
[   56.004436] audit(1213717048.223:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4972 profile="/usr/sbin/cupsd" namespace="default"
[   60.803605] eth0: link down
[   61.051630] Bluetooth: Core ver 2.11
[   61.052726] NET: Registered protocol family 31
[   61.052755] Bluetooth: HCI device and connection manager initialized
[   61.052761] Bluetooth: HCI socket layer initialized
[   61.152358] Bluetooth: L2CAP ver 2.9
[   61.152366] Bluetooth: L2CAP socket layer initialized
[   61.188226] Bluetooth: RFCOMM socket layer initialized
[   61.188676] Bluetooth: RFCOMM TTY layer initialized
[   61.188734] Bluetooth: RFCOMM ver 1.8
[   63.978933] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   67.382807] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   67.382822] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   67.382828] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[   67.383995] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   67.384382] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   67.384718] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   67.385037] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[   67.392603] [fglrx] GART Table is not in FRAME_BUFFER range 
[   67.392624] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   67.512055] [fglrx] interrupt source 20008000 successfully enabled
[   67.512069] [fglrx] enable ID = 0x00000004
[   67.512656] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   67.513139] [fglrx] interrupt source 10000000 successfully enabled
[   67.513149] [fglrx] enable ID = 0x00000005
[   67.513656] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[31279.676944] NET: Registered protocol family 10
[31279.677830] lo: Disabled Privacy Extensions
[31279.679014] ADDRCONF(NETDEV_UP): eth0: link is not ready
[31279.679801] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[31287.917156] NET: Registered protocol family 17
[31288.671808] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[31298.982890] UDF-fs: No VRS found
[31298.999345] ISO 9660 Extensions: Microsoft Joliet Level 1
[31299.016056] ISOFS: changing to secondary root
[31302.161757] kjournald starting.  Commit interval 5 seconds
[31302.162160] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[31302.163029] EXT3 FS on sdb3, internal journal
[31302.163043] EXT3-fs: mounted filesystem with ordered data mode.
[31304.657471] wlan0: no IPv6 routers present

---

