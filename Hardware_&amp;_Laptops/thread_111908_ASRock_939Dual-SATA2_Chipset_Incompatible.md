---
title: "ASRock 939Dual-SATA2 Chipset Incompatible?"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by KRiSX on 2006-01-03
hey hey

in my quest to finally move over to linux from windows... i have noticed a rather annoying problem or 2 with my hardware...

first was the network card... onboard doesn't work with 5.10... solved by putting in a second card... something i didn't want to do...

second... couldn't get surround sound working with the onboard sound card... unable to solve... which isn't that big of a deal seeing as it doesn't work in every app in windows anyway...

third... and this is the killer... the very poor performance access hard drives and cd roms... i have a feeling this comes down to lack of drivers for the chipset used on this motherboard... the worst was when copying files from a cd to my hdd... everything was painfully slow... i've never noticed this before on older machines i have, i am going to do some testing (i have 2 other ubuntu 5.04 boxes that i can test on) but yeah... this has forced me to stay with windows a little longer of my main system...

if anyone else has experienced this or knows a way to fix it... please let me know!

---

### Post by KRiSX on 2006-01-03
it does seem to slow down a bit on my 5.04 box too... maybe its just how it is... just bugs me that i don't notice such slow downs in windows...

could it be gnome that does it? maybe i should try going back to kde... its been a while since i've used it

---

### Post by SpaceTrapper on 2006-01-04
i just read this and thought i might be able to help:

im getting a ASRock 939Dual-SATA2 and its got a ULi 1695 chipset. Accidentally i found this numbers flying over the changelog for the latest 2.6.15 kernel and it said they included support for it in that release. I cant tell you for sure cause i havent tried it (but im gonna test it for myself soon, should get the new board in a few days together with a bunch of nice other parts :D ) but upgrading to this release might fix your problems. I'll be using Kubuntu Flight 2 for Amd64, that should give you the right kernel since flight 2 already has 2.6.15

---

### Post by KRiSX on 2006-01-04
ah very nice... i might give that a go!

if i don't get around to it, can you please report how you go with your system?

i was thinking that a newer kernel would fix it... but i didn't want to waste my time if someone else had already tried.. lol and i have since taken ubuntu off this system to test various other things (i try out many many dists lol).

but i would def like to put it back on to see what happens, might download the flight 2 iso and try that instead of 5.10

---

### Post by SpaceTrapper on 2006-01-04
i tried a bunch of distros, but i got stuck with kubuntu, even though i gotta admit my best working install is broken right now^^
as i said i haven tried it but probably will soon, ill post here when i have.
the testing release is maybe not the best for getting a stable system to work with the board but i like the bleeding edge :D

---

### Post by GameManK on 2006-01-07
[QUOTE=SpaceTrapper]i just read this and thought i might be able to help:

im getting a ASRock 939Dual-SATA2 and its got a ULi 1695 chipset. Accidentally i found this numbers flying over the changelog for the latest 2.6.15 kernel and it said they included support for it in that release. I cant tell you for sure cause i havent tried it (but im gonna test it for myself soon, should get the new board in a few days together with a bunch of nice other parts :D ) but upgrading to this release might fix your problems. I'll be using Kubuntu Flight 2 for Amd64, that should give you the right kernel since flight 2 already has 2.6.15[/QUOTE]
I thought using the dapper flight 2 cd would work too, but it doesn't for me.  See my thread [here]("http://ubuntuforums.org/showthread.php?t=112001").

When you get your board, tell me if you have any luck with it or any ideas. thx.  i still have to try the i386 version just in case that's the problem.

---

### Post by Amon_Re on 2006-01-07
[QUOTE=KRiSX]hey hey

in my quest to finally move over to linux from windows... i have noticed a rather annoying problem or 2 with my hardware...

first was the network card... onboard doesn't work with 5.10... solved by putting in a second card... something i didn't want to do...

second... couldn't get surround sound working with the onboard sound card... unable to solve... which isn't that big of a deal seeing as it doesn't work in every app in windows anyway...

third... and this is the killer... the very poor performance access hard drives and cd roms... i have a feeling this comes down to lack of drivers for the chipset used on this motherboard... the worst was when copying files from a cd to my hdd... everything was painfully slow... i've never noticed this before on older machines i have, i am going to do some testing (i have 2 other ubuntu 5.04 boxes that i can test on) but yeah... this has forced me to stay with windows a little longer of my main system...

if anyone else has experienced this or knows a way to fix it... please let me know![/QUOTE]

Could you post your dmesg output, and the results for the following commands:

sudo hdparm /dev/dvd
sudo hdparm /dev/hda

---

