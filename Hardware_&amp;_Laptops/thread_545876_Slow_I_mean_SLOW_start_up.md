---
title: "Slow I mean SLOW start up"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by johnbl on 2007-09-08
My system was off line for some time whilst the lights are on no one home networking problem was, seemingly, resolved. 
Now with 0.6.4-8 network manager installed  up I'm at least online.

However, boot now runs, logon user name / password, then, pink screen for 4 minutes or so. After a while a white rectangle taking say 1/9th of screen area opens in the upper left corner.

An error message to the effect that the system will attempt to fix the startup daemon next time shows and the boot completes. Next time is like the last time however, groundhog day but I'm not getting  'it ' what ever ' it ' is <sigh>

last lines of dmesg that seems to show the halt are;

[   32.972000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   34.008000] [drm] Initialized drm 1.1.0 20060810
[   34.016000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   34.016000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   34.016000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   34.780000] ppdev: user-space parallel port driver
[   35.412000] NET: Registered protocol family 17
[   35.760000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   35.760000] apm: overridden by ACPI.
[   40.480000] NET: Registered protocol family 10
[   40.480000] lo: Disabled Privacy Extensions
[   50.996000] eth1: no IPv6 routers present
[   51.396000] eth0: no IPv6 routers present

Any help on how to stop the system looking for the IPv6 routers that it seems to have the hots for would be most appreciated..

---

### Post by ddrichardson on 2007-09-08
Open a terminal and```
gksudo gedit /etc/modprobe.d/blacklist
```Add a line that reads```

blacklist ipv6
```Reboot

---

### Post by johnbl on 2007-09-10
Thanks for that,

That worked, in that ipv6 is no longer a feature of dmesg, however, slow is growing to now some 12 minutes hung... Have also noted that in /dev there are many many files being created at boot some 255 pty##,255 tty## , plus multiple  RAM#,  vcs#  all zero length

No idea what they all mean!


I've highlighted two areas that may be some indication in dmesg , like I'd know <sigh> but in the first the time seems to restart on setting up the clock, the second again the clock but with a sizeable delay.

All a mystery to me I'm afraid but it sure makes a mobile notebook very ' static '...<sigh>
Clearly something I've done or not is at the root of this and as that was ' rescuing ' the ability to get on line via replacement of Network Manager am wondering, but how to reverse all that ..

dmesg in whole is now 

