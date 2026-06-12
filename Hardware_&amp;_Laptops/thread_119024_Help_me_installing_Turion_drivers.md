---
title: "Help me installing Turion drivers"
date: 2006-01-18
forum: Hardware &amp; Laptops
---

### Post by lzfy on 2006-01-18
Hi, i recently installed Ubuntu 5.10 on my Acer Aspire 5024 and all I can say is that i'm very impressed:KS

The only that bothers me is that my CPU is running @1.80 GHz. there's a driver on AMD's website for [http://www.amd.com/us-en/assets/content_type/utilities/PN_1_50_03.BZ2]("http://www.amd.com/us-en/assets/content_type/utilities/PN_1_50_03.BZ2")

I downloaded it but i have no idea what to do with it:???:  can someone please help me?

thanks...

> 
**AMD Turion™ 64 Mobile Technology PowerNow! Driver Version 1.50.03 Linux** - AMD Turion™ 64 Mobile Technology PowerNow! Driver Version 1.50.03 for Linux 2.6 series kernels. Provides support for AMD PowerNow! technology for Linux systems. Adds support for 2.6.10 and later kernels. Requires cpufreq-1.20, cpuspeed-1.20.1, or powersaved-0.8.19 or later to support SMP and dual-core systems.

---

### Post by Sef on 2006-01-18
You will need to compile from source.

A) Install build-essential from the terminal:  sudo apt-get install build-essential

