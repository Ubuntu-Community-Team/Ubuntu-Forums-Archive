---
title: "I cant mount my usb enclusure help"
date: 2008-11-20
forum: Hardware
---

### Post by jcer93705 on 2008-11-20
Hi I have a enclusure from compusa with a laptop harddrive. 
It seem i cant mount it. Its because i didn't safely unmount 
it in xp. Well I cant go back to xp and unmount now, xp is gone. 
Whats next?

---

### Post by Mewshi on 2008-11-20
Is it an NTFS drive?
If so, first off, use something better :P
Second, you should be able to run a command to fix the filesystem, which should help.

If you need further help, run 'dmesg' and give us everything related to the drive.

---

### Post by Therion on 2008-11-20
See that line in the "Can not mount volume" error message that starts **For example type on the command line...**?  
Just do as it says and type in what it tells you on the command line:```
mount -t ntfs-3g /dev/sdb5 /media/Backup Storage -o force
```
I typed that up from memory, so if the Cut and Paste doesn't work, type in exactly what the error message displays.

---

### Post by taurus on 2008-11-20
> **Therion said:**
> See that line in the "Can Not Mount Volume" error message that starts **For example type on the command line...**?  
Just do as it says and type in what it tells you on the command line:```
mount -t ntfs-3g /dev/sdb5 **/media/Backup Storage** -o force
```
I typed that up from memory, so if the Cut and Paste doesn't work, type in exactly what the error message displays.

First, make sure there is such a directory because automount usually creates one as needed (then removes when you unmount the drive).  Then, you have to put the name in quotes because of white space between the words.

```
sudo mkdir /media/"Backup Storage"
sudo mount -t ntfs-3g /dev/sdb1 /media/"Backup Storage" -o force
df -h
```

---

### Post by Therion on 2008-11-20
> **taurus said:**
> ... you have to put the name in quotes because of white space between the words.
D'oh...  I KNEW THAT!!!



/facepalm...
//really, i do...

---

### Post by jcer93705 on 2008-11-20
[QUOTE=Mewshi;6219782]Is it an NTFS drive?
If so, first off, use something better :P
Second, you should be able to run a command to fix the filesystem, which should help.