### Post by GameManK on 2006-01-08
[QUOTE=GameManK]I thought using the dapper flight 2 cd would work too, but it doesn't for me.  See my thread [here]("http://ubuntuforums.org/showthread.php?t=112001").

When you get your board, tell me if you have any luck with it or any ideas. thx.  i still have to try the i386 version just in case that's the problem.[/QUOTE]
no luck with the i386 installer either.  I tried doing the expert install which lets you choose a module, but nothing uli is listed there.

---

### Post by KRiSX on 2006-01-08
ok i managed to get the onboard surround sound working... was quite easy.. just had to play around with alsamixer settings...

haven't really played with the network... currently have suse 10.0 installed just to see if it performs any different... mind you i'm using the x64 version... i am going to install kubuntu again on this machine (i386 cause i need flash to work easily etc etc)... and i'll do the things amon_re said and post my output

so yeah main things of concern now are the network not working (i'm guessing this will be fixed in a newer kernel? and the possible lack of proper ide support... which i'm not 100% sure on yet

---

### Post by KRiSX on 2006-01-08
[QUOTE=Amon_Re]Could you post your dmesg output, and the results for the following commands:

sudo hdparm /dev/dvd
sudo hdparm /dev/hda[/QUOTE]

here is the output

> krisx@<hostremoved>:~$ sudo hdparm /dev/dvd
Password:

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
krisx@<hostremoved>:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 234493056, start = 0
krisx@<hostremoved>:~$

---

### Post by KRiSX on 2006-01-08
here is the dmesg output

> krisx@<hostremoved>:~$ dmesg
00] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294668.732000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.744000] Memory: 1030796k/1048256k available (1415k kernel code, 16524k reserved, 763k data, 224k init, 130752k highmem)
[4294668.744000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.744000] Calibrating delay loop... 4816.89 BogoMIPS (lpj=2408448)
[4294668.768000] Security Framework v1.0.0 initialized
[4294668.768000] SELinux:  Disabled at boot.
[4294668.768000] Mount-cache hash table entries: 512
[4294668.768000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294668.768000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294668.768000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294668.768000] CPU: L2 Cache: 512K (64 bytes/line)
[4294668.768000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000010 00000001 00000000 00000001
[4294668.768000] CPU: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[4294668.768000] Enabling fast FPU save and restore... done.
[4294668.768000] Enabling unmasked SIMD FPU exception support... done.
[4294668.768000] Checking 'hlt' instruction... OK.
[4294668.772000] Checking for popad bug... OK.
[4294668.772000] checking if image is initramfs... it is
[4294669.065000] Freeing initrd memory: 4824k freed
[4294669.065000] ACPI: Looking for DSDT in initrd... not found!
[4294669.103000]  not found!
[4294669.109000] ENABLING IO-APIC IRQs
[4294669.109000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294669.220000] NET: Registered protocol family 16
[4294669.220000] EISA bus registered
[4294669.220000] ACPI: bus type pci registered
[4294669.220000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[4294669.220000] PCI: Using configuration type 1
[4294669.220000] mtrr: v2.0 (20020519)
[4294669.220000] ACPI: Subsystem revision 20050729
[4294669.225000] ACPI: Interpreter enabled
[4294669.225000] ACPI: Using IOAPIC for interrupt routing
[4294669.225000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.225000] PCI: Probing PCI hardware (bus 00)
[4294669.225000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.227000] Boot video device is 0000:03:00.0
[4294669.227000] PCI: Transparent bridge - 0000:00:06.0
[4294669.237000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.237000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[4294669.238000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
[4294669.242000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB1._PRT]
[4294669.242000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB2._PRT]
[4294669.243000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294669.243000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294669.243000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[4294669.243000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15), disabled.
[4294669.243000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294669.244000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294669.244000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294669.244000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[4294669.244000] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294669.244000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.244000] pnp: PnP ACPI init
[4294669.248000] pnp: PnP ACPI: found 14 devices
[4294669.248000] PnPBIOS: Disabled by ACPI PNP
[4294669.248000] PCI: Using ACPI for IRQ routing
[4294669.248000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.254000] pnp: 00:0c: ioport range 0x290-0x29f has been reserved
[4294669.254000] audit: initializing netlink socket (disabled)
[4294669.254000] audit: initialized
[4294669.254000] highmem bounce pool size: 64 pages
[4294669.254000] VFS: Disk quotas dquot_6.5.1
[4294669.254000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.254000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.254000] devfs: boot_options: 0x0
[4294669.254000] Initializing Cryptographic API
[4294669.254000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 29 (level, low) -> IRQ 29
[4294669.254000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.254000] assign_interrupt_mode Found MSI capability
[4294669.254000] Allocate Port Service[pcie00]
[4294669.254000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 34 (level, low) -> IRQ 34
[4294669.254000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294669.254000] assign_interrupt_mode Found MSI capability
[4294669.254000] Allocate Port Service[pcie00]
[4294669.254000] isapnp: Scanning for PnP cards...
[4294669.608000] isapnp: No Plug & Play device found
[4294669.618000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294669.620000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.620000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.620000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.620000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.621000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.621000] io scheduler noop registered
[4294669.621000] io scheduler anticipatory registered
[4294669.621000] io scheduler deadline registered
[4294669.621000] io scheduler cfq registered
[4294669.622000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.622000] EISA: Probing bus 0 at eisa.0
[4294669.622000] EISA: Detected 0 cards.
[4294669.622000] NET: Registered protocol family 2
[4294669.631000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294669.631000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294669.632000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.632000] TCP: Hash tables configured (established 262144 bind 65536)
[4294669.632000] NET: Registered protocol family 8
[4294669.632000] NET: Registered protocol family 20
[4294669.632000] ACPI wakeup devices:
[4294669.632000]  HTT PS2K PS2M UAR1 AC97 MC97  LAN USB0 USB1 USB2 UB20 PEB1 PEB2 PEB3
[4294669.632000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.632000] Freeing unused kernel memory: 224k freed
[4294669.643000] vga16fb: initializing
[4294669.643000] vga16fb: mapped to 0xc00a0000
[4294669.846000] Console: switching to colour frame buffer device 80x30
[4294669.846000] fb0: VGA16 VGA frame buffer device
[4294669.860000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.022000] Capability LSM initialized
[4294671.030000] NET: Registered protocol family 1
[4294671.039000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.039000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.039000] ACPI: bus type ide registered
[4294671.045000] ALI15X3: IDE controller at PCI slot 0000:00:12.0
[4294671.045000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294671.045000] ALI15X3: chipset revision 199
[4294671.045000] ALI15X3: not 100% native mode: will probe irqs later
[4294671.045000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[4294671.045000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[4294671.045000] Probing IDE interface ide0...
[4294671.309000] hda: SAMSUNG SP1213N, ATA DISK drive
[4294671.564000] hdb: ST3200822A, ATA DISK drive
[4294671.615000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.615000] Probing IDE interface ide1...
[4294672.287000] hdc: PIONEER DVD-RW DVR-108, ATAPI CD/DVD-ROM drive
[4294672.899000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.899000] Probing IDE interface ide2...
[4294673.412000] Probing IDE interface ide3...
[4294673.924000] Probing IDE interface ide4...
[4294674.436000] Probing IDE interface ide5...
[4294674.950000] hda: max request size: 1024KiB
[4294674.950000] hda: 234493056 sectors (120060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.951000] hda: cache flushes supported
[4294674.951000]  /dev/ide/host0/bus0/target0/lun0: p1
[4294674.959000] hdb: max request size: 1024KiB
[4294674.960000] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[4294674.960000] hdb: cache flushes supported
[4294674.960000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
[4294675.010000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
[4294675.010000] Uniform CD-ROM driver Revision: 3.20
[4294675.204000] Attempting manual resume
[4294675.204000] swsusp: Suspend partition has wrong signature?
[4294675.257000] usbcore: registered new driver usbfs
[4294675.257000] usbcore: registered new driver hub
[4294675.258000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294675.258000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294675.258000] ohci_hcd 0000:00:13.0: ALi Corporation USB 1.1 Controller
[4294675.258000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294675.258000] ohci_hcd 0000:00:13.0: irq 20, io mem 0xfebfe000
[4294675.311000] hub 1-0:1.0: USB hub found
[4294675.311000] hub 1-0:1.0: 3 ports detected
[4294675.314000] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 21 (level, low) -> IRQ 21
[4294675.314000] ohci_hcd 0000:00:13.1: ALi Corporation USB 1.1 Controller (#2)
[4294675.314000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294675.314000] ohci_hcd 0000:00:13.1: irq 21, io mem 0xfebfd000
[4294675.367000] hub 2-0:1.0: USB hub found
[4294675.367000] hub 2-0:1.0: 3 ports detected
[4294675.370000] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 22 (level, low) -> IRQ 22
[4294675.370000] ohci_hcd 0000:00:13.2: ALi Corporation USB 1.1 Controller (#3)
[4294675.370000] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294675.370000] ohci_hcd 0000:00:13.2: irq 22, io mem 0xfebfc000
[4294675.423000] hub 3-0:1.0: USB hub found
[4294675.423000] hub 3-0:1.0: 3 ports detected
[4294675.441000] ACPI: PCI Interrupt 0000:00:13.3[D] -> GSI 23 (level, low) -> IRQ 23
[4294675.441000] ehci_hcd 0000:00:13.3: ALi Corporation USB 2.0 Controller
[4294675.441000] ehci_hcd 0000:00:13.3: debug port 1
[4294675.462000] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[4294675.462000] ehci_hcd 0000:00:13.3: irq 23, io mem 0xfebfbc00
[4294675.462000] ehci_hcd 0000:00:13.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.462000] hub 4-0:1.0: USB hub found
[4294675.462000] hub 4-0:1.0: 8 ports detected
[4294675.512000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294675.512000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294675.512000] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294675.531000] e100: eth0: e100_probe: addr 0xfeaff000, irq 21, MAC addr 00:90:27:58:47:F3
[4294677.894000] ACPI: CPU0 (power states: C1[C1])
[4294678.128000] Attempting manual resume
[4294678.128000] swsusp: Suspend partition has wrong signature?
[4294678.140000] kjournald starting.  Commit interval 5 seconds
[4294678.140000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.022000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.667000] Adding 3036244k swap on /dev/hdb5.  Priority:-1 extents:1
[4294681.964000] EXT3 FS on hdb1, internal journal
[4294686.079000] parport: PnPBIOS parport detected.
[4294686.079000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294686.163000] lp0: using parport0 (interrupt-driven).
[4294686.183000] mice: PS/2 mouse device common for all mice
[4294686.202000] Linux agpgart interface v0.101 (c) Dave Jones
[4294686.213000] nvidia: module license 'NVIDIA' taints kernel.
[4294686.221000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294686.221000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294686.526000] input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
[4294686.761000] ts: Compaq touchscreen protocol output
[4294689.791000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294690.690000] cdrom: open failed.
[4294692.742000] agpgart: Unsupported ALi chipset (device id: 1689)
[4294692.796000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294692.804000] shpchp: shpc_init : shpc_cap_offset == 0
[4294692.804000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294692.898000] agpgart: Detected AGP bridge 20
[4294692.898000] Setting up ULi AGP.
[4294692.914000] agpgart: AGP aperture is 256M @ 0xd0000000
[4294693.041000] ali1563: SMBus control = 0403
[4294693.051000] ali1563_probe: Returning 0
[4294693.112000] ali15x3_smbus 0000:00:07.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294693.112000] ali15x3_smbus 0000:00:07.1: ALI15X3 not detected, module not inserted.
[4294693.149000] ali1535_smbus 0000:00:07.1: ALI1535_smb region uninitialized - upgrade BIOS?
[4294693.149000] ali1535_smbus 0000:00:07.1: ALI1535 not detected, module not inserted.
[4294693.264000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294694.275000] AC'97 1 does not respond - RESET
[4294694.275000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294694.275000] Unable to initialize codec #1
[4294694.325000] intel8x0_measure_ac97_clock: measured 49035 usecs
[4294694.325000] intel8x0: clocking to 48000
[4294696.064000] Real Time Clock Driver v1.12
[4294696.125000] input: PC Speaker
[4294696.166000] Floppy drive(s): fd0 is 1.44M
[4294696.190000] FDC 0 is a post-1991 82077
[4294697.735000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294699.339000] NET: Registered protocol family 10
[4294699.339000] Disabled Privacy Extensions on device c02eb280(lo)
[4294699.339000] IPv6 over IPv4 tunneling driver
[4294701.738000] ACPI: Power Button (FF) [PWRF]
[4294701.738000] ACPI: Power Button (CM) [PWRB]
[4294701.805000] ibm_acpi: ec object not found
[4294706.170000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[4294706.170000] apm: overridden by ACPI.
[4294706.510000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294706.511000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6 (1400 mV)
[4294706.511000] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0xa (1300 mV)
[4294706.511000] cpu_init done, current fid 0xa, vid 0x6
[4294707.082000] Bluetooth: Core ver 2.7
[4294707.082000] NET: Registered protocol family 31
[4294707.082000] Bluetooth: HCI device and connection manager initialized
[4294707.082000] Bluetooth: HCI socket layer initialized
[4294707.124000] Bluetooth: L2CAP ver 2.7
[4294707.124000] Bluetooth: L2CAP socket layer initialized
[4294707.169000] Bluetooth: RFCOMM ver 1.5
[4294707.169000] Bluetooth: RFCOMM socket layer initialized
[4294707.169000] Bluetooth: RFCOMM TTY layer initialized
[4294708.421000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
[4294708.421000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
[4294708.421000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[4294708.859000] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
[4294708.859000] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
[4294708.859000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[4294709.624000] eth0: no IPv6 routers present
krisx@<hostremoved>:~$

---

