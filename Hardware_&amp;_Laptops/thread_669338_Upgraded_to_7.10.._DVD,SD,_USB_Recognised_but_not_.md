---
title: "Upgraded to 7.10.. DVD,SD, USB Recognised but not working"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by USFMD82 on 2008-01-16
I upgraded to 7.10 about 2 weeks ago and little by little am getting my computer back to properly functioning parameters. After I upgraded from 7.04 I noticed many things wrong but here is the issue I am having as fo now.

My DVD,SD, and USB drives if I put one in either of these slots, the computer recognizes that there is a DVD, SD, or USB drive on there however I can not access the contents of either of them. for instance, I will put a SD card in my slot, and it shows up on the File host as SD/MMC Drive, and when I click it nothing happens, right click I have the option ot open/open new window/or mount when pushing any of these nothing happens.. any ideas?

 posted in absolute beginners but I think it got lost in al lthe other posts.

Thank you!

---

### Post by USFMD82 on 2008-01-16
Forgot to mention the smae goes for my Windows (C:) partition, where I keep all my music, on 7.04 I coudl very easily just click on the "64.8gb Volume" and it woudl open up.. now it wont do anything when I click it or try to mount it.

---

### Post by USFMD82 on 2008-01-17
Bump... still having trouble with it :(

---

### Post by USFMD82 on 2008-01-19
Anybody know how to handle these problems? :(

---

### Post by dustman on 2008-01-19
have a little patience man! the ubuntu community is composed out of volunteers, people like you and me that work 8-10 hours a day, and then come home and them maybe they have enough time to take a look on this forum, and perhaps it takes some time for them to figure out what's the matter ;). so...just a little patience.


Cheers!

Radu

---

### Post by Greg Mueller on 2008-01-19
USFMD82
I am having a similar problem except with a USB CCD camera.
I can see it in the device manager, but it won't connect to the software

---

### Post by fasthands on 2008-01-20
I am having this problem too but it's just my cd dvd drive that wont read discs, Ubuntu Linux is a real pain!!!:mad:

---

### Post by USFMD82 on 2008-01-21
Im having patience with it, Im just feeling I need to bump it every day or two, because I dont know how far back people look when they log in, so if it isnt somewhat recent someone that knows what the problem is wont see my post. And im really hating having to use XP to use my SD card adn what not :)

---

### Post by USFMD82 on 2008-01-28
Bump.. Still being a pain, and all the other areas I am reserachign are coming up with no answers.. and im quickly hating usign XP on the dual boot :(

---

### Post by USFMD82 on 2008-02-01
Bump.. is there a way I could make my question more specific.. is that the problem?

---

### Post by cansei on 2008-02-01
I have a similar problem with my cell phone in USB storage mode:

[http://ubuntuforums.org/showthread.php?t=683855](http://ubuntuforums.org/showthread.php?t=683855)

I've found a lot of people with usb problems but nobody has a solution

I think I will go back to 7.04... and I hope this problem appears fixed on 8.04 final

---

### Post by USFMD82 on 2008-02-08
I hope this is not the best answer reverting back to the older version, I had no problems with any of this until I upgraded to the new version.. Its been one problem after another, and luckily I have been able to fix most of the problems with researching, but this one still seems to have me stuck..

---

### Post by dustman on 2008-02-08
seems like no one has seen your thread, or no one has the solution for your problem :(. Have you tried to install 7.10 fresh install, not upgrade from 7.04? Cause i've seen a lot of problems that appeared after upgrading. One thing...did you try to mount the devices manually? (i understood that they get recognized, but aren't mounted). Another thing that you might do is to input:
```
dmesg
```
then insert  for example a USB stick in a slot on your computer, then issue again ```
dmesg
``` and paste here the bottom lines from dmesg after you inserted the USB stick - it's easier to see the difference once you introduce the command twice, before and after ;).



Sorry about not posting earlier, but i've been too busy :|

---

### Post by USFMD82 on 2008-02-08
No need to apologise, I am just glad someone is finally able to help!

I dont know how to do a "fresh install" in other words, I dont know how I would go about deleting this one, I am in a dual boot machine, and also if I were to wipe out 7.04 would that erase al lthe stuff I have done on this OS (gotten the wifi functional and athe reports I have done on this OS (since I cant transfer them to a DVD or USB drive I dont knwo how else to do it)

I think I have tried manualhere is a screenshot of what I am doing
[IMG]http://img.photobucket.com/albums/v66/Callsignbishop/Screenshot.png[/IMG]
When I click on the word mount, nothing happens, it just acts like I didnt even click it.

Here is what came up on the dmesg werid to have so much bluetooth stuff on here since my comp doesnt actually have bluetooth, first is without SD card second is with SD card
[PHP]timber@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8340
[    0.000000] Entering add_active_range(0, 0, 98032) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98032
[    0.000000]   HighMem     98032 ->    98032
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98032
[    0.000000] On node 0 totalpages: 98032
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 733 pages used for memmap
[    0.000000]   Normal zone: 93203 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8290 checksum 0
[    0.000000] ACPI: RSDP 000F8290, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 17EF8C5B, 0034 (r1 HP     3093     20040809  LTP        0)
[    0.000000] ACPI: FACP 17EFEE41, 0074 (r1 HP     3093     20040809 PTL        5F)
[    0.000000] ACPI: DSDT 17EF8C8F, 61B2 (r1 HP     3091     20040809 MSFT  100000E)
[    0.000000] ACPI: FACS 17EFFFC0, 0040
[    0.000000] ACPI: SSDT 17EFEEB5, 00B5 (r1 PTLTD  POWERNOW 20040809  LTP        1)
[    0.000000] ACPI: APIC 17EFEF6A, 005A (r1 PTLTD       3093   20040809  LTP        0)
[    0.000000] ACPI: MCFG 17EFEFC4, 003C (r1 PTLTD    MCFG   20040809  LTP        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 97267
[    0.000000] Kernel command line: find=/wubi/boot/linux ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1591.920 MHz processor.
[   13.525008] Console: colour VGA+ 80x25
[   13.525394] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.525708] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.534817] Memory: 376844k/392128k available (2015k kernel code, 14768k reserved, 916k data, 364k init, 0k highmem)
[   13.534829] virtual kernel memory layout:
[   13.534831]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.534832]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.534834]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   13.534835]     lowmem  : 0xc0000000 - 0xd7ef0000   ( 382 MB)
[   13.534837]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.534839]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   13.534840]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   13.534844] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.534886] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.614883] Calibrating delay using timer specific routine.. 3187.37 BogoMIPS (lpj=6374746)
[   13.614911] Security Framework v1.0.0 initialized
[   13.614917] SELinux:  Disabled at boot.
[   13.614931] Mount-cache hash table entries: 512
[   13.615054] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   13.615064] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.615067] CPU: L2 Cache: 1024K (64 bytes/line)
[   13.615070] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   13.615082] Compat vDSO mapped to ffffe000.
[   13.615093] Checking 'hlt' instruction... OK.
[   13.631018] SMP alternatives: switching to UP code
[   13.631201] Freeing SMP alternatives: 11k freed
[   13.631492] Early unpacking initramfs... done
[   14.009102] ACPI: Core revision 20070126
[   14.009194] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.013339] CPU0: AMD Turion(tm) 64 Mobile Technology ML-30 stepping 02
[   14.013361] Total of 1 processors activated (3187.37 BogoMIPS).
[   14.013537] ENABLING IO-APIC IRQs
[   14.013741] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.053459] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   14.053504] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   14.053506] ...trying to set up timer as Virtual Wire IRQ... works.
[   14.198722] Brought up 1 CPUs
[   14.198837] Booting paravirtualized kernel on bare hardware
[   14.198920] Time: 14:43:57  Date: 01/08/108
[   14.198942] NET: Registered protocol family 16
[   14.199026] EISA bus registered
[   14.199043] ACPI: bus type pci registered
[   14.199177] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=6
[   14.199179] PCI: Using configuration type 1
[   14.199181] Setting up standard PCI resources
[   14.201508] ACPI: EC: Look up EC in DSDT
[   14.202147] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   14.203283] ACPI: Interpreter enabled
[   14.203286] ACPI: (supports S0 S3 S4 S5)
[   14.203300] ACPI: Using IOAPIC for interrupt routing
[   14.208164] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   14.214638] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.214647] PCI: Probing PCI hardware (bus 00)
[   14.216080] PCI: Transparent bridge - 0000:00:14.4
[   14.216176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.216313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   14.216436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   14.218253] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   14.218362] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   14.218467] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   14.218573] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   14.218698] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   14.218809] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   14.218916] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   14.219023] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   14.219107] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.219117] pnp: PnP ACPI init
[   14.219127] ACPI: bus type pnp registered
[   14.221566] pnp: PnP ACPI: found 10 devices
[   14.221569] ACPI: ACPI bus type pnp unregistered
[   14.221572] PnPBIOS: Disabled by ACPI PNP
[   14.221615] PCI: Using ACPI for IRQ routing
[   14.221618] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.242993] NET: Registered protocol family 8
[   14.242995] NET: Registered protocol family 20
[   14.243048] pnp: 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   14.243052] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   14.243056] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.243064] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   14.243067] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   14.243071] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   14.243077] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   14.243082] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   14.243086] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   14.243089] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   14.246668] Time: tsc clocksource has been installed.
[   14.273340] PCI: Bridge: 0000:00:01.0
[   14.273343]   IO window: 9000-9fff
[   14.273348]   MEM window: c0100000-c01fffff
[   14.273351]   PREFETCH window: c8000000-cfffffff
[   14.273357] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[   14.273359]   IO window: 0000a400-0000a4ff
[   14.273365]   IO window: 0000a800-0000a8ff
[   14.273372]   PREFETCH window: 30000000-33ffffff
[   14.273378]   MEM window: 34000000-37ffffff
[   14.273384] PCI: Bridge: 0000:00:14.4
[   14.273388]   IO window: a000-afff
[   14.273395]   MEM window: c0200000-c02fffff
[   14.273400]   PREFETCH window: 30000000-33ffffff
[   14.273441] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[   14.273459] NET: Registered protocol family 2
[   14.310690] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   14.310736] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   14.310934] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   14.311090] TCP: Hash tables configured (established 16384 bind 16384)
[   14.311094] TCP reno registered
[   14.322764] checking if image is initramfs... it is
[   14.774491] Switched to high resolution mode on CPU 0
[   15.069760] Freeing initrd memory: 7418k freed
[   15.070197] audit: initializing netlink socket (disabled)
[   15.070213] audit(1202481837.072:1): initialized
[   15.071974] VFS: Disk quotas dquot_6.5.1
[   15.072021] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.072106] io scheduler noop registered
[   15.072109] io scheduler anticipatory registered
[   15.072111] io scheduler deadline registered
[   15.072127] io scheduler cfq registered (default)
[   15.072139] PCI: MSI quirk detected. MSI deactivated.
[   15.738029] Boot video device is 0000:01:05.0
[   15.738176] isapnp: Scanning for PnP cards...
[   16.092731] isapnp: No Plug & Play device found
[   16.117973] Real Time Clock Driver v1.12ac
[   16.118066] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.118677] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   16.118687] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   16.119231] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.119441] input: Macintosh mouse button emulation as /class/input/input0
[   16.119510] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.122714] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.122719] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.122872] mice: PS/2 mouse device common for all mice
[   16.122973] EISA: Probing bus 0 at eisa.0
[   16.122982] Cannot allocate resource for EISA slot 1
[   16.123012] Cannot allocate resource for EISA slot 8
[   16.123014] EISA: Detected 0 cards.
[   16.123112] TCP cubic registered
[   16.123128] NET: Registered protocol family 1
[   16.123152] Using IPI No-Shortcut mode
[   16.123335]   Magic number: 12:742:737
[   16.123998] Freeing unused kernel memory: 364k freed
[   16.161873] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.322962] md: raid1 personality registered for level 1
[   17.327203] md: raid0 personality registered for level 0
[   17.332632] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   17.349083] SCSI subsystem initialized
[   17.353771] libata version 2.21 loaded.
[   17.369594] usbcore: registered new interface driver usbfs
[   17.369637] usbcore: registered new interface driver hub
[   17.369670] usbcore: registered new device driver usb
[   17.370611] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[   17.370626] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   17.370681] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[   17.370739] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0002000
[   17.370752] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.370883] usb usb1: configuration #1 chosen from 1 choice
[   17.370927] hub 1-0:1.0: USB hub found
[   17.370935] hub 1-0:1.0: 8 ports detected
[   17.478135] USB Universal Host Controller Interface driver v3.0
[   17.482662] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.482712] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   17.482725] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   17.482767] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[   17.482786] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0000000
[   17.541323] usb usb2: configuration #1 chosen from 1 choice
[   17.541364] hub 2-0:1.0: USB hub found
[   17.541376] hub 2-0:1.0: 4 ports detected
[   17.645273] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   17.645282] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   17.645314] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   17.645328] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0001000
[   17.705229] usb usb3: configuration #1 chosen from 1 choice
[   17.705264] hub 3-0:1.0: USB hub found
[   17.705276] hub 3-0:1.0: 4 ports detected
[   17.813801] usbcore: registered new interface driver libusual
[   17.821240] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.821246] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.822816] Initializing USB Mass Storage driver...
[   17.822851] usbcore: registered new interface driver usb-storage
[   17.822854] USB Mass Storage support registered.
[   17.936428] JFS: nTxBlock = 3006, nTxLock = 24048
[   17.945840] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   17.946396] SGI XFS Quota Management subsystem
[   17.967637] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   17.974031] fuse init (API version 7.8)
[   17.979483] loop: module loaded
[   17.983449] Registering unionfs 1.4
[   17.983453] unionfs: debugging is not enabled
[   17.987254] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   18.008988] AppArmor: AppArmor initialized<5>audit(1202481840.072:2):  type=1505 info="AppArmor initialized" pid=1583
[   18.015295] Failure registering capabilities with primary security module.
[   18.028423] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.028429] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.029930] ACPI: Thermal Zone [THRM] (51 C)
[   18.538344] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   18.538368] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   18.538380] ATIIXP: chipset revision 0
[   18.538383] ATIIXP: not 100% native mode: will probe irqs later
[   18.538393]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   18.538409]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   18.538420] Probing IDE interface ide0...
[   18.654751] 8139too Fast Ethernet driver 0.9.28
[   18.849094] hda: FUJITSU MHT2080AT PL, ATA DISK drive
[    5.244000] Marking TSC unstable due to: possible TSC halt in C2.
[    5.256000] Time: acpi_pm clocksource has been installed.
[    5.848000] hda: selected mode 0x45
[    5.848000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.916000] Probing IDE interface ide1...
[    6.656000] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[    6.992000] hdc: selected mode 0x22
[    6.992000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.996000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    6.996000] eth0: RealTek RTL8139 at 0xd896a000, 00:c0:9f:bd:46:64, IRQ 19
[    6.996000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.000000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    7.000000] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 22 (level, low) -> IRQ 20
[    7.048000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.064000] hda: max request size: 128KiB
[    7.068000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[    7.068000] Uniform CD-ROM driver Revision: 3.20
[    7.068000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[    7.068000] hda: cache flushes supported
[    7.068000]  hda: hda1 hda2
[    8.152000] kjournald starting.  Commit interval 5 seconds
[    8.152000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.232000] EXT3 FS on loop0, internal journal
[    8.320000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000065437e]
[   27.608000] Linux agpgart interface v0.102 (c) Dave Jones
[   27.760000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.800000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.952000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.292000] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[   28.292000] Yenta: Enabling burst memory read transactions
[   28.292000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   28.292000] Yenta: Routing CardBus interrupts to PCI
[   28.292000] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x64
[   28.524000] Yenta: ISA IRQ mask 0x0ee8, PCI irq 16
[   28.524000] Socket status: 30000006
[   28.524000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[   28.524000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   28.524000] cs: IO port probe 0xa000-0xafff: clean.
[   28.524000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   28.524000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   28.700000] sdhci: Secure Digital Host Controller Interface driver
[   28.700000] sdhci: Copyright(c) Pierre Ossman
[   28.700000] sdhci: SDHCI controller found at 0000:05:09.4 [104c:8034] (rev 0)
[   28.700000] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 16
[   28.700000] mmc0: SDHCI at 0xc020a400 irq 16 DMA
[   28.704000] mmc1: SDHCI at 0xc020a000 irq 16 DMA
[   28.704000] mmc2: SDHCI at 0xc0208400 irq 16 DMA
[   29.032000] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 16
[   29.120000] input: PC Speaker as /class/input/input2
[   29.284000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
[   29.380000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   29.408000] cs: IO port probe 0x100-0x3af: clean.
[   29.412000] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.412000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   29.412000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   29.416000] cs: IO port probe 0xa00-0xaff: clean.
[   29.492000] MC'97 0 converters and GPIO not ready (0x1)
[   29.668000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   29.700000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   30.268000] lp: driver loaded but no devices found
[   30.380000] ndiswrapper version 1.45 loaded (smp=yes)
[   30.508000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[   30.508000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 22
[   30.516000] ndiswrapper: using IRQ 22
[   30.724000] wlan0: ethernet device 00:14:a5:11:a3:20 using NDIS driver: bcmwl5, version: 0x3642e00, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   30.724000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.724000] usbcore: registered new interface driver ndiswrapper
[   30.756000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   31.828000] EXT3 FS on loop0, internal journal
[   32.956000] kjournald starting.  Commit interval 5 seconds
[   32.956000] EXT3 FS on loop1, internal journal
[   32.956000] EXT3-fs: mounted filesystem with ordered data mode.
[   37.388000] Adding 373036k swap on /media/host/wubi/disks/swap.virtual.disk.  Priority:-1 extents:1 across:373036k
[   38.692000] No dock devices found.
[   38.764000] ACPI: AC Adapter [ACAD] (off-line)
[   38.780000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   38.876000] ACPI: Battery Slot [BAT1] (battery present)
[   38.988000] input: Power Button (FF) as /class/input/input4
[   38.992000] ACPI: Power Button (FF) [PWRF]
[   39.028000] input: Power Button (CM) as /class/input/input5
[   39.032000] ACPI: Power Button (CM) [PWRB]
[   39.072000] input: Sleep Button (CM) as /class/input/input6
[   39.072000] ACPI: Sleep Button (CM) [SLPB]
[   39.092000] input: Lid Switch as /class/input/input7
[   39.092000] ACPI: Lid Switch [LID]
[   39.372000] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-30 processors (version 2.00.00)
[   39.372000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4
[   39.372000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[   43.488000] eth0: link down
[   47.952000] ppdev: user-space parallel port driver
[   49.228000] audit(1202499885.631:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5189 profile="/usr/sbin/cupsd"
[   49.928000] apm: BIOS not found.
[   50.792000] [fglrx] Maximum main memory to use for locked dma buffers: 313 MBytes.
[   50.792000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   50.916000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   54.596000] Clocksource tsc unstable (delta = -190006209 ns)
[   55.276000] [fglrx] total      GART = 130023424
[   55.276000] [fglrx] free       GART = 114032640
[   55.276000] [fglrx] max single GART = 114032640
[   55.276000] [fglrx] total      LFB  = 134217728
[   55.276000] [fglrx] free       LFB  = 120320000
[   55.276000] [fglrx] max single LFB  = 120320000
[   55.276000] [fglrx] total      Inv  = 0
[   55.276000] [fglrx] free       Inv  = 0
[   55.276000] [fglrx] max single Inv  = 0
[   55.276000] [fglrx] total      TIM  = 0
[   55.360000] Failure registering capabilities with primary security module.
[   56.508000] Bluetooth: Core ver 2.11
[   56.508000] NET: Registered protocol family 31
[   56.508000] Bluetooth: HCI device and connection manager initialized
[   56.508000] Bluetooth: HCI socket layer initialized
[   56.544000] Bluetooth: L2CAP ver 2.8
[   56.544000] Bluetooth: L2CAP socket layer initialized
[   57.008000] Bluetooth: RFCOMM socket layer initialized
[   57.008000] Bluetooth: RFCOMM TTY layer initialized
[   57.008000] Bluetooth: RFCOMM ver 1.8
[  102.048000] APIC error on CPU0: 00(40)
[  145.672000] tifm_core: SmartMedia/xD card detected in socket 0:2
[  145.788000] tifm0 : demand removing card from socket 0:2
[  154.032000] tifm_core: SmartMedia/xD card detected in socket 0:2
[  155.388000] tifm0 : demand removing card from socket 0:2
[  160.880000] tifm_core: MMC/SD card detected in socket 0:3
[  162.080000] mmcblk0: mmc3:b368 SMI   993792KiB 
[  162.080000]  mmcblk0: p1
[  175.580000] NET: Registered protocol family 17
[  188.568000] NET: Registered protocol family 10
[  188.568000] lo: Disabled Privacy Extensions
[  188.568000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  199.300000] eth1: no IPv6 routers present
[  252.616000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  314.512000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  318.080000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  337.072000] eth1: no IPv6 routers present
[  367.072000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  371.768000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  371.768000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  382.764000] eth0: no IPv6 routers present
[  435.516000] eth0: no IPv6 routers present
[  454.048000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1186.732000] tifm0 : demand removing card from socket 0:3
timber@ubuntu:~$ 

[/PHP]
[PHP]timber@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8340
[    0.000000] Entering add_active_range(0, 0, 98032) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98032
[    0.000000]   HighMem     98032 ->    98032
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98032
[    0.000000] On node 0 totalpages: 98032
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 733 pages used for memmap
[    0.000000]   Normal zone: 93203 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8290 checksum 0
[    0.000000] ACPI: RSDP 000F8290, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 17EF8C5B, 0034 (r1 HP     3093     20040809  LTP        0)
[    0.000000] ACPI: FACP 17EFEE41, 0074 (r1 HP     3093     20040809 PTL        5F)
[    0.000000] ACPI: DSDT 17EF8C8F, 61B2 (r1 HP     3091     20040809 MSFT  100000E)
[    0.000000] ACPI: FACS 17EFFFC0, 0040
[    0.000000] ACPI: SSDT 17EFEEB5, 00B5 (r1 PTLTD  POWERNOW 20040809  LTP        1)
[    0.000000] ACPI: APIC 17EFEF6A, 005A (r1 PTLTD       3093   20040809  LTP        0)
[    0.000000] ACPI: MCFG 17EFEFC4, 003C (r1 PTLTD    MCFG   20040809  LTP        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 97267
[    0.000000] Kernel command line: find=/wubi/boot/linux ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1591.920 MHz processor.
[   13.525008] Console: colour VGA+ 80x25
[   13.525394] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.525708] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.534817] Memory: 376844k/392128k available (2015k kernel code, 14768k reserved, 916k data, 364k init, 0k highmem)
[   13.534829] virtual kernel memory layout:
[   13.534831]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.534832]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.534834]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   13.534835]     lowmem  : 0xc0000000 - 0xd7ef0000   ( 382 MB)
[   13.534837]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.534839]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   13.534840]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   13.534844] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.534886] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.614883] Calibrating delay using timer specific routine.. 3187.37 BogoMIPS (lpj=6374746)
[   13.614911] Security Framework v1.0.0 initialized
[   13.614917] SELinux:  Disabled at boot.
[   13.614931] Mount-cache hash table entries: 512
[   13.615054] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   13.615064] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.615067] CPU: L2 Cache: 1024K (64 bytes/line)
[   13.615070] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   13.615082] Compat vDSO mapped to ffffe000.
[   13.615093] Checking 'hlt' instruction... OK.
[   13.631018] SMP alternatives: switching to UP code
[   13.631201] Freeing SMP alternatives: 11k freed
[   13.631492] Early unpacking initramfs... done
[   14.009102] ACPI: Core revision 20070126
[   14.009194] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.013339] CPU0: AMD Turion(tm) 64 Mobile Technology ML-30 stepping 02
[   14.013361] Total of 1 processors activated (3187.37 BogoMIPS).
[   14.013537] ENABLING IO-APIC IRQs
[   14.013741] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.053459] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   14.053504] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   14.053506] ...trying to set up timer as Virtual Wire IRQ... works.
[   14.198722] Brought up 1 CPUs
[   14.198837] Booting paravirtualized kernel on bare hardware
[   14.198920] Time: 14:43:57  Date: 01/08/108
[   14.198942] NET: Registered protocol family 16
[   14.199026] EISA bus registered
[   14.199043] ACPI: bus type pci registered
[   14.199177] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=6
[   14.199179] PCI: Using configuration type 1
[   14.199181] Setting up standard PCI resources
[   14.201508] ACPI: EC: Look up EC in DSDT
[   14.202147] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   14.203283] ACPI: Interpreter enabled
[   14.203286] ACPI: (supports S0 S3 S4 S5)
[   14.203300] ACPI: Using IOAPIC for interrupt routing
[   14.208164] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   14.214638] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.214647] PCI: Probing PCI hardware (bus 00)
[   14.216080] PCI: Transparent bridge - 0000:00:14.4
[   14.216176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.216313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   14.216436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   14.218253] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   14.218362] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   14.218467] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   14.218573] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   14.218698] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   14.218809] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   14.218916] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   14.219023] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   14.219107] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.219117] pnp: PnP ACPI init
[   14.219127] ACPI: bus type pnp registered
[   14.221566] pnp: PnP ACPI: found 10 devices
[   14.221569] ACPI: ACPI bus type pnp unregistered
[   14.221572] PnPBIOS: Disabled by ACPI PNP
[   14.221615] PCI: Using ACPI for IRQ routing
[   14.221618] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.242993] NET: Registered protocol family 8
[   14.242995] NET: Registered protocol family 20
[   14.243048] pnp: 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   14.243052] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   14.243056] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.243064] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   14.243067] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   14.243071] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   14.243077] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   14.243082] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   14.243086] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   14.243089] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   14.246668] Time: tsc clocksource has been installed.
[   14.273340] PCI: Bridge: 0000:00:01.0
[   14.273343]   IO window: 9000-9fff
[   14.273348]   MEM window: c0100000-c01fffff
[   14.273351]   PREFETCH window: c8000000-cfffffff
[   14.273357] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[   14.273359]   IO window: 0000a400-0000a4ff
[   14.273365]   IO window: 0000a800-0000a8ff
[   14.273372]   PREFETCH window: 30000000-33ffffff
[   14.273378]   MEM window: 34000000-37ffffff
[   14.273384] PCI: Bridge: 0000:00:14.4
[   14.273388]   IO window: a000-afff
[   14.273395]   MEM window: c0200000-c02fffff
[   14.273400]   PREFETCH window: 30000000-33ffffff
[   14.273441] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[   14.273459] NET: Registered protocol family 2
[   14.310690] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   14.310736] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   14.310934] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   14.311090] TCP: Hash tables configured (established 16384 bind 16384)
[   14.311094] TCP reno registered
[   14.322764] checking if image is initramfs... it is
[   14.774491] Switched to high resolution mode on CPU 0
[   15.069760] Freeing initrd memory: 7418k freed
[   15.070197] audit: initializing netlink socket (disabled)
[   15.070213] audit(1202481837.072:1): initialized
[   15.071974] VFS: Disk quotas dquot_6.5.1
[   15.072021] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.072106] io scheduler noop registered
[   15.072109] io scheduler anticipatory registered
[   15.072111] io scheduler deadline registered
[   15.072127] io scheduler cfq registered (default)
[   15.072139] PCI: MSI quirk detected. MSI deactivated.
[   15.738029] Boot video device is 0000:01:05.0
[   15.738176] isapnp: Scanning for PnP cards...
[   16.092731] isapnp: No Plug & Play device found
[   16.117973] Real Time Clock Driver v1.12ac
[   16.118066] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.118677] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   16.118687] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   16.119231] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.119441] input: Macintosh mouse button emulation as /class/input/input0
[   16.119510] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.122714] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.122719] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.122872] mice: PS/2 mouse device common for all mice
[   16.122973] EISA: Probing bus 0 at eisa.0
[   16.122982] Cannot allocate resource for EISA slot 1
[   16.123012] Cannot allocate resource for EISA slot 8
[   16.123014] EISA: Detected 0 cards.
[   16.123112] TCP cubic registered
[   16.123128] NET: Registered protocol family 1
[   16.123152] Using IPI No-Shortcut mode
[   16.123335]   Magic number: 12:742:737
[   16.123998] Freeing unused kernel memory: 364k freed
[   16.161873] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.322962] md: raid1 personality registered for level 1
[   17.327203] md: raid0 personality registered for level 0
[   17.332632] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   17.349083] SCSI subsystem initialized
[   17.353771] libata version 2.21 loaded.
[   17.369594] usbcore: registered new interface driver usbfs
[   17.369637] usbcore: registered new interface driver hub
[   17.369670] usbcore: registered new device driver usb
[   17.370611] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[   17.370626] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   17.370681] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[   17.370739] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0002000
[   17.370752] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.370883] usb usb1: configuration #1 chosen from 1 choice
[   17.370927] hub 1-0:1.0: USB hub found
[   17.370935] hub 1-0:1.0: 8 ports detected
[   17.478135] USB Universal Host Controller Interface driver v3.0
[   17.482662] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.482712] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   17.482725] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   17.482767] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[   17.482786] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0000000
[   17.541323] usb usb2: configuration #1 chosen from 1 choice
[   17.541364] hub 2-0:1.0: USB hub found
[   17.541376] hub 2-0:1.0: 4 ports detected
[   17.645273] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   17.645282] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   17.645314] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   17.645328] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0001000
[   17.705229] usb usb3: configuration #1 chosen from 1 choice
[   17.705264] hub 3-0:1.0: USB hub found
[   17.705276] hub 3-0:1.0: 4 ports detected
[   17.813801] usbcore: registered new interface driver libusual
[   17.821240] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.821246] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.822816] Initializing USB Mass Storage driver...
[   17.822851] usbcore: registered new interface driver usb-storage
[   17.822854] USB Mass Storage support registered.
[   17.936428] JFS: nTxBlock = 3006, nTxLock = 24048
[   17.945840] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   17.946396] SGI XFS Quota Management subsystem
[   17.967637] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   17.974031] fuse init (API version 7.8)
[   17.979483] loop: module loaded
[   17.983449] Registering unionfs 1.4
[   17.983453] unionfs: debugging is not enabled
[   17.987254] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   18.008988] AppArmor: AppArmor initialized<5>audit(1202481840.072:2):  type=1505 info="AppArmor initialized" pid=1583
[   18.015295] Failure registering capabilities with primary security module.
[   18.028423] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.028429] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.029930] ACPI: Thermal Zone [THRM] (51 C)
[   18.538344] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   18.538368] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   18.538380] ATIIXP: chipset revision 0
[   18.538383] ATIIXP: not 100% native mode: will probe irqs later
[   18.538393]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   18.538409]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   18.538420] Probing IDE interface ide0...
[   18.654751] 8139too Fast Ethernet driver 0.9.28
[   18.849094] hda: FUJITSU MHT2080AT PL, ATA DISK drive
[    5.244000] Marking TSC unstable due to: possible TSC halt in C2.
[    5.256000] Time: acpi_pm clocksource has been installed.
[    5.848000] hda: selected mode 0x45
[    5.848000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.916000] Probing IDE interface ide1...
[    6.656000] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[    6.992000] hdc: selected mode 0x22
[    6.992000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.996000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    6.996000] eth0: RealTek RTL8139 at 0xd896a000, 00:c0:9f:bd:46:64, IRQ 19
[    6.996000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.000000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    7.000000] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 22 (level, low) -> IRQ 20
[    7.048000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.064000] hda: max request size: 128KiB
[    7.068000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[    7.068000] Uniform CD-ROM driver Revision: 3.20
[    7.068000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[    7.068000] hda: cache flushes supported
[    7.068000]  hda: hda1 hda2
[    8.152000] kjournald starting.  Commit interval 5 seconds
[    8.152000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.232000] EXT3 FS on loop0, internal journal
[    8.320000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000065437e]
[   27.608000] Linux agpgart interface v0.102 (c) Dave Jones
[   27.760000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.800000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.952000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.292000] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[   28.292000] Yenta: Enabling burst memory read transactions
[   28.292000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   28.292000] Yenta: Routing CardBus interrupts to PCI
[   28.292000] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x64
[   28.524000] Yenta: ISA IRQ mask 0x0ee8, PCI irq 16
[   28.524000] Socket status: 30000006
[   28.524000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[   28.524000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   28.524000] cs: IO port probe 0xa000-0xafff: clean.
[   28.524000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   28.524000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   28.700000] sdhci: Secure Digital Host Controller Interface driver
[   28.700000] sdhci: Copyright(c) Pierre Ossman
[   28.700000] sdhci: SDHCI controller found at 0000:05:09.4 [104c:8034] (rev 0)
[   28.700000] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 16
[   28.700000] mmc0: SDHCI at 0xc020a400 irq 16 DMA
[   28.704000] mmc1: SDHCI at 0xc020a000 irq 16 DMA
[   28.704000] mmc2: SDHCI at 0xc0208400 irq 16 DMA
[   29.032000] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 16
[   29.120000] input: PC Speaker as /class/input/input2
[   29.284000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
[   29.380000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   29.408000] cs: IO port probe 0x100-0x3af: clean.
[   29.412000] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.412000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   29.412000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   29.416000] cs: IO port probe 0xa00-0xaff: clean.
[   29.492000] MC'97 0 converters and GPIO not ready (0x1)
[   29.668000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   29.700000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   30.268000] lp: driver loaded but no devices found
[   30.380000] ndiswrapper version 1.45 loaded (smp=yes)
[   30.508000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[   30.508000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 22
[   30.516000] ndiswrapper: using IRQ 22
[   30.724000] wlan0: ethernet device 00:14:a5:11:a3:20 using NDIS driver: bcmwl5, version: 0x3642e00, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   30.724000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.724000] usbcore: registered new interface driver ndiswrapper
[   30.756000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   31.828000] EXT3 FS on loop0, internal journal
[   32.956000] kjournald starting.  Commit interval 5 seconds
[   32.956000] EXT3 FS on loop1, internal journal
[   32.956000] EXT3-fs: mounted filesystem with ordered data mode.
[   37.388000] Adding 373036k swap on /media/host/wubi/disks/swap.virtual.disk.  Priority:-1 extents:1 across:373036k
[   38.692000] No dock devices found.
[   38.764000] ACPI: AC Adapter [ACAD] (off-line)
[   38.780000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   38.876000] ACPI: Battery Slot [BAT1] (battery present)
[   38.988000] input: Power Button (FF) as /class/input/input4
[   38.992000] ACPI: Power Button (FF) [PWRF]
[   39.028000] input: Power Button (CM) as /class/input/input5
[   39.032000] ACPI: Power Button (CM) [PWRB]
[   39.072000] input: Sleep Button (CM) as /class/input/input6
[   39.072000] ACPI: Sleep Button (CM) [SLPB]
[   39.092000] input: Lid Switch as /class/input/input7
[   39.092000] ACPI: Lid Switch [LID]
[   39.372000] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-30 processors (version 2.00.00)
[   39.372000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4
[   39.372000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[   43.488000] eth0: link down
[   47.952000] ppdev: user-space parallel port driver
[   49.228000] audit(1202499885.631:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5189 profile="/usr/sbin/cupsd"
[   49.928000] apm: BIOS not found.
[   50.792000] [fglrx] Maximum main memory to use for locked dma buffers: 313 MBytes.
[   50.792000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   50.916000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   54.596000] Clocksource tsc unstable (delta = -190006209 ns)
[   55.276000] [fglrx] total      GART = 130023424
[   55.276000] [fglrx] free       GART = 114032640
[   55.276000] [fglrx] max single GART = 114032640
[   55.276000] [fglrx] total      LFB  = 134217728
[   55.276000] [fglrx] free       LFB  = 120320000
[   55.276000] [fglrx] max single LFB  = 120320000
[   55.276000] [fglrx] total      Inv  = 0
[   55.276000] [fglrx] free       Inv  = 0
[   55.276000] [fglrx] max single Inv  = 0
[   55.276000] [fglrx] total      TIM  = 0
[   55.360000] Failure registering capabilities with primary security module.
[   56.508000] Bluetooth: Core ver 2.11
[   56.508000] NET: Registered protocol family 31
[   56.508000] Bluetooth: HCI device and connection manager initialized
[   56.508000] Bluetooth: HCI socket layer initialized
[   56.544000] Bluetooth: L2CAP ver 2.8
[   56.544000] Bluetooth: L2CAP socket layer initialized
[   57.008000] Bluetooth: RFCOMM socket layer initialized
[   57.008000] Bluetooth: RFCOMM TTY layer initialized
[   57.008000] Bluetooth: RFCOMM ver 1.8
[  102.048000] APIC error on CPU0: 00(40)
[  145.672000] tifm_core: SmartMedia/xD card detected in socket 0:2
[  145.788000] tifm0 : demand removing card from socket 0:2
[  154.032000] tifm_core: SmartMedia/xD card detected in socket 0:2
[  155.388000] tifm0 : demand removing card from socket 0:2
[  160.880000] tifm_core: MMC/SD card detected in socket 0:3
[  162.080000] mmcblk0: mmc3:b368 SMI   993792KiB 
[  162.080000]  mmcblk0: p1
[  175.580000] NET: Registered protocol family 17
[  188.568000] NET: Registered protocol family 10
[  188.568000] lo: Disabled Privacy Extensions
[  188.568000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  199.300000] eth1: no IPv6 routers present
[  252.616000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  314.512000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  318.080000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  337.072000] eth1: no IPv6 routers present
[  367.072000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  371.768000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  371.768000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  382.764000] eth0: no IPv6 routers present
[  435.516000] eth0: no IPv6 routers present
[  454.048000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1186.732000] tifm0 : demand removing card from socket 0:3
[ 1289.728000] tifm_core: SmartMedia/xD card detected in socket 0:2
[ 1290.088000] tifm0 : demand removing card from socket 0:2
[ 1290.636000] tifm_core: SmartMedia/xD card detected in socket 0:2
[ 1290.692000] tifm0 : demand removing card from socket 0:2
[ 1293.572000] tifm_core: MMC/SD card detected in socket 0:3
[ 1293.756000] mmcblk0: mmc3:b368 SMI   993792KiB 
[ 1293.756000]  mmcblk0: p1
timber@ubuntu:~$ 
[/PHP]

Thanks for your assistance!!

---

### Post by USFMD82 on 2008-02-10
Let me know if oyu needed any more information..

---

### Post by dustman on 2008-02-14
well i said manually mounting i was referring to give the instructions from the console. If there is an error, the console will return an error message, while the GUI won't. The output of dmesg is somehow puzzling to me. It seems that the card gets recognized, then it's removed, then it gets recognized again, then again removed. Searched over the web, and found this post here : [http://www.avrfreaks.net/index.php?name=PNphpBB2&file=viewtopic&t=56640&postdays=0&postorder=asc](http://www.avrfreaks.net/index.php?name=PNphpBB2&file=viewtopic&t=56640&postdays=0&postorder=asc) . The last lines of dmesg that were posted there are similar to yours. Could you please post the output of the following command after you have connected your device? ```
ls -l /dev | grep mmc
``` 
And not to forget, also take a look here : [http://sputnik.altervista.org/](http://sputnik.altervista.org/) . This dude says that he also had problems with XD Cards, and dmesg says that you do have a XD card.


P.S. 100 posts :D

---

### Post by colinsanter on 2008-02-16
If your problem is playing music or DVD&#347; try following this link [http://www.getautomatix.com/]("http://www.getautomatix.com/") download and install the version that suits your machine type and then install the drivers and plugins for Mplayer, extra restricted codecs, and the DVD codecs. It solved all of my sound and DVD problems. 
Hope this helps.

---

### Post by dustman on 2008-02-16
i think that the problem is that the  devices gets recognized (dmesg shows it, and nautilus shows it) but it doesn't get mounted automatically. Still waiting for the feedback from USFMD82, regarding the output of "ls -l /dev | grep mmc"  :).

---

### Post by USFMD82 on 2008-02-19
```
timber@ubuntu:~$ ls -l /dev | grep mmc
brw-rw---- 1 root   plugdev 179,   0 2008-02-19 19:25 mmcblk0
brw-rw---- 1 root   plugdev 179,   1 2008-02-19 19:25 mmcblk0p1
timber@ubuntu:~$ 

```

Sorry been really busy week with school, forgot to mention, my USB drive does work because I am using my mouse throguh the USB, but it just seems that no drives mount manually or automaticaly.

---

### Post by oldsoundguy on 2008-02-19
Ubuntu may SEE the drives or plug ins, but unless you install the program to RUN them from the synaptic library or from the on line repositories NOTHING will work.

The best guide I have found: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by USFMD82 on 2008-02-19
I guess Im not 100% sure what your sayign, like I get I need something to run them, woudl that of been erased in the upgrade I installed 7.04 clean, and had no problems accessing stuff.. is the program I want NFTS or is it something else like that?

---

### Post by dustman on 2008-02-20
create a folder in /media or /mnt (let's say the new folder is in "/media" and will be called "card"). Then try to mount the device manually :
```
sudo mount -t vfat /dev/mmcblk0 /media/card
```
and if that shows and error like : 
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
try :
```
sudo mount -t vfat /dev/mmcblk0p1 /media/card
```
well, i think that the file system is vfat (not sure about it, but you could give it a try).

If any error comes out, copy+paste it here, along with 
```
dmesg | tail
```

Cheers!

Radu

---

### Post by dustman on 2008-02-24
well...i searched and found that the devices automount cand also be done in the following way: go to Applications->System Tools->Configuration Editor (if you do not have it, go to System->Preferences->Main Menu, then in the left list click onto System Tools, then in the right list make sure that Configuration Editor is checked). In the Configuration Editor window, in the left list, go to desktop->gnome->volume_manager, and click onto "volume_manager". In the right list you should see a bunch of checked and unchecked options. Make sure that the "automount_drives" and "automount_media" are checked.

Hope it does the trick!


Cheers,

Radu

---

### Post by USFMD82 on 2008-03-04
Dustman, have been so busy with exams have not had the chance to try the things you suggested.. and as of right now I cant get my Ubuntu up right now.. but when I do I will run the commands as well as check the configuration settings you suggested.. I am curious. what som of the peopel are saying is I need a program to recognize the drives.. (NTFS?) I never downloaded anything extra when I updated.. should I go to synaptic and download something that I might need? this might be my whole problem.

thanks so much for all the work and help oyu have done so far!!

---

### Post by USFMD82 on 2008-03-04
Checked it and both of those options are checked.. will try the USB mount tomorrow

---

### Post by dustman on 2008-03-05
as i know it, for Ubuntu to write onto NTFS drives, you need the program called **ntfs-3g**. But this is only for writing. Ubuntu 7.04 (could be wrong) was the first Ubuntu version to have this ntfs-3g installed by default. Therefore Gutsy must also have it by default. But as i see it, your drives get recognized by the system, but they don't get mounted automatically, nor does the visual manual mount work (right click on the drive ->mount). So i don't think that you need some other extra program; of course you could try to write ```
sudo ntfs-3g
``` in a terminal, and see whether the output is something like : "the ntfs-3g command is not installed bla bla", or you'll receive some instructions about how to use the command. 

I hope you'll solve your problem :)


Cheers!

Radu

---

### Post by USFMD82 on 2008-03-05
Weird thing Happened when went to create the "card folder" in /media it would not let me creat a folder as well many folders said I didnt have permissions here is what the screenshot looked like

[IMG]http://img.photobucket.com/albums/v66/Callsignbishop/Screenshot-media_-_File_Browser.jpg[/IMG]

and when I ran the latest command you asked for I got this (note this is with both a USB flash drive as well as a SD card in the reader
```
timber@ubuntu:~$ sudo ntfs-3g
ntfs-3g: No device is specified.

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  http://ntfs-3g.org
timber@ubuntu:~$ 
```

---

### Post by dustman on 2008-03-05
> **USFMD82 said:**
> Weird thing Happened when went to create the "card folder" in /media it would not let me creat a folder as well many folders said I didnt have permissions here is what the screenshot looked like

well you should try to create that folder from the command line :) . You can create a folder in /media only if you are root (and you are logged in as timber). The command is: ```
sudo mkdir /media/card
```

> **USFMD82 said:**
> 
and when I ran the latest command you asked for I got this (note this is with both a USB flash drive as well as a SD card in the reader
```
timber@ubuntu:~$ sudo ntfs-3g
ntfs-3g: No device is specified.

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  http://ntfs-3g.org
timber@ubuntu:~$ 
```
that is a good thing. It means that you have ntfs-3g installed. If the mounting will not work with the "vfat" filesystem, try a "man mount" and change that "vfat" with the available filesystems you find in the man pages for "mount". I dunno what filesystem does your card/USB flashdrive has, but mine has "vfat".

Regards,

Radu

---

### Post by USFMD82 on 2008-03-06
THE SD CARD IS WORKING!!!
Well it is readable, I cant write to it, and whenever I clicked a song on there it dissappeared and now it is showing nothing on the contents of the drive. I took it out and tested it in window, and everything is still there.. I am writing in windows so I I dont have the code that showed up but when I did

```
sudo mkdir /media/card
```
the folder was created

```
sudo mount -t vfat /dev/mmcblk0 /media/card
``` and this came up
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
sudo mount -t vfat /dev/mmcblk0p1 /media/card/
```

This worked and mounted the card but as mentioned it was only able to see what was on the drive was unable ot listen ot any sogns or write to it (I tried to copy and paste a word document to it but was told I had insufficient privilieges.. I have a feelign we are getting somewhere with this!!!!

---

### Post by dustman on 2008-03-06
yeah, i didn't really know if you card was mmcblk0 or mmcblk0p1, that's why i wrote you to try them both :D. I don't know why you get that behaviour (your card gets mounted but you can't use the data on it). The thing with having no permissions of copying those files is because you are logged in as "timber", and the "/media/card" folder was created by root ("sudo mkdir...."). You have 2 options here: use the command line to copy the files, or run Nautilus as root ("sudo nautilus") - or you could try to create a folder in your home directory ("mkdir /home/timber/card"), and mounting the card there (never tried it though). About that strange situation with not being able to use the files directly from the card...i'm out of any ideas :|. Try to copy those files...maybe it'll work.

Cheers!

Radu

---

### Post by USFMD82 on 2008-03-08
OK.. so I must of been wrong.. I am listening to a song right now off of my SD card.. as well I was able ot move files around on it to and form Ubuntu.. os disregard the whole thing I said about that.. so.. now that we know that worked for SD.. what can we do to mount m USB flash drive, as well as my DVD drive,as well as my  windows file system (other partition). As well as get these things ot mount themselves automatically.. oh to be back ot the simpler days of 7.04 lol.. Once this is fived I think I will be somewhat out of the wood work..cant begin to tell oyu how grateful I am for the help oyu have been

---

### Post by dustman on 2008-03-09
i'm glad i could help you! That's the whole idea of these forums, to help others and be helped ;). I'm using linux for about a year and a half, and it was difficult at the beginning...i didn't even know how to install something, but now it's better, and all this because of this forum, that made my Ubuntu work like a dream . Now about your other devices that don't get automatically mounted, you couud do something like you did with your SD card. Make separate mount points (folders in /media), and use that command: ```
sudo mount -t vfat /dev/mmcblk0p1 /media/card/
```, but instead of "vfat" you have to put the corresponding filesystem, instead of "mmcblk0p1" you have to put the device you want to mount, and "card" you must change to the folder created for that device. It's a lot of work, and you must mount those devices manually everytime :|. There is a file :"/etc/fstab", and as i understood, it manages all the mounting and unmounting (automatically) + boot up. But because i never had this kind of problem, i dunno how this is done. You could stick with Gutsy for the time being, and when Hardy Heron will be released, make a clean install of it.  Backup your data on DVD-s or on the windows partitions, and format your Ubuntu partitions. When you make a distro upgrade, there might appear all sorts of problems (i know cause i had several).

So, if you install Hardy Heron, take into consideration that a new version sometimes is better, and sometimes it's not, because there could be some bugs that could make your Ubuntu experience miserable :) . But because Hardy is Long Term Support, it's supposed to be more reliable than other versions.


Best regards,

Radu

---

### Post by USFMD82 on 2008-03-10
How do I know what to put in place of mmcblk0p1? I think I got what oyu are saying for the rest.. I will look at fstab later today.. Thanks again!

---

### Post by dustman on 2008-03-12
> **USFMD82 said:**
> How do I know what to put in place of mmcblk0p1? I think I got what oyu are saying for the rest.. I will look at fstab later today.. Thanks again!
well, i kinda guessed what the name of the device is, by looking at the output of "dmesg". Some USB flash memory sticks are recognized as "sdb", "sdb1" etc...but that might be just in my case. So do as you did before...input in a terminal : "dmesg" (without the quotes :) ), then plug in you device, and input dmesg again. Scroll up to see the differences (and try to guess what's the name of the device). Then try a ```
ls /dev | grep NAME_OF_DEVICE
``` where the NAME_OF_DEVICE  is the name you got from dmesg. 
My knowledge of the contents of fstab is very limited. I only know how to configure the GRUB kernel list (that's towards the end of the file). I could be wrong about the thing that fstab is the file that handles the automatically mounting of the devices :).


Cheers!

Radu

---

### Post by USFMD82 on 2008-03-12
so this fix wouldnt work for my C drive then i am assuming? I will start doing soem research on FStab maybey I will come up with something.. thanks again for all your help

---

### Post by dustman on 2008-03-13
> **USFMD82 said:**
> so this fix wouldnt work for my C drive then i am assuming? I will start doing soem research on FStab maybey I will come up with something.. thanks again for all your help
well, your C drive gets recognized (but not automatically mounted) when your kernel loads....so it's already in /dev/ when you enter Ubuntu. Try a ```
ls /dev | grep sda
```  I think you'll get the names of all the partitions of your hard disk (i would paste you my output but currently i'm not  at home) - "sda1,sda2,sda3,sda4 etc" . Then you can create a mount point (folder) in /media (let's say "c_drive"), and mount the C partition in the same manner as you did with the SD card ;) 
```
sudo mount -t ntfs /dev/sda1 /media/c_drive
``` that is if your C partition is "sda1". Sometimes the partition table is a little odd, so you could try to mount all your "sda", and check everytime whethever you found the C partition :). This stuff with partition mounting is easier to be done automatically, cause you don't need to unmount them only when the compter shuts down (compared to the SD card or the USB flash drive, where you usually plug them in, copy/paste/delete files , then unplug 'em). You could mount your windows partitions by making a script that'll run at start-up, containing the mounting commands. There are a lot of tutorials about how to make a script run at start-up.

P.S. like i said, glad i could help you :)

Cheers!

Radu

---