If you need further help, run 'dmesg' and give us everything related to the drive.[/QUOTE








Okay Here it is, I tried doing what ya guys did and it wont work. Yes
drive is in ntfs. I wont use other format because I use windows too, 
and most of my friend use windows so if i go to any of their house, and
its in some type of linux partition, their computer probably wont reconize. Anyways here is the info. 







[    0.560585] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.560592] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.560677] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.560766] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.560774] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.560782] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.560790] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.560798] PCI: 0000:00:1f.1 reg 20 io port: [1880, 188f]
[    0.560873] PCI: 0000:00:1f.3 reg 20 io port: [18a0, 18bf]
[    0.560942] PCI: 0000:01:00.0 reg 10 32bit mmio: [a0000000, a0ffffff]
[    0.560950] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, cfffffff]
[    0.560968] PCI: 0000:01:00.0 reg 1c 64bit mmio: [90000000, 90ffffff]
[    0.560981] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.561047] PCI: bridge 0000:00:01.0 32bit mmio: [90000000, afffffff]
[    0.561051] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, cfffffff]
[    0.561116] PCI: 0000:06:03.0 reg 10 32bit mmio: [0, fff]
[    0.561141] pci 0000:06:03.0: supports D1
[    0.561142] pci 0000:06:03.0: supports D2
[    0.561145] pci 0000:06:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.561220] pci 0000:06:03.0: PME# disabled
[    0.561336] PCI: 0000:06:03.2 reg 10 32bit mmio: [b0004000, b00047ff]
[    0.561347] PCI: 0000:06:03.2 reg 14 32bit mmio: [b0000000, b0003fff]
[    0.561416] pci 0000:06:03.2: supports D1
[    0.561418] pci 0000:06:03.2: supports D2
[    0.561420] pci 0000:06:03.2: PME# supported from D0 D1 D2 D3hot
[    0.561494] pci 0000:06:03.2: PME# disabled
[    0.561607] PCI: 0000:06:03.3 reg 10 32bit mmio: [b0005000, b0005fff]
[    0.561685] pci 0000:06:03.3: supports D1
[    0.561687] pci 0000:06:03.3: supports D2
[    0.561689] pci 0000:06:03.3: PME# supported from D0 D1 D2 D3hot
[    0.561764] pci 0000:06:03.3: PME# disabled
[    0.561885] PCI: 0000:06:04.0 reg 10 32bit mmio: [b0006000, b0006fff]
[    0.561964] pci 0000:06:04.0: PME# supported from D0 D3hot D3cold
[    0.562038] pci 0000:06:04.0: PME# disabled
[    0.562156] PCI: 0000:06:08.0 reg 10 32bit mmio: [b0007000, b0007fff]
[    0.562167] PCI: 0000:06:08.0 reg 14 io port: [2000, 203f]
[    0.562234] pci 0000:06:08.0: supports D1
[    0.562236] pci 0000:06:08.0: supports D2
[    0.562238] pci 0000:06:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.562314] pci 0000:06:08.0: PME# disabled
[    0.562429] pci 0000:00:1e.0: transparent bridge
[    0.562500] PCI: bridge 0000:00:1e.0 io port: [2000, 2fff]
[    0.562505] PCI: bridge 0000:00:1e.0 32bit mmio: [b0000000, b00fffff]
[    0.562548] bus 00 -> node 0
[    0.562555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.562970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.563144] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.568478] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.569315] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.570089] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.570861] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.571695] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.572474] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.573362] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.574248] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.575187] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.575291] pnp: PnP ACPI init
[    0.575363] ACPI: bus type pnp registered
[    0.577773] pnp: PnP ACPI: found 8 devices
[    0.577842] ACPI: ACPI bus type pnp unregistered
[    0.577910] PnPBIOS: Disabled by ACPI PNP
[    0.578313] PCI: Using ACPI for IRQ routing
[    0.578513] NET: Registered protocol family 8
[    0.578513] NET: Registered protocol family 20
[    0.578513] NetLabel: Initializing
[    0.578513] NetLabel:  domain hash size = 128
[    0.580033] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.580112] NetLabel:  unlabeled traffic allowed by default
[    0.580302] hpet clockevent registered
[    0.580308] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.580576] hpet0: 3 64-bit timers, 14318180 Hz
[    0.582158] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.582230]    actual entries 65620
[    0.582374] AppArmor: AppArmor Filesystem Enabled
[    0.582465] ACPI: RTC can wake from S4
[    0.582539] system 00:04: ioport range 0x380-0x383 has been reserved
[    0.582539] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.582539] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.582539] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.582539] system 00:04: ioport range 0x1640-0x164f has been reserved
[    0.582539] system 00:04: iomem range 0xf0008000-0xf000bfff could not be reserved
[    0.582539] system 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[    0.582539] system 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[    0.584036] system 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[    0.584117] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.619235] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.619307] pci 0000:00:01.0:   IO window: disabled
[    0.619377] pci 0000:00:01.0:   MEM window: 0x90000000-0xafffffff
[    0.619446] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.619536] pci 0000:06:03.0: CardBus bridge, secondary bus 0000:07
[    0.619605] pci 0000:06:03.0:   IO window: 0x002400-0x0024ff
[    0.619678] pci 0000:06:03.0:   IO window: 0x002800-0x0028ff
[    0.619750] pci 0000:06:03.0:   PREFETCH window: 0x88000000-0x8bffffff
[    0.619824] pci 0000:06:03.0:   MEM window: 0x8c000000-0x8fffffff
[    0.619896] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.619966] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.620047] pci 0000:00:1e.0:   MEM window: 0xb0000000-0xb00fffff
[    0.620119] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.620213] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.620287] pci 0000:00:01.0: setting latency timer to 64
[    0.620294] pci 0000:00:1e.0: setting latency timer to 64
[    0.620306] pci 0000:06:03.0: enabling device (0000 -> 0003)
[    0.620379] pci 0000:06:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.620455] bus: 00 index 0 io port: [0, ffff]
[    0.620521] bus: 00 index 1 mmio: [0, ffffffff]
[    0.620588] bus: 01 index 0 mmio: [0, 0]
[    0.620653] bus: 01 index 1 mmio: [90000000, afffffff]
[    0.620721] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.620788] bus: 01 index 3 mmio: [0, 0]
[    0.620854] bus: 06 index 0 io port: [2000, 2fff]
[    0.620920] bus: 06 index 1 mmio: [b0000000, b00fffff]
[    0.620988] bus: 06 index 2 mmio: [88000000, 8bffffff]
[    0.621055] bus: 06 index 3 io port: [0, ffff]
[    0.621122] bus: 06 index 4 mmio: [0, ffffffff]
[    0.621189] bus: 07 index 0 io port: [2400, 24ff]
[    0.621255] bus: 07 index 1 io port: [2800, 28ff]
[    0.621322] bus: 07 index 2 mmio: [88000000, 8bffffff]
[    0.621389] bus: 07 index 3 mmio: [8c000000, 8fffffff]
[    0.621462] NET: Registered protocol family 2
[    0.621652] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.621957] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.622685] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.623159] TCP: Hash tables configured (established 131072 bind 65536)
[    0.623233] TCP reno registered
[    0.623445] NET: Registered protocol family 1
[    0.623645] checking if image is initramfs... it is
[    1.084071] Switched to high resolution mode on CPU 0
[    1.354954] Freeing initrd memory: 7916k freed
[    1.355255] Simple Boot Flag at 0x36 set to 0x1
[    1.355855] audit: initializing netlink socket (disabled)
[    1.355944] type=2000 audit(1227188963.352:1): initialized
[    1.362713] highmem bounce pool size: 64 pages
[    1.362789] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.365290] VFS: Disk quotas dquot_6.5.1
[    1.365449] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.365644] msgmni has been set to 1743
[    1.365845] io scheduler noop registered
[    1.365914] io scheduler anticipatory registered
[    1.365981] io scheduler deadline registered
[    1.366057] io scheduler cfq registered (default)
[    1.366245] pci 0000:01:00.0: Boot video device
[    1.366268] pci 0000:06:08.0: Firmware left e100 interrupts enabled; disabling
[    1.366447] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.366477] pcieport-driver 0000:00:01.0: found MSI capability
[    1.366574] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.366622] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.366929] isapnp: Scanning for PnP cards...
[    1.721879] isapnp: No Plug & Play device found
[    1.757519] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.759867] brd: module loaded
[    1.760314] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.760516] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.763679] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.767592] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.767665] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.767733] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.767801] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.767867] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.768388] mice: PS/2 mouse device common for all mice
[    1.768600] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.768700] rtc0: alarms up to one month, y3k, hpet irqs
[    1.768890] EISA: Probing bus 0 at eisa.0
[    1.768965] Cannot allocate resource for EISA slot 1
[    1.769032] Cannot allocate resource for EISA slot 2
[    1.769126] EISA: Detected 0 cards.
[    1.769195] cpuidle: using governor ladder
[    1.769262] cpuidle: using governor menu
[    1.769844] TCP cubic registered
[    1.769938] Using IPI No-Shortcut mode
[    1.770188] registered taskstats version 1
[    1.770373]   Magic number: 0:699:837
[    1.770515] tty ptyu3: hash matches
[    1.770659] rtc_cmos 00:05: setting system clock to 2008-11-20 13:49:24 UTC (1227188964)
[    1.770744] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.770812] EDD information not available.
[    1.771120] Freeing unused kernel memory: 424k freed
[    1.771238] Write protecting the kernel text: 2576k
[    1.771335] Write protecting the kernel read-only data: 936k
[    1.872608] fuse init (API version 7.9)
[    1.970901] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.896269] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.896538] processor ACPI0007:00: registered as cooling_device0
[    2.896611] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.899445] Marking TSC unstable due to TSC halts in idle
[    2.900024] thermal LNXTHERM:01: registered as thermal_zone0
[    2.902153] ACPI: Thermal Zone [THRM] (52 C)
[    3.423162] usbcore: registered new interface driver usbfs
[    3.423263] usbcore: registered new interface driver hub
[    3.423685] usbcore: registered new device driver usb
[    3.426131] USB Universal Host Controller Interface driver v3.0
[    3.429024] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.429106] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.429111] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.429227] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.429344] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    3.429599] usb usb1: configuration #1 chosen from 1 choice
[    3.429697] hub 1-0:1.0: USB hub found
[    3.429771] hub 1-0:1.0: 2 ports detected
[    3.460180] No dock devices found.
[    3.520225] SCSI subsystem initialized
[    3.530972] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    3.531046] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.566055] libata version 3.00 loaded.
[    3.636362] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.636446] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.636451] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.636543] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.636660] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    3.636829] usb usb2: configuration #1 chosen from 1 choice
[    3.636925] hub 2-0:1.0: USB hub found
[    3.636999] hub 2-0:1.0: 2 ports detected
[    3.740358] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.740443] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.740447] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.740538] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.740654] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    3.740817] usb usb3: configuration #1 chosen from 1 choice
[    3.740915] hub 3-0:1.0: USB hub found
[    3.740988] hub 3-0:1.0: 2 ports detected
[    3.748024] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.844364] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.844449] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.844453] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.844544] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.844661] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    3.844825] usb usb4: configuration #1 chosen from 1 choice
[    3.844922] hub 4-0:1.0: USB hub found
[    3.844994] hub 4-0:1.0: 2 ports detected
[    3.911574] usb 1-1: configuration #1 chosen from 1 choice
[    3.948468] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.948560] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.948564] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.948657] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.954420] ehci_hcd 0000:00:1d.7: debug port 1
[    3.954494] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.954502] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x80004000
[    3.968023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.968208] usb usb5: configuration #1 chosen from 1 choice
[    3.968305] hub 5-0:1.0: USB hub found
[    3.968377] hub 5-0:1.0: 8 ports detected
[    4.080021] Clocksource tsc unstable (delta = -86399683 ns)
[    4.120084] usb 1-1: USB disconnect, address 2
[    4.177262] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.177378] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    4.177393] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    4.177509] e100 0000:06:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.210090] e100 0000:06:08.0: PME# disabled
[    4.211842] e100: eth0: e100_probe: addr 0xb0007000, irq 20, MAC addr 00:01:4a:c0:cb:b0
[    4.211968] ohci1394 0000:06:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.261801] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0004000-b00047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.269058] ata_piix 0000:00:1f.1: version 2.12
[    4.269071] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.269181] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.269774] scsi0 : ata_piix
[    4.270093] scsi1 : ata_piix
[    4.270907] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    4.270980] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    4.404036] usb 5-1: new high speed USB device using ehci_hcd and address 2
[    4.440648] ata1.00: ATA-6: TOSHIBA MK1233GAS, AA011A, max UDMA/100
[    4.440721] ata1.00: 234441648 sectors, multi 16: LBA48 
[    4.440806] ata1.01: ATAPI: MATSHITAUJ-840D, 1.01, max UDMA/33
[    4.448568] ata1.00: configured for UDMA/100
[    4.464538] ata1.01: configured for UDMA/33
[    4.464651] ata2: port disabled. ignoring.
[    4.464775] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1233GA AA01 PQ: 0 ANSI: 5
[    4.466797] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.01 PQ: 0 ANSI: 5
[    4.476809] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.476919] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.495427] Driver 'sd' needs updating - please use bus_type methods
[    4.495611] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.495705] sd 0:0:0:0: [sda] Write Protect is off
[    4.495775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.495813] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.495973] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.496084] sd 0:0:0:0: [sda] Write Protect is off
[    4.496154] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.496198] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.496284]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.531996]  sda1 sda2 <<6>usb 5-1: configuration #1 chosen from 1 choice
[    4.548884] usbcore: registered new interface driver libusual
[    4.556511] Initializing USB Mass Storage driver...
[    4.558503]  sda5<6>scsi2 : SCSI emulation for USB Mass Storage devices
[    4.562240] usbcore: registered new interface driver usb-storage
[    4.562314] USB Mass Storage support registered.
[    4.562466] usb-storage: device found at 2
[    4.562469] usb-storage: waiting for device to settle before scanning
[    4.572520]  sda6 sda7 >
[    4.596143] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.603250] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.603327] Uniform CD-ROM driver Revision: 3.20
[    4.603474] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.031717] PM: Starting manual resume from disk
[    5.031786] PM: Resume from partition 8:7
[    5.031788] PM: Checking hibernation image.
[    5.032016] PM: Resume from disk failed.
[    5.082408] kjournald starting.  Commit interval 5 seconds
[    5.082493] EXT3-fs: mounted filesystem with ordered data mode.
[    5.532145] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301e76a88]
[    9.560199] usb-storage: device scan complete
[    9.563554] scsi 2:0:0:0: Direct-Access     TOSHIBA  MK2546GSX             PQ: 0 ANSI: 2
[    9.564908] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    9.567281] sd 2:0:0:0: [sdb] Write Protect is off
[    9.567352] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[    9.567355] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.568406] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    9.570782] sd 2:0:0:0: [sdb] Write Protect is off
[    9.570850] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[    9.570853] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.570922]  sdb: sdb1 < sdb5 >
[   11.818204] sd 2:0:0:0: [sdb] Attached SCSI disk
[   11.818420] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   14.296622] udevd version 124 started
[   15.098686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.141905] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.293764] Linux agpgart interface v0.103
[   15.376768] iTCO_vendor_support: vendor-support=0
[   15.426784] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   15.426971] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   15.427064] iTCO_wdt: No card detected
[   15.639382] intel_rng: FWH not detected
[   15.735576] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   15.744027] ACPI: Power Button (FF) [PWRF]
[   15.744165] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   15.745190] ACPI: Lid Switch [LID0]
[   15.745310] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   15.760046] ACPI: Power Button (CM) [PWRB]
[   15.761930] ACPI: AC Adapter [ADP1] (on-line)
[   15.836310] ACPI: Battery Slot [BAT0] (battery present)
[   16.308580] nvidia: module license 'NVIDIA' taints kernel.
[   16.900600] Yenta: CardBus bridge found at 0000:06:03.0 [104d:818f]
[   16.900702] Yenta: Enabling burst memory read transactions
[   16.900776] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.900844] Yenta: Routing CardBus interrupts to PCI
[   16.900915] Yenta TI: socket 0000:06:03.0, mfunc 0x01001b22, devctl 0x64
[   17.067493] ieee80211_crypt: registered algorithm 'NULL'
[   17.115218] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.115295] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.132853] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   17.132929] Socket status: 30000006
[   17.132995] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   17.133082] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   17.133175] cs: IO port probe 0x2000-0x2fff: clean.
[   17.133514] pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xb00fffff
[   17.133585] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   17.284937] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input5
[   17.285157] tifm_7xx1 0000:06:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.296063] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   17.296891] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/input/input6
[   17.308030] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   17.308196] tifm_core: MMC/SD card detected in socket 0:0
[   17.435094] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.435183] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.435325] ipw2200 0000:06:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.447262] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.447395] firmware: requesting ipw2200-bss.fw
[   17.620656] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.620765] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.810879] sony-laptop: Sony Notebook Control Driver v0.6.
[   17.833888] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/SNY5001:00/input/input7
[   17.844097] input: Sony Vaio Jogdial as /devices/virtual/input/input8
[   18.683920] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   18.801254] input: PC Speaker as /devices/platform/pcspkr/input/input10
[   18.807827] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[   20.304612] cs: IO port probe 0x100-0x3af: clean.
[   20.307059] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.310731] cs: IO port probe 0x820-0x8ff: clean.
[   20.311664] cs: IO port probe 0xc00-0xcf7: clean.
[   20.312791] cs: IO port probe 0xa00-0xaff: clean.
[   20.595102] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   20.595313] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.595390] nvidia 0000:01:00.0: setting latency timer to 64
[   20.595569] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   21.298371] lp: driver loaded but no devices found
[   21.571210] Adding 1847432k swap on /dev/sda7.  Priority:-1 extents:1 across:1847432k
[   22.012708] EXT3 FS on sda6, internal journal
[   22.567725] type=1505 audit(1227217785.463:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4096
[   22.770239] type=1505 audit(1227217785.667:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4101
[   22.770490] type=1505 audit(1227217785.667:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4101
[   22.894901] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.965821] ACPI: WMI: Mapper loaded
[   32.220155] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   32.333554] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   32.333562] apm: overridden by ACPI.
[   32.551214] ppdev: user-space parallel port driver
[   35.842158] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   35.843310] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   35.845408] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   35.845416] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   35.845418] sonypi: device allocated minor is 60
[   35.848839] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input12
[   35.876122] input: Sony Vaio Keys as /devices/platform/sonypi/input/input13
[   35.955363] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
[   36.002847] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
[   36.050315] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
[   36.097777] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
[   36.337863] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   36.337871] vboxdrv: Successfully done.
[   36.337873] vboxdrv: Found 1 processor cores.
[   36.339293] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   36.339301] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   40.401896] Bluetooth: Core ver 2.13
[   40.404900] NET: Registered protocol family 31
[   40.404915] Bluetooth: HCI device and connection manager initialized
[   40.404922] Bluetooth: HCI socket layer initialized
[   40.512037] Bluetooth: L2CAP ver 2.11
[   40.512050] Bluetooth: L2CAP socket layer initialized
[   40.554220] Bluetooth: RFCOMM socket layer initialized
[   40.554657] Bluetooth: RFCOMM TTY layer initialized
[   40.554669] Bluetooth: RFCOMM ver 1.10
[   40.558202] Bluetooth: SCO (Voice Link) ver 0.6
[   40.558213] Bluetooth: SCO socket layer initialized
[   40.601582] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.601588] Bluetooth: BNEP filters: protocol multicast
[   40.824143] Bridge firewalling registered
[   40.826240] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   45.090908] NET: Registered protocol family 17
[   46.622370] NET: Registered protocol family 10
[   46.625603] lo: Disabled Privacy Extensions
[   46.628079] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   58.364037] eth1: no IPv6 routers present
[  100.840064] usb 3-1: new low speed USB device using uhci_hcd and address 2
[  101.028301] usb 3-1: configuration #1 chosen from 1 choice
[  101.229754] usbcore: registered new interface driver hiddev
[  101.262656] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input14
[  101.264935] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:1d.2-1
[  101.266442] usbcore: registered new interface driver usbhid
[  101.267241] usbhid: v2.6:USB HID core driver
[  537.148559] usb 5-1: USB disconnect, address 2
[  537.892066] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  538.051881] usb 5-1: configuration #1 chosen from 1 choice
[  538.082132] scsi3 : SCSI emulation for USB Mass Storage devices
[  538.086067] usb-storage: device found at 4
[  538.086078] usb-storage: waiting for device to settle before scanning
[  543.084213] usb-storage: device scan complete
[  543.088660] scsi 3:0:0:0: Direct-Access     TOSHIBA  MK2546GSX             PQ: 0 ANSI: 2
[  543.108532] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  543.111407] sd 3:0:0:0: [sdb] Write Protect is off
[  543.111420] sd 3:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  543.111426] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  543.113280] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  543.116161] sd 3:0:0:0: [sdb] Write Protect is off
[  543.116174] sd 3:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  543.116180] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  543.117052]  sdb: sdb1 < sdb5 >
[  545.060185] sd 3:0:0:0: [sdb] Attached SCSI disk
[  545.060749] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  616.206512] ipw2200: Firmware error detected.  Restarting.
jaime@jaime-laptop:~$

---

### Post by taurus on 2008-11-20
How about 

```
sudo fdisk -l
```

---

### Post by jcer93705 on 2008-11-20
> **taurus said:**
> How about 

```
sudo fdisk -l
```


jaime@jaime-laptop:~$ sudo fdisk -l
[sudo] password for jaime: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c695658

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7309    58708518+   7  HPFS/NTFS
/dev/sda2            7310       14593    58508730    f  W95 Ext'd (LBA)
/dev/sda5            7310        9128    14611086    7  HPFS/NTFS
/dev/sda6            9129       14363    42050106   83  Linux
/dev/sda7           14364       14593     1847443+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b9f3a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS
jaime@jaime-laptop:~$

---

### Post by taurus on 2008-11-20
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sdb5 /media/windows -o force
df -h
```

---

### Post by jcer93705 on 2008-11-20
> **taurus said:**
> ```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sdb5 /media/windows -o force
df -h
```

WOAH, thank you very much. Now  how do I  delete two ntfs partition that i have on this computer then add to my linux parttion For more space?

---