j@interserve3:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003eed0000 end: 000000003efd0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003efd0000 size: 000000000000f000 end: 000000003efdf000 type: 3
[    0.000000] copy_e820_map() start: 000000003efdf000 size: 0000000000021000 end: 000000003f000000 type: 4
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003efd0000 (usable)
[    0.000000]  BIOS-e820: 000000003efd0000 - 000000003efdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003efdf000 - 000000003f000000 (ACPI NVS)
[    0.000000] 111MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 258000) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   258000
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   258000
[    0.000000] On node 0 totalpages: 258000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 223 pages used for memmap
[    0.000000]   HighMem zone: 28401 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f6540
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x03000523 MSFT 0x00000097) @ 0x3efd0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x03000523 MSFT 0x00000097) @ 0x3efd0200
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x03000523 MSFT 0x00000097) @ 0x3efdf040
[    0.000000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x02002026) @ 0x3efd3a80
[    0.000000] ACPI: DSDT (v001  1ABWG 1ABWG001 0x00000001 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f000000:c1000000)
[    0.000000] Detected 2000.146 MHz processor.
[    8.217463] Built 1 zonelists.  Total pages: 255985
[    8.217467] Kernel command line: root=UUID=3c40d6ed-5807-4662-a3bf-50cb661bea78 ro quiet splash
[    8.217614] Found and enabled local APIC!
[    8.217617] mapped APIC to ffffd000 (fee00000)
[    8.217621] Enabling fast FPU save and restore... done.
[    8.217623] Enabling unmasked SIMD FPU exception support... done.
[    8.217633] Initializing CPU#0
[    8.217708] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.219168] Console: colour VGA+ 80x25
[    8.219565] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.220037] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.251295] Memory: 1011944k/1032000k available (1993k kernel code, 19328k reserved, 900k data, 328k init, 114496k highmem)
[    8.251305] virtual kernel memory layout:
[    8.251305]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.251307]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.251308]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.251309]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.251310]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    8.251311]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[    8.251312]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[    8.251315] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.329504] Calibrating delay using timer specific routine.. 4002.64 BogoMIPS (lpj=8005295)
[    8.329540] Security Framework v1.0.0 initialized
[    8.329547] SELinux:  Disabled at boot.
[    8.329562] Mount-cache hash table entries: 512
[    8.329683] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[    8.329694] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.329696] CPU: L2 cache: 2048K
[    8.329699] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000
[    8.329707] Compat vDSO mapped to ffffe000.
[    8.329710] Remapping vsyscall page to ffffe000
[    8.329719] Checking 'hlt' instruction... OK.
[    8.345561] SMP alternatives: switching to UP code
[    8.345750] Freeing SMP alternatives: 11k freed
[    8.345910] Early unpacking initramfs... done
[    8.625053] ACPI: Core revision 20060707
[    8.625731] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.627078] ACPI: setting ELCR to 0200 (from 0e28)
[    8.698692] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06
[    8.698696] SMP motherboard not detected.
[    8.804656] Brought up 1 CPUs
[    8.804870] Booting paravirtualized kernel on bare hardware
[    8.804936] Time: 21:33:37  Date: 08/10/107
[    8.804961] NET: Registered protocol family 16
[    8.805037] EISA bus registered
[    8.805041] ACPI: bus type pci registered
[    8.806098] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    8.806100] PCI: Using configuration type 1
[    8.806101] Setting up standard PCI resources
[    8.816134] ACPI: Interpreter enabled
[    8.816137] ACPI: Using PIC for interrupt routing
[    8.816409] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.816416] PCI: Probing PCI hardware (bus 00)
[    8.816676] Boot video device is 0000:00:02.0
[    8.816947] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    8.816950] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[    8.817254] PCI: Transparent bridge - 0000:00:1e.0
[    8.817298] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[    8.817301] Please report the result to linux-kernel to fix this permanently
[    8.817314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.843120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    8.848156] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    8.848423] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    8.848696] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.848956] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    8.849217] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.849476] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.849738] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.850000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.850116] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.850122] pnp: PnP ACPI init
[    8.851991] pnp: PnP ACPI: found 10 devices
[    8.851995] PnPBIOS: Disabled by ACPI PNP
[    8.852032] PCI: Using ACPI for IRQ routing
[    8.852035] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.855359] NET: Registered protocol family 8
[    8.855361] NET: Registered protocol family 20
[    8.855843] pnp: 00:08: ioport range 0x1100-0x113f has been reserved
[    8.855846] pnp: 00:08: ioport range 0x1254-0x1254 has been reserved
[    8.855848] pnp: 00:08: ioport range 0x12d4-0x12d4 has been reserved
[    8.855850] pnp: 00:08: ioport range 0x1300-0x1375 has been reserved
[    8.855853] pnp: 00:08: ioport range 0x1377-0x137f has been reserved
[    8.856078] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    8.856090] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[    8.856093]   IO window: 0000c000-0000c0ff
[    8.856096]   IO window: 0000c400-0000c4ff
[    8.856100]   PREFETCH window: 40000000-43ffffff
[    8.856104]   MEM window: 48000000-4bffffff
[    8.856107] PCI: Bridge: 0000:00:1e.0
[    8.856109]   IO window: c000-cfff
[    8.856114]   MEM window: ffb00000-ffbfffff
[    8.856117]   PREFETCH window: 40000000-43ffffff
[    8.856128] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.856311] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[    8.856314] PCI: setting IRQ 3 as level-triggered
[    8.856317] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[    8.856322] PCI: Setting latency timer of device 0000:01:03.0 to 64
[    8.856344] NET: Registered protocol family 2
[    8.880532] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.880629] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.881482] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.882086] TCP: Hash tables configured (established 131072 bind 65536)
[    8.882090] TCP reno registered
[    8.892614] checking if image is initramfs... it is
[    9.446337] Freeing initrd memory: 6767k freed
[    9.446770] audit: initializing netlink socket (disabled)
[    9.446787] audit(1189460017.240:1): initialized
[    9.446857] highmem bounce pool size: 64 pages
[    9.446920] VFS: Disk quotas dquot_6.5.1
[    9.446938] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.446991] io scheduler noop registered
[    9.446993] io scheduler anticipatory registered
[    9.446995] io scheduler deadline registered
[    9.447005] io scheduler cfq registered (default)
[    9.447292] isapnp: Scanning for PnP cards...
[    9.800365] isapnp: No Plug & Play device found
[    9.822229] Real Time Clock Driver v1.12ac
[    9.822281] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.822970] mice: PS/2 mouse device common for all mice
[    9.823427] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.823646] input: Macintosh mouse button emulation as /class/input/input0
[    9.823674] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.823677] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.823886] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.829147] i8042.c: Detected active multiplexing controller, rev 1.0.
[    9.830147] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.830151] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.830153] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.830155] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.830157] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.830264] EISA: Probing bus 0 at eisa.0
[    9.830306] EISA: Detected 0 cards.
[    9.860341] TCP cubic registered
[    9.860349] NET: Registered protocol family 1
[    9.860398] Testing NMI watchdog ... OK.
[    9.900034] Using IPI No-Shortcut mode
[    9.900082] ACPI: (supports S0 S3 S4 S5)
[    9.900121]   Magic number: 7:28:601
[    9.900167]   hash matches device ptyd5
[    9.900435] Freeing unused kernel memory: 328k freed
[    9.900847] input: AT Translated Set 2 keyboard as /class/input/input1
[[COLOR="Yellow"]    9.902572] Time: tsc clocksource has been installed.
[   11.085245] Capability LSM initialized[/COLOR]
[   11.113575] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.113580] ACPI: Processor [CPU1] (supports 8 throttling states)
[   11.114278] ACPI: Thermal Zone [THRM] (11 C)
[   11.411726] usbcore: registered new interface driver usbfs
[   11.411751] usbcore: registered new interface driver hub
[   11.411777] usbcore: registered new device driver usb
[   11.412463] USB Universal Host Controller Interface driver v3.0
[   11.412747] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   11.412750] PCI: setting IRQ 11 as level-triggered
[   11.412754] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.412764] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.412768] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.412919] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.412940] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000e480
[   11.413030] usb usb1: configuration #1 chosen from 1 choice
[   11.413049] hub 1-0:1.0: USB hub found
[   11.413054] hub 1-0:1.0: 2 ports detected
[   11.481538] ieee1394: Initialized config rom entry `ip1394'
[   11.490549] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   11.515935] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   11.515939] PCI: setting IRQ 5 as level-triggered
[   11.515943] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   11.515954] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.515957] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.515978] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.516002] uhci_hcd 0000:00:1d.1: irq 5, io base 0x0000e800
[   11.516085] usb usb2: configuration #1 chosen from 1 choice
[   11.516106] hub 2-0:1.0: USB hub found
[   11.516112] hub 2-0:1.0: 2 ports detected
[   11.619727] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   11.619731] PCI: setting IRQ 9 as level-triggered
[   11.619734] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   11.619745] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.619749] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.619768] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.619789] uhci_hcd 0000:00:1d.2: irq 9, io base 0x0000e880
[   11.619869] usb usb3: configuration #1 chosen from 1 choice
[   11.619895] hub 3-0:1.0: USB hub found
[   11.619900] hub 3-0:1.0: 2 ports detected
[    3.276000] Time: acpi_pm clocksource has been installed.
[    3.340000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.340000] PCI: setting IRQ 10 as level-triggered
[    3.340000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.340000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.340000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.340000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.340000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.340000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.340000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xffdffc00
[    3.344000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.344000] usb usb4: configuration #1 chosen from 1 choice
[    3.344000] hub 4-0:1.0: USB hub found
[    3.344000] hub 4-0:1.0: 6 ports detected
[    3.452000] SCSI subsystem initialized
[    3.456000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[    3.504000] libata version 2.20 loaded.
[    3.508000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[ffbfe800-ffbfefff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.512000] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.512000] 8139cp 0000:01:0c.0: Try the "8139too" driver instead.
[    3.520000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.520000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.520000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[    3.520000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.524000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    3.524000] 8139too Fast Ethernet driver 0.9.28
[    3.524000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    3.524000] scsi0 : ata_piix
[    3.688000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.688000] ata1.00: ATA-6: ST980829A, 3.04, max UDMA/100
[    3.688000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.696000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.696000] ata1.00: configured for UDMA/100
[    3.696000] scsi1 : ata_piix
[    4.172000] ata2.00: ATAPI, max UDMA/33
[    4.272000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.336000] ata2.00: configured for UDMA/33
[    4.336000] scsi 0:0:0:0: Direct-Access     ATA      ST980829A        3.04 PQ: 0 ANSI: 5
[    4.336000] scsi 1:0:0:0: CD-ROM            QSI      DVD+-RW SDW-082S LX06 PQ: 0 ANSI: 5
[    4.336000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    4.336000] eth0: RealTek RTL8139 at 0xf88a0400, 00:03:0d:28:4b:2d, IRQ 5
[    4.336000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.348000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.348000] sda: Write Protect is off
[    4.348000] sda: Mode Sense: 00 3a 00 00
[    4.348000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.348000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.348000] sda: Write Protect is off
[    4.348000] sda: Mode Sense: 00 3a 00 00
[    4.348000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.348000]  sda: sda1 sda2 < sda5 >
[    4.384000] sd 0:0:0:0: Attached scsi disk sda
[    4.388000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.388000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.396000] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[    4.396000] Uniform CD-ROM driver Revision: 3.20
[    4.396000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.444000] usb 2-1: configuration #1 chosen from 1 choice
[    4.672000] Attempting manual resume
[    4.672000] swsusp: Resume From Partition 8:5
[    4.672000] PM: Checking swsusp image.
[    4.672000] PM: Resume from disk failed.
[    4.688000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.720000] kjournald starting.  Commit interval 5 seconds
[    4.720000] EXT3-fs: mounted filesystem with ordered data mode.
[    4.780000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d492230be1f]
[    4.840000] usb 3-2: configuration #1 chosen from 1 choice
[    4.844000] hub 3-2:1.0: USB hub found
[    4.844000] hub 3-2:1.0: 4 ports detected
[    5.160000] usb 3-2.4: new low speed USB device using uhci_hcd and address 3
[    5.300000] usb 3-2.4: configuration #1 chosen from 1 choice
[    5.304000] usbcore: registered new interface driver hiddev
[    5.324000] input: Logitech USB RECEIVER as /class/input/input2
[    5.324000] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.1-1
[    5.336000] input: Logitech USB Receiver as /class/input/input3
[    5.336000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2.4
[    5.368000] input: Logitech USB Receiver as /class/input/input4
[    5.368000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2.4
[    5.368000] usbcore: registered new interface driver usbhid
[B][U][    5.368000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.900000] Linux agpgart interface v0.102 (c) Dave Jones[/U][/B]
[   17.924000] agpgart: Detected an Intel 855 Chipset.
[   17.924000] agpgart: Detected 16252K stolen memory.
[   17.932000] agpgart: AGP aperture is 128M @ 0xf0000000
[   17.940000] intel_rng: FWH not detected
[   18.016000] iTCO_vendor_support: vendor-support=0
[   18.016000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.016000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0460)
[   18.016000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.112000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.116000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.788000] input: PC Speaker as /class/input/input5
[   18.836000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x926eb1, caps: 0x804719/0x0
[   18.880000] input: SynPS/2 Synaptics TouchPad as /class/input/input6
[   18.996000] Yenta: CardBus bridge found at 0000:01:03.0 [1584:3200]
[   18.996000] Yenta: adjusting diagnostic: 40 -> 60
[   18.996000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.996000] Yenta: Routing CardBus interrupts to PCI
[   18.996000] Yenta TI: socket 0000:01:03.0, mfunc 0x000c1002, devctl 0x44
[   19.008000] usbcore: registered new interface driver lmpcm_usb
[   19.008000] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   19.040000] ieee80211_crypt: registered algorithm 'NULL'
[   19.040000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.040000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.080000] psmouse.c: Failed to reset mouse on isa0060/serio3
[   19.200000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   19.200000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.228000] Yenta: ISA IRQ mask 0x00d0, PCI irq 3
[   19.228000] Socket status: 30000006
[   19.228000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   19.228000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   19.228000] cs: IO port probe 0xc000-0xcfff: clean.
[   19.228000] pcmcia: parent PCI bridge Memory window: 0xffb00000 - 0xffbfffff
[   19.228000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   19.228000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   19.228000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.564000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   19.712000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   19.712000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.712000] cs: IO port probe 0x820-0x8ff: clean.
[   19.716000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.716000] cs: IO port probe 0xa00-0xaff: clean.
[   19.796000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   19.796000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.064000] AC'97 1 does not respond - RESET
[   21.064000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   21.064000] Unable to initialize codec #1
[   21.120000] intel8x0_measure_ac97_clock: measured 55637 usecs
[   21.120000] intel8x0: clocking to 48000
[   28.536000] input: PS/2 Generic Mouse as /class/input/input7
[   28.736000] psmouse.c: Failed to enable mouse on isa0060/serio3
[   29.060000] fuse init (API version 7.8)
[   29.136000] lp: driver loaded but no devices found
[   29.252000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   29.376000] Adding 2980016k swap on /dev/disk/by-uuid/a304571e-9f4a-4144-884a-96951ebea191.  Priority:-1 extents:1 across:2980016k
[   29.540000] EXT3 FS on sda1, internal journal
[   30.776000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   30.924000] input: Power Button (FF) as /class/input/input8
[   30.928000] ACPI: Power Button (FF) [PWRF]
[   30.956000] input: Lid Switch as /class/input/input9
[   30.960000] ACPI: Lid Switch [LID]
[   30.988000] input: Sleep Button (CM) as /class/input/input10
[   30.992000] ACPI: Sleep Button (CM) [SLPB]
[   31.020000] input: Power Button (CM) as /class/input/input11
[   31.024000] ACPI: Power Button (CM) [PWRB]
[   31.040000] ibm_acpi: ec object not found
[   31.064000] Using specific hotkey driver
[   31.092000] No dock devices found.
[   31.112000] ACPI: AC Adapter [AC0] (on-line)
[   31.132000] ACPI: Battery Slot [BAT0] (battery present)
[   31.172000] pcc_acpi: loading...
[   32.684000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   33.788000] [drm] Initialized drm 1.1.0 20060810
[   33.792000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   33.792000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   33.796000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   34.556000] ppdev: user-space parallel port driver
[   35.088000] NET: Registered protocol family 17
[   35.560000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   35.560000] apm: overridden by ACPI.
j@interserve3:~$

---

### Post by ddrichardson on 2007-09-10
For generally quicker booting, try [here]("http://ubuntuforums.org/showthread.php?t=89491").

As for the highlighted line, put ```
clocksource=acpi_pm
``` on the grub bootline and see if it helps.

You are right though in that something has triggered this problem - I'm assuming that the Live CD boots relatively quickly - proving there isn't a problem relating to voltages.

This is very much in the domain of the lernel developer which I am not. Hopefully someone can provide a better explanation.

One thing - has any one specified specific timing options? What is appended as kernel/grub options in grub.lst?

---