B) Read psychocats.net:  [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")  Note: since the download is saved a bz2, you will need to untar it like this:  tar xvjf

---

### Post by lzfy on 2006-01-18
Ok i extractet the file with the tar xvjf command. now i have a folder with 3 folders in it with different version numbers. I assume that i have to take the folder with the latest version number. Now there are 2 files in that folder: powernow-k8.c and powernow-k8.h What do i have to do now? there's no make file or something elde.

please help :(

Edit- Here's the readme file of the driver.

> This tar file contains the Linux CPU frequency driver
for AMD Athlon64 / Opteron processors. 

The driver obtains data as to supported frequencies 
and voltages for the processor from the BIOS. 

Version 1.00.xx of the driver uses a BIOS table called 
the PSB, which is not supported by all BIOSs. Included
driver versions are:
1.00.09 - versions of the driver for both 2.4 and 2.6
          kernels. The driver is dependent on the
          cpufreq driver, which is available as a patch
          for 2.4 kernels, and is built into 2.6 kernels.
1.00.12 - the latest version of the driver, for 2.6
          only, that includes sample code to hardcode a
          PSB table to bypass BIOSs that do not offer
          the support.

Version 1.39.xx of the driver can use either the 
PSB table or ACPI objects, dependent on whether
the kernel is configured to include ACPI support or
not. The driver version included is 1.39.04, for
the 2.6 kernel only. This driver supports SMP
frequency management and dual-core processors.  It
will not load on an SMP or dual-core system unless
the ACPI objects are available.  It will work on
all 2.6 kernels, but the 1.50.03 driver (below) 
is preferred for kernels 2.6.10 and later.

Version 1.50.xx of the driver can use either the
PSB table of the ACPI objects.  It supports Opteron,
Athlon 64 processors, in both single and dual core
versions, for all of the 754, 939, 940, and 1207
pin packages.  This driver supports SMP frequency
management but will not work on SMP or dual core
systems unless the ACPI powerstate objects are
available.  It will only work on 2.6.10 and later
kernels.  This driver is distributed with the
2.6.13 and later kernels.

The powernow-k8.c and powernow-k8.h files should be 
placed in the arch/i386/kernel/cpu/cpufreq directory. 
The kernel will then need to be rebuilt and the system
rebooted.  Builds of the 64-bit arch/x86_64 kernel use 
the same source files.

For further documentation, see the 
linux/Documentation/cpu-freq directory.

Support: [email]mark.langsdorf@amd.com[/email]
License: GPL




---

### Post by hw-tph on 2006-01-19
Did you read what you posted?

> The powernow-k8.c and powernow-k8.h files should be
placed in the arch/i386/kernel/cpu/cpufreq directory.
The kernel will then need to be rebuilt and the system
rebooted. Builds of the 64-bit arch/x86_64 kernel use
the same source files.

For further documentation, see the
linux/Documentation/cpu-freq directory.

First download and untar the kernel sources (keep them in /usr/src/linux or /usr/local/src/linux) and then follow the instructions you posted. You might want to apt-get install kernel-package if you want to create a .deb for your new kernel (highly suggested).


H&#229;kan

---

### Post by lzfy on 2006-01-19
How do you rebuild a kernel? :confused: 

I'm sorry if this sounds stupid but i'm a complete noob :(

---

### Post by hw-tph on 2006-01-19
There are [instructions](https://wiki.ubuntu.com/KernelBuildpackageDetailedHowto) in the [Ubuntu wiki](http://wiki.ubuntu.com).

---

### Post by tokyovigilante on 2006-01-25
I don't think you need any of the above.

Surely 
```
modprobe powernow_k8 (which should already be built and installed with your kernel)
apt-get install powernowd
```

Should get your Cool'n'quiet running?

My Athlon64 X2 never shifts from 1007MHz, I should've just got a Sempron instead of blowing my dough ;)

---

### Post by lzfy on 2006-01-25
Thanks tokyovigilante but that didn't work for me, i'm gonna try to build a new kernel with the drivers ;)

---

### Post by tokyovigilante on 2006-01-26
[QUOTE=lzfy]Thanks tokyovigilante but that didn't work for me, i'm gonna try to build a new kernel with the drivers ;)[/QUOTE]
Thats odd...

What kernel version are you running? (uname -r)
What output does dmesg give?
What specifically didn't work for you? modprobing the module? Installing powernowd?

Try 
```
sudo slocate -u
locate powernow_k8
```
and post the output.

I really think recompiling the kernel should be a last resort, On the latest Dapper builds the powernow_k8 module is loaded without me having to do anything.

---

### Post by lzfy on 2006-01-26
> **tokyovigilante]Thats odd...

What kernel version are you running? (uname -r)[/QUOTE]
```
lzfy@UbuntuTurion:~$ uname -r
2.6.12-10-k7
```
> 
What output does dmesg give?
```
lzfy@UbuntuTurion:~$ dmesg
)
[4294671.055000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.063000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[4294671.063000] Boot video device is 0000:01:00.0
[4294671.065000] PCI: Transparent bridge - 0000:00:14.4
[4294671.071000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.073000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[4294671.073000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[4294671.073000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[4294671.073000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[4294671.075000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[4294671.075000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[4294671.075000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[4294671.075000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[4294671.077000] burst-mode-ec-10-Aug
[4294671.077000] ACPI: Embedded Controller [EC0] (gpe 3)
[4294671.155000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[4294671.155000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[4294671.157000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[4294671.157000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[4294671.157000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.157000] pnp: PnP ACPI init
[4294671.173000] pnp: PnP ACPI: found 10 devices
[4294671.173000] PnPBIOS: Disabled by ACPI PNP
[4294671.173000] PCI: Using ACPI for IRQ routing
[4294671.173000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294671.219000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[4294671.219000] pnp: 00:07: ioport range 0x1200-0x120f has been reserved
[4294671.219000] pnp: 00:07: ioport range 0x500-0x51f has been reserved
[4294671.219000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[4294671.219000] audit: initializing netlink socket (disabled)
[4294671.219000] audit: initialized
[4294671.219000] VFS: Disk quotas dquot_6.5.1
[4294671.219000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.219000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.219000] devfs: boot_options: 0x0
[4294671.219000] Initializing Cryptographic API
[4294671.219000] PCI: 0000:00:02.0 has unsupported PM cap regs version (3)
[4294671.219000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294671.219000] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendo r BIOS
[4294671.219000] assign_interrupt_mode Found MSI capability
[4294671.219000] Allocate Port Service[pcie00]
[4294671.219000] PCI: 0000:00:06.0 has unsupported PM cap regs version (3)
[4294671.219000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294671.219000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendo r BIOS
[4294671.219000] assign_interrupt_mode Found MSI capability
[4294671.219000] Allocate Port Service[pcie00]
[4294671.219000] PCI: 0000:00:07.0 has unsupported PM cap regs version (3)
[4294671.219000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[4294671.219000] pcie_portdrv_probe->Dev[5a39:1002] has invalid IRQ. Check vendo r BIOS
[4294671.219000] assign_interrupt_mode Found MSI capability
[4294671.219000] Allocate Port Service[pcie00]
[4294671.221000] isapnp: Scanning for PnP cards...
[4294671.927000] isapnp: No Plug & Play device found
[4294671.957000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 i rq 1,12
[4294671.974000] i8042.c: Detected active multiplexing controller, rev 1.9.
[4294671.980000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294671.982000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294671.984000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294671.984000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294671.986000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.986000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shari ng enabled
[4294671.986000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.988000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> I RQ 17
[4294671.988000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[4294671.988000] io scheduler noop registered
[4294671.988000] io scheduler anticipatory registered
[4294671.988000] io scheduler deadline registered
[4294671.990000] io scheduler cfq registered
[4294671.990000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294671.990000] NET: Registered protocol family 2
[4294672.012000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294672.012000] TCP established hash table entries: 16384 (order: 5, 131072 byt es)
[4294672.012000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.012000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.012000] NET: Registered protocol family 8
[4294672.012000] NET: Registered protocol family 20
[4294672.012000] ACPI wakeup devices:
[4294672.012000] LID0 SLPB OHC1 OHC2 EHCI  P2P MODM
[4294672.012000] ACPI: (supports S0 S3 S4 S5)
[4294672.012000] Freeing unused kernel memory: 168k freed
[4294672.036000] vga16fb: initializing
[4294672.036000] vga16fb: mapped to 0xc00a0000
[4294672.310000] Console: switching to colour frame buffer device 80x30
[4294672.310000] fb0: VGA16 VGA frame buffer device
[4294673.661000] Capability LSM initialized
[4294673.677000] NET: Registered protocol family 1
[4294673.699000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.699000] ide: Assuming 33MHz system bus speed for PIO modes said:**
>  ACPI: bus type ide registered
[4294673.715000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[4294673.715000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> I RQ 16
[4294673.715000] ATIIXP: chipset revision 0
[4294673.715000] ATIIXP: not 100% native mode: will probe irqs later
[4294673.715000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb: pio
[4294673.715000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd: pio
[4294673.715000] Probing IDE interface ide0...
[4294674.001000] hda: HTS541010G9AT00, ATA DISK drive
[4294674.627000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.627000] Probing IDE interface ide1...
[4294675.321000] hdc: MATSHITAUJ-845D, ATAPI CD/DVD-ROM drive
[4294675.633000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.633000] Probing IDE interface ide2...
[4294676.157000] Probing IDE interface ide3...
[4294676.680000] Probing IDE interface ide4...
[4294677.203000] Probing IDE interface ide5...
[4294677.730000] hda: max request size: 1024KiB
[4294677.764000] hda: 195371568 sectors (100030 MB) w/7539KiB Cache, CHS=16383/2 55/63, UDMA(100)
[4294677.766000] hda: cache flushes supported
[4294677.766000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 >
[4294677.876000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.876000] Uniform CD-ROM driver Revision: 3.20
[4294678.309000] Attempting manual resume
[4294678.355000] swsusp: Suspend partition has wrong signature?
[4294678.443000] usbcore: registered new driver usbfs
[4294678.443000] usbcore: registered new driver hub
[4294678.445000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Dri ver (PCI)
[4294678.445000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> I RQ 19
[4294678.445000] ohci_hcd 0000:00:13.0: PCI device 1002:4374 (ATI Technologies I nc)
[4294678.660000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus num ber 1
[4294678.660000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[4294678.720000] hub 1-0:1.0: USB hub found
[4294678.720000] hub 1-0:1.0: 4 ports detected
[4294678.726000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> I RQ 19
[4294678.726000] ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies I nc)
[4294678.941000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus num ber 2
[4294678.941000] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[4294679.001000] hub 2-0:1.0: USB hub found
[4294679.001000] hub 2-0:1.0: 4 ports detected
[4294679.033000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> I RQ 19
[4294679.033000] ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies I nc)
[4294679.033000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus num ber 3
[4294679.033000] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[4294679.033000] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294679.033000] hub 3-0:1.0: USB hub found
[4294679.033000] hub 3-0:1.0: 8 ports detected
[4294679.261000] r8169 Gigabit Ethernet driver 2.2LK loaded
[4294679.261000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 23 (level, low) -> I RQ 23
[4294679.263000] eth0: Identified chip type is 'RTL8169s/8110s'.
[4294679.263000] eth0: RTL8169 at 0xe0898400, 00:0a:e4:e1:a1:55, IRQ 23
[4294679.461000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[4294681.315000] usbcore: registered new driver hiddev
[4294681.327000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on  usb-0000:00:13.0-1
[4294681.327000] usbcore: registered new driver usbhid
[4294681.327000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294682.055000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294682.151000] ACPI: Thermal Zone [TZS0] (60 C)
[4294682.247000] ACPI: Thermal Zone [TZS1] (51 C)
[4294682.347000] ACPI: Thermal Zone [TZSV] (55 C)
[4294682.933000] Attempting manual resume
[4294682.961000] swsusp: Suspend partition has wrong signature?
[4294683.043000] kjournald starting.  Commit interval 5 seconds
[4294683.043000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.999000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294690.579000] Adding 1020088k swap on /dev/hda5.  Priority:-1 extents:1
[4294691.119000] EXT3 FS on hda2, internal journal
[4294702.341000] lp: driver loaded but no devices found
[4294702.405000] mice: PS/2 mouse device common for all mice
[4294702.467000] ieee1394: Initialized config rom entry `ip1394'
[4294702.477000] SCSI subsystem initialized
[4294702.483000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294702.557000] Linux agpgart interface v0.101 (c) Dave Jones
[4294702.593000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies , Starnberg, GERMANY' taints kernel.
[4294702.599000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294702.599000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> I RQ 18
[4294702.599000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294703.761000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa0 4713/0x204000
[4294703.765000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[4294703.833000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[4294704.135000] ts: Compaq touchscreen protocol output
[4294709.239000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294711.133000] cdrom: open failed.
[4294712.451000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294712.541000] NTFS volume version 3.1.
[4294712.621000] NTFS volume version 3.1.
[4294716.267000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294716.297000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294717.171000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> I RQ 17
[4294719.001000] Linux Kernel Card Services
[4294719.001000]   options:  [pci] [cardbus] [pm]
[4294719.021000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> I RQ 20
[4294719.021000] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080]
[4294719.021000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294719.021000] Yenta: Routing CardBus interrupts to PCI
[4294719.021000] Yenta TI: socket 0000:06:06.0, mfunc 0x010a1b22, devctl 0x64
[4294719.243000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20
[4294719.243000] Socket status: 30000006
[4294719.419000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294719.419000] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 22 (level, low) -> I RQ 22
[4294719.527000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c02080 00-c02087ff]  Max Packet=[2048]
[4294720.789000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[1234567812345678]
[4294721.779000] Real Time Clock Driver v1.12
[4294721.853000] input: PC Speaker
[4294722.811000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294722.855000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1792);  check system log for messages from 'loadndisdriver'
[4294723.459000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294723.461000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1792);  check system log for messages from 'loadndisdriver'
[4294723.563000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294723.567000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1792);  check system log for messages from 'loadndisdriver'
[4294723.599000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294723.605000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1792);  check system log for messages from 'loadndisdriver'
[4294723.641000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294723.643000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1792);  check system log for messages from 'loadndisdriver'
[4294723.677000] NET: Registered protocol family 17
[4294723.717000] r8169: eth0: link up
[4294735.673000] NET: Registered protocol family 10
[4294735.673000] Disabled Privacy Extensions on device c0321b80(lo)
[4294735.673000] IPv6 over IPv4 tunneling driver
[4294737.915000] ACPI: AC Adapter [ADP1] (on-line)
[4294738.003000] ACPI: Battery Slot [BAT0] (battery absent)
[4294738.033000] ACPI: Power Button (FF) [PWRF]
[4294738.033000] ACPI: Lid Switch [LID0]
[4294738.033000] ACPI: Sleep Button (CM) [SLPB]
[4294738.209000] ibm_acpi: ec object not found
[4294738.401000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294738.401000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294746.107000] eth0: no IPv6 routers present
[4294752.111000] apm: BIOS not found.
[4294752.555000] ip_tables: (C) 2000-2002 Netfilter core team
[4294752.609000] ip_conntrack version 2.1 (4085 buckets, 32680 max) - 248 bytes per conntrack
[4294755.107000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294755.115000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc1 7 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294755.117000] cs: IO port probe 0xa00-0xaff: clean.
[4294755.473000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (versio n 1.40.4)
[4294755.473000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4 (1450 mV)
[4294755.473000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[4294755.473000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[4294755.473000] cpu_init done, current fid 0xa, vid 0x4
[4294756.789000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294756.985000] Bluetooth: Core ver 2.7
[4294756.985000] NET: Registered protocol family 31
[4294756.985000] Bluetooth: HCI device and connection manager initialized
[4294756.985000] Bluetooth: HCI socket layer initialized
[4294757.007000] Bluetooth: L2CAP ver 2.7
[4294757.007000] Bluetooth: L2CAP socket layer initialized
[4294757.031000] Bluetooth: RFCOMM ver 1.5
[4294757.031000] Bluetooth: RFCOMM socket layer initialized
[4294757.031000] Bluetooth: RFCOMM TTY layer initialized
[4294990.095000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched .

```

> 
What specifically didn't work for you? modprobing the module? Installing powernowd?


Well I did both what you said but my CPU still runs at 100% speed (1.80GHZ) In Windows i can install the driver and everything works (runs at 700MHz when idle) When i try to install the powernowd i get the message that i already have it installed, and when i do that other thing nothing happens.
[QUOTE]
Try 
```
sudo slocate -u
locate powernow_k8
```
and post the output.


```
lzfy@UbuntuTurion:~$ sudo slocate -u locate powernow_k8
lzfy@UbuntuTurion:~$

```
As you can see i have no output when i type that command, the console waits about 3-4 minuts and then nothing happens.
> 
I really think recompiling the kernel should be a last resort, On the latest Dapper builds the powernow_k8 module is loaded without me having to do anything.

I'm running 5.10, does that make any difference?

---

### Post by tokyovigilante on 2006-01-27
[QUOTE=lzfy]```
lzfy@UbuntuTurion:~$ uname -r
2.6.12-10-k7
```[/QUOTE]
I see the problem. You're running a 32-bit Athlon XP/Sempron kernel (which is fine and compatible with your hardware) but trying to load a 64-bit kernel extension (-k7 kernel vs -k8 driver).

[QUOTE=lzfy]When i try to install the powernowd i get the message that i already have it installed, and when i do that other thing nothing happens.


```
lzfy@UbuntuTurion:~$ sudo slocate -u locate powernow_k8
lzfy@UbuntuTurion:~$

```
As you can see i have no output when i type that command, the console waits about 3-4 minuts and then nothing happens.[/QUOTE]
That's because sudo slocate -u and locate powernow_k8 are separate commands.
Try:
```
sudo slocate -u (updates LOCATE database)
locate powernow_k7 (searches for powernow_k7 32-bit extension)
locate powernow_k8 (searches for powernow_k8 64-bit extension)

```
[QUOTE=lzfy]
I'm running 5.10, does that make any difference?[/QUOTE]
No, but 5.10 doesn't always automatically enable power management.

Hopefully you have one or other of the above powernow kernel extensions on your system. If so, sudo modprobe it, and then
```
sudo invoke-rc.d powernowd restart
```
which will restart the CPU frequency scaler.
Hopefully then a 
```
cat /proc/cpuinfo
``` 
will show dynamic scaling.

If not, let me know.

---

