---
title: "EDGY - ATI RADEON 7500 - no suggestions work for Direct Rendering"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by becatlibra on 2007-01-22
It has been months - I have followed ALL the suggestions to get direct rendering to turn on.  NOTHING seems to work at all.  Using the ATI driver, using the radeon driver.  Using 5-10 various options in many different configurations, and using NO options at all.  

It CANNOT be the flglx driver.  That does not support the 7500.  The laptop this is on is a IBM T42.  Knoppix (installed on the HDD) worked fine but I thought I'd switch to ubuntu.  Since then (from dapper to edgy) I have not been able to get this to work right AT ALL.

Nothing anyone suggests works worth a damn.  Direct rendering should be able to work.  It's a 32meg video card.

Has anyone actually solved this?  Some people say they have but then their solutions don't work at all.

PLEASE

---

### Post by IntuitiveNipple on 2007-01-22
I don't have that chip-set, but I've successfully solved a similar issue (twice) for Intel i810 (i815) chip-sets.

I did a quick Google based on your chip-set and my experience and found this:
> ...make sure the agpgart and intel_agp kernel modules are loaded before the radeon module. I enforce this by adding add before radeon intel_agp agpgart to /etc/modules.d/aliases

What do the /var/log/dmesg and /var/log/Xorg.9.log look like? If you want to [paste-bin](paste.ubuntu-nl.org) them I will take a quick look for anything obvious.

After I solved my issues I realised the clues to solving them earlier had been in those logs all along.

---

### Post by becatlibra on 2007-01-22
I don't have an /etc/modules.d/ directory.

There is an /etc/modprobe.d/ directory which contains a file titled aliases however this file does not contain entries for agpgart, intel_agp or radeon.

I just ran some updates and I will see if that fixes anything.

Nope - didn't work.  I assume the google'd advice was for another distro?

I will post what you asked for.

I REALLY APPRECIATE your help in this.  It has been very frustrating.  I've never had a problem like this before.

---

### Post by IntuitiveNipple on 2007-01-22
Sorry, yes... for us on Ubuntu it is **/etc/modprobe.d/** - I pasted in the solution the other user found. I know how frustrating it is - it turned out to be a simple solution on the i810 - the **DefaultDepth** (bits-per-pixel) had to be set to 16 in **xorg.conf** to enable DRI.

Idea: If you have a Knoppix LiveCD why not boot it, go into X and check it has started with DRI, then save all the log files and output of lsmod, return to Ubuntu, boot, and then compare the log files and lsmod output - you might notice something significant.

---

### Post by becatlibra on 2007-01-22
Okay - I'm not really sure what that paste-bin did so i'll post them here as well

> 
[17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000005ff50000 (usable)
[17179569.184000]  BIOS-e820: 000000005ff50000 - 000000005ff67000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000005ff67000 - 000000005ff79000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[17179569.184000] 639MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 393040
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 163664 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f6d70
[17179569.184000] ACPI: XSDT (v001 IBM    TP-1R    0x00003210  LTP 0x00000000) @ 0x5ff5a6bd
[17179569.184000] ACPI: FADT (v003 IBM    TP-1R    0x00003210 IBM  0x00000001) @ 0x5ff5a800
[17179569.184000] ACPI: SSDT (v001 IBM    TP-1R    0x00003210 MSFT 0x0100000e) @ 0x5ff5a9b4
[17179569.184000] ACPI: ECDT (v001 IBM    TP-1R    0x00003210 IBM  0x00000001) @ 0x5ff66ecc
[17179569.184000] ACPI: TCPA (v001 IBM    TP-1R    0x00003210 PTL  0x00000001) @ 0x5ff66f1e
[17179569.184000] ACPI: BOOT (v001 IBM    TP-1R    0x00003210  LTP 0x00000001) @ 0x5ff66fd8
[17179569.184000] ACPI: DSDT (v001 IBM    TP-1R    0x00003210 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 70000000 (gap: 60000000:9f800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=c98c0347-566f-4df0-83cf-5b11d84a1ea9 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01c05000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 599.575 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.784000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.784000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.908000] Memory: 1547180k/1572160k available (1829k kernel code, 23660k reserved, 1038k data, 288k init, 654656k highmem)
[17179571.908000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.988000] Calibrating delay using timer specific routine.. 1200.33 BogoMIPS (lpj=2400661)
[17179571.988000] Security Framework v1.0.0 initialized
[17179571.988000] SELinux:  Disabled at boot.
[17179571.988000] Mount-cache hash table entries: 512
[17179571.988000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179571.988000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179571.988000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179571.988000] CPU: L2 cache: 2048K
[17179571.988000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179571.988000] CPU: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[17179571.988000] Checking 'hlt' instruction... OK.
[17179572.004000] SMP alternatives: switching to UP code
[17179572.004000] Freeing SMP alternatives: 0k freed
[17179572.004000] checking if image is initramfs... it is
[17179573.848000] Freeing initrd memory: 6988k freed
[17179573.848000] ACPI: Core revision 20060707
[17179573.848000] ACPI: Looking for DSDT ... not found!
[17179573.860000] ACPI: setting ELCR to 0200 (from 0820)
[17179573.904000] NET: Registered protocol family 16
[17179573.904000] EISA bus registered
[17179573.904000] ACPI: bus type pci registered
[17179573.904000] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[17179573.904000] PCI: Using configuration type 1
[17179573.904000] Setting up standard PCI resources
[17179573.908000] ACPI: Found ECDT
[17179573.932000] ACPI: Interpreter enabled
[17179573.932000] ACPI: Using PIC for interrupt routing
[17179573.932000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[17179573.932000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11)
[17179573.936000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[17179573.936000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[17179573.940000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179573.940000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179573.940000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179573.944000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[17179573.944000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.944000] PCI: Probing PCI hardware (bus 00)
[17179573.952000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179573.952000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179573.952000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.952000] Boot video device is 0000:01:00.0
[17179573.952000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.952000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.964000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[17179573.968000] ACPI: Power Resource [PUBS] (on)
[17179573.968000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179573.968000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179573.972000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.972000] pnp: PnP ACPI init
[17179573.984000] pnp: PnP ACPI: found 13 devices
[17179573.984000] PnPBIOS: Disabled by ACPI PNP
[17179573.984000] PCI: Using ACPI for IRQ routing
[17179573.984000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.000000] PCI: Bridge: 0000:00:01.0
[17179574.000000]   IO window: 3000-3fff
[17179574.000000]   MEM window: c0100000-c01fffff
[17179574.000000]   PREFETCH window: e0000000-e7ffffff
[17179574.000000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[17179574.000000]   IO window: 00004000-000040ff
[17179574.000000]   IO window: 00004400-000044ff
[17179574.000000]   PREFETCH window: e8000000-e9ffffff
[17179574.000000]   MEM window: c2000000-c3ffffff
[17179574.000000] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[17179574.000000]   IO window: 00004800-000048ff
[17179574.000000]   IO window: 00004c00-00004cff
[17179574.000000]   PREFETCH window: ea000000-ebffffff
[17179574.000000]   MEM window: c4000000-c5ffffff
[17179574.000000] PCI: Bridge: 0000:00:1e.0
[17179574.000000]   IO window: 4000-8fff
[17179574.000000]   MEM window: c0200000-cfffffff
[17179574.000000]   PREFETCH window: e8000000-efffffff
[17179574.000000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.000000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179574.000000] PCI: setting IRQ 11 as level-triggered
[17179574.000000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179574.004000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179574.004000] PCI: setting IRQ 5 as level-triggered
[17179574.004000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179574.004000] NET: Registered protocol family 2
[17179574.044000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.044000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179574.044000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.044000] TCP: Hash tables configured (established 262144 bind 65536)
[17179574.044000] TCP reno registered
[17179574.044000] Simple Boot Flag at 0x35 set to 0x1
[17179574.048000] audit: initializing netlink socket (disabled)
[17179574.048000] audit(1169491404.048:1): initialized
[17179574.048000] highmem bounce pool size: 64 pages
[17179574.048000] VFS: Disk quotas dquot_6.5.1
[17179574.048000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.048000] Initializing Cryptographic API
[17179574.048000] io scheduler noop registered
[17179574.048000] io scheduler anticipatory registered
[17179574.048000] io scheduler deadline registered
[17179574.048000] io scheduler cfq registered (default)
[17179574.048000] isapnp: Scanning for PnP cards...
[17179574.400000] isapnp: No Plug & Play device found
[17179574.444000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.448000] pnp: Device 00:0a activated.
[17179574.448000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179574.448000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179574.448000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179574.448000] mice: PS/2 mouse device common for all mice
[17179574.448000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.448000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.448000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.448000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179574.456000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.456000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.456000] EISA: Probing bus 0 at eisa.0
[17179574.456000] Cannot allocate resource for EISA slot 1
[17179574.456000] Cannot allocate resource for EISA slot 2
[17179574.456000] Cannot allocate resource for EISA slot 3
[17179574.456000] Cannot allocate resource for EISA slot 4
[17179574.456000] Cannot allocate resource for EISA slot 5
[17179574.456000] Cannot allocate resource for EISA slot 6
[17179574.456000] Cannot allocate resource for EISA slot 7
[17179574.456000] Cannot allocate resource for EISA slot 8
[17179574.456000] EISA: Detected 0 cards.
[17179574.456000] TCP bic registered
[17179574.456000] NET: Registered protocol family 1
[17179574.456000] NET: Registered protocol family 8
[17179574.456000] NET: Registered protocol family 20
[17179574.456000] Using IPI Shortcut mode
[17179574.456000] ACPI: (supports S0 S3 S4 S5)
[17179574.456000] Freeing unused kernel memory: 288k freed
[17179574.464000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.828000] Capability LSM initialized
[17179576.044000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179576.044000] ACPI: Processor [CPU] (supports 8 throttling states)
[17179576.044000] ACPI: Thermal Zone [THM0] (45 C)
[17179576.928000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179576.928000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.928000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179576.928000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179576.928000] ICH4: chipset revision 1
[17179576.928000] ICH4: not 100% native mode: will probe irqs later
[17179576.928000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179576.928000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179576.928000] Probing IDE interface ide0...
[17179577.220000] hda: ST980815A, ATA DISK drive
[17179577.892000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.928000] Probing IDE interface ide1...
[17179578.664000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, ATAPI CD/DVD-ROM drive
[17179579.000000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.012000] hda: max request size: 512KiB
[17179579.028000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179579.032000] hda: cache flushes supported
[17179579.032000]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 >
[17179579.112000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.112000] Uniform CD-ROM driver Revision: 3.20
[17179580.228000] usbcore: registered new driver usbfs
[17179580.228000] usbcore: registered new driver hub
[17179580.232000] USB Universal Host Controller Interface driver v3.0
[17179580.232000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179580.232000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179580.232000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179580.232000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179580.232000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[17179580.232000] usb usb1: configuration #1 chosen from 1 choice
[17179580.232000] hub 1-0:1.0: USB hub found
[17179580.232000] hub 1-0:1.0: 2 ports detected
[17179580.336000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179580.336000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179580.336000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179580.336000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179580.336000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179580.336000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[17179580.336000] usb usb2: configuration #1 chosen from 1 choice
[17179580.336000] hub 2-0:1.0: USB hub found
[17179580.336000] hub 2-0:1.0: 2 ports detected
[17179580.440000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179580.440000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179580.440000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179580.440000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179580.440000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[17179580.440000] usb usb3: configuration #1 chosen from 1 choice
[17179580.440000] hub 3-0:1.0: USB hub found
[17179580.440000] hub 3-0:1.0: 2 ports detected
[17179580.548000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[17179580.548000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[17179580.548000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179580.548000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179580.548000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179580.548000] ehci_hcd 0000:00:1d.7: debug port 1
[17179580.548000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179580.548000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[17179580.552000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.552000] usb usb4: configuration #1 chosen from 1 choice
[17179580.552000] hub 4-0:1.0: USB hub found
[17179580.552000] hub 4-0:1.0: 6 ports detected
[17179581.072000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179581.072000] EXT3-fs: write access will be enabled during recovery.
[17179585.892000] kjournald starting.  Commit interval 5 seconds
[17179585.892000] EXT3-fs: hda5: orphan cleanup on readonly fs
[17179585.892000] ext3_orphan_cleanup: deleting unreferenced inode 104582
[17179585.908000] ext3_orphan_cleanup: deleting unreferenced inode 66142
[17179585.916000] EXT3-fs: hda5: 2 orphan inodes deleted
[17179585.916000] EXT3-fs: recovery complete.
[17179585.956000] EXT3-fs: mounted filesystem with ordered data mode.
[17179600.172000] Linux agpgart interface v0.101 (c) Dave Jones
[17179600.176000] agpgart: Detected an Intel 855PM Chipset.
[17179600.192000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179600.988000] Real Time Clock Driver v1.12ac
[17179601.088000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179601.124000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179601.172000] hw_random hardware driver 1.0.0 loaded
[17179601.356000] Floppy drive(s): fd0 is 1.44M
[17179601.372000] FDC 0 is a National Semiconductor PC87306
[17179601.512000] input: PC Speaker as /class/input/input1
[17179602.008000] parport: PnPBIOS parport detected.
[17179602.008000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[17179602.788000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179602.788000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[17179602.788000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179602.788000] Yenta: Routing CardBus interrupts to PCI
[17179602.788000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[17179602.848000] irda_init()
[17179602.848000] NET: Registered protocol family 23
[17179602.928000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17179602.944000] input: TPPS/2 IBM TrackPoint as /class/input/input2
[17179603.028000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179603.028000] Socket status: 30000086
[17179603.028000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[17179603.028000] cs: IO port probe 0x4000-0x8fff: clean.
[17179603.028000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179603.028000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[17179603.032000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179603.032000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179603.032000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179603.032000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
[17179603.032000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179603.032000] Yenta: Routing CardBus interrupts to PCI
[17179603.032000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
[17179603.264000] Yenta: ISA IRQ mask 0x0418, PCI irq 5
[17179603.264000] Socket status: 30000086
[17179603.264000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[17179603.264000] cs: IO port probe 0x4000-0x8fff: clean.
[17179603.264000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179603.264000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[17179603.444000] ts: Compaq touchscreen protocol output
[17179603.560000] Intel(R) PRO/1000 Network Driver - version 7.1.9-k4
[17179603.560000] Copyright (c) 1999-2006 Intel Corporation.
[17179603.580000] pnp: Device 00:0c activated.
[17179603.580000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[17179603.580000] nsc-ircc, chip->init
[17179603.580000] nsc-ircc, Found chip at base=0x02e
[17179603.580000] nsc-ircc, driver loaded (Dag Brattli)
[17179603.580000] IrDA: Registered device irda0
[17179603.580000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[17179603.620000] ath_hal: module license 'Proprietary' taints kernel.
[17179603.620000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179603.676000] wlan: 0.8.4.2 (0.9.2.1)
[17179603.680000] ath_rate_sample: 1.2 (0.9.2.1)
[17179603.688000] ath_pci: 0.9.4.5 (0.9.2.1)
[17179603.852000] intel8x0_measure_ac97_clock: measured 55382 usecs
[17179603.852000] intel8x0: clocking to 48000
[17179603.852000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179604.112000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:83:8f:1c
[17179604.148000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179604.148000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179604.656000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179604.656000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179604.656000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179604.656000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179604.656000] wifi0: mac 5.9 phy 4.3 radio 4.6
[17179604.656000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179604.656000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179604.656000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179604.656000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179604.656000] wifi0: Use hw queue 8 for CAB traffic
[17179604.656000] wifi0: Use hw queue 9 for beacons
[17179604.764000] wifi0: Atheros 5212: mem=0xc0210000, irq=11
[17179605.672000] cs: IO port probe 0x100-0x3af: clean.
[17179605.672000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179605.672000] cs: IO port probe 0x820-0x8ff: clean.
[17179605.672000] cs: IO port probe 0xc00-0xcf7: clean.
[17179605.672000] cs: IO port probe 0xa00-0xaff: clean.
[17179605.676000] cs: IO port probe 0x100-0x3af: clean.
[17179605.676000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179605.676000] cs: IO port probe 0x820-0x8ff: clean.
[17179605.676000] cs: IO port probe 0xc00-0xcf7: clean.
[17179605.676000] cs: IO port probe 0xa00-0xaff: clean.
[17179605.828000] lp0: using parport0 (interrupt-driven).
[17179605.924000] Adding 1020088k swap on /dev/disk/by-uuid/144fc1b6-07da-4d70-a1a6-1f53984b5fb6.  Priority:-1 extents:1 across:1020088k
[17179606.148000] EXT3 FS on hda5, internal journal
[17179606.316000] NET: Registered protocol family 17
[17179606.436000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179606.436000] md: bitmap version 4.39
[17179606.720000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179612.128000] NET: Registered protocol family 10
[17179612.128000] lo: Disabled Privacy Extensions
[17179612.132000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179612.132000] IPv6 over IPv4 tunneling driver
[17179614.228000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179614.320000] NTFS volume version 3.1.


---

### Post by becatlibra on 2007-01-22
I can't post the /var/log/Xorg.0.log because it is too long

---

### Post by becatlibra on 2007-01-22
> **IntuitiveNipple said:**
> Sorry, yes... for us on Ubuntu it is **/etc/modprobe.d/** - I pasted in the solution the other user found. I know how frustrating it is - it turned out to be a simple solution on the i810 - the **DefaultDepth** (bits-per-pixel) had to be set to 16 in **xorg.conf** to enable DRI.

My default depth is set to 16 so that's a no go.

As for the aliases file, as I said it doesn't contain any of those 3 you mentioned.

I don't have the Knoppix CD on me and my cd burner in my laptop died.  It won't work in either Windows or Linux.  Any way those files I posted help?  I could only post the one.  The other was too long to post but I think that may be the one that contains the most helpful info.  I could run it through grep if there is something in particular you might be looking for.

Thanks again for the time

---

### Post by IntuitiveNipple on 2007-01-22
The Xorg.0.log file is the more important of the two - can you attach it to a post here in the forums? I don't see anything related to your video card in the boot log.

The Paste-Bin is a service for people to post large text files for a short period so others can view them without cluttering up forums, live chat sessions, etc., with screen-fulls of data. 

You enter a (nick) name, paste your text, and press the Paste! button. Your paste page appears and you simply copy the URL into any messages you want to refer to it from. A day or so later the data is deleted.

---

### Post by becatlibra on 2007-01-24
> **IntuitiveNipple said:**
> The Xorg.0.log file is the more important of the two - can you attach it to a post here in the forums? I don't see anything related to your video card in the boot log.

The Paste-Bin is a service for people to post large text files for a short period so others can view them without cluttering up forums, live chat sessions, etc., with screen-fulls of data. 

You enter a (nick) name, paste your text, and press the Paste! button. Your paste page appears and you simply copy the URL into any messages you want to refer to it from. A day or so later the data is deleted.

Okay Here is the link [http://paste.ubuntu-nl.org/2821/](http://paste.ubuntu-nl.org/2821/)  How long is it up for?


Thanks again for your time

---

### Post by CowzRule on 2007-01-24
What is telling you that you're not getting direct rendering?
According to your Xorg.0.log file, I see the line> 301    (==) AIGLX enabledand> 808    (II) RADEON(0): Direct rendering enabledWhat to you get from```
glxinfo | grep render
``` and maybe post a copy of your xorg.conf file also.

---

### Post by talkingwires on 2007-01-25
> **IntuitiveNipple said:**
> I don't have that chip-set, but I've successfully solved a similar issue (twice) for Intel i810 (i815) chip-sets.Best. Username. Evar.

Anyway, I have a Dell Latitude 640 with the same ATI 7500 chipset. I spent two weeks trying to get get Edgy and DRI working on the damned thing, and was about to give up when I booted the Dapper Live CD, changed the driver to "radeon", and it worked. Shocked, I booted Edgy's Live CD, and it worked, too. One fresh install later, and I had OpenGL and Compiz working fine.

I had tried every tweak I found on these forums and on Google to get it working, but in the end, the *only* thing I had to do was change the driver from "ati" to "radeon" and restart X. Going back through my xorg.conf file, commenting out each change and restarting, I found that several of the changes recommended killed DRI, even while letting X boot normally. Especially those related to the AGP settings. So, try running dpkg to reconfigure X and get a fresh xorg.conf, set the driver to "radeon", and restart. Hopefully, that'll get you up and running.

---

### Post by becatlibra on 2007-01-25
glxinfo | grep render is what is showing me that direct rendering is NOT working.

On my lunch hour (or possibly when I go home) I will post my xorg.conf.

Radeon is set to be the driver.  I have tried it without any options and also with 10+ options (which I gleaned from many other posts.)

Thanks again for your help guys.  I will post the xorg.conf up here.

Well I suppose first I should run dpkg to reconfigure X.  What would the context of this be?  dpkg-reconfigure xserver-xorg?  Is that right?

---

### Post by CowzRule on 2007-01-25
> **becatlibra said:**
> glxinfo | grep render is what is showing me that direct rendering is NOT working.

On my lunch hour (or possibly when I go home) I will post my xorg.conf.

Radeon is set to be the driver.  I have tried it without any options and also with 10+ options (which I gleaned from many other posts.)

Thanks again for your help guys.  I will post the xorg.conf up here.

Well I suppose first I should run dpkg to reconfigure X.  What would the context of this be?  dpkg-reconfigure xserver-xorg?  Is that right?

Yea, dpkg-reconfigure xserver-xorg is correct, just don't forget the "sudo".
Also, don't know if you tried, but you can get fglrx drivers from ati/amd for the last year.
[http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html]("http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html")

---

### Post by ushaba on 2007-01-25
this may sound strange, but i'm pretty sure i was getting direct acceleration with the basic ati driver on the livecd too. i know i know... but i was completely sober and just as baffled as anyone else. that said, the radeon driver never fails. as soon as you've got it working though, you'll be tweaking the x.org config file again for fps boosts in glxgears... 
cheers

---

### Post by becatlibra on 2007-01-25
> **CowzRule said:**
> Yea, dpkg-reconfigure xserver-xorg is correct, just don't forget the "sudo".
Also, don't know if you tried, but you can get fglrx drivers from ati/amd for the last year.
[http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html]("http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html")

fglrx doesn't support the 7500 -

---

### Post by becatlibra on 2007-01-25
Okay - I went to a console session and ran sudo dpkg-reconfigure xserver-org (it wouldn't work in a terminal window) and rebooted.  Then I checked and still no direct.  Then I changed the driver to radeon, rebooted and still nothing.

Argh!  This has been REALLY frustrating.  I had knoppix on there and it worked GREAT.  I reinstalled with ubuntu because I thought I'd try something new.

Here is my output:

GLXINFO: [http://paste.ubuntu-nl.org/2892/](http://paste.ubuntu-nl.org/2892/)

/var/log/Xorg.0.log: [http://paste.ubuntu-nl.org/2893/](http://paste.ubuntu-nl.org/2893/)

/etc/X11/xorg.conf : [http://paste.ubuntu-nl.org/2894/](http://paste.ubuntu-nl.org/2894/)

/var/log/dmesg : [http://paste.ubuntu-nl.org/2897/](http://paste.ubuntu-nl.org/2897/)

Please have a look and tell me what you think.   Thanks

---

### Post by becatlibra on 2007-01-25
Both knoppix and ubuntu dapper live cds have direct on when loaded.  

both using the "ati" driver  what the hell am I doing wrong??  HELP?

please?

---

### Post by CowzRule on 2007-01-25
> **becatlibra said:**
> Both knoppix and ubuntu dapper live cds have direct on when loaded.  

both using the "ati" driver  what the hell am I doing wrong??  HELP?

please?

Did you install Dapper then upgrade to Edgy? The reason I ask is that in your /var/log/Xorg.0.log it says that AiGLX is enabled. Dapper uses an older version of XOrg which doesn't have AiGLX. I'm thinking this is what is causing your problem. You could try disabling AiGLX by adding the following to the bottom of your xorg.conf file```
Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection
```and reboot. Then check glxinfo. If it works, great, but if it doesn't, I'm thinking you're going to have to reinstall Dapper and stick with it (don't upgrade to edgy).

---

### Post by becatlibra on 2007-01-26
Damn Damn Damn

No - Not reinstalling!  Argh.

I tried the option you suggested twice, once with ati and once with radeon drivers with default color depth set to 16.

Yes I went from dapper to edgy but the thing is it never worked in Dapper.  

I have heavily modded this install - installing many applications, etc.  I don't want to have to reinstall everything again and setup all the file-type associations, etc again.  Get all the mozilla plugins ... blah, blah, blah 

PLEASE - IT HAS TO BE FIXABLE WITHOUT A REINSTALL?!?  It's not windoze for cryin out loud!  :)

More help PLEASE? pretty Please?

---

### Post by becatlibra on 2007-01-29
Bump - PleasE?  Any other Ideas?  This is a dualboot system and It took me forever to get everything tweaked the way I needed it with the special work software we use, etc.

If it works with all the live cds then can't SOMEONE help me with figuring out what is wrong here?  I am at a loss


Is it possible to run some sort of REPAIR installation so I don't lose everything?

Thanks

Benjamin

---

### Post by finferflu on 2007-02-13
Hi,
I've had many troubles getting direct rendering to work with my Mobility Radeon 7500, then I followed [this guide]("https://help.ubuntu.com/community/RadeonDriver"), after running sudo dpkg-reconfigure xserver-xorg, choosing ATI as driver, and leaving the other options in default mode (apart from keyboard layout). 

I hope it helps.

---

### Post by GoingDown on 2007-02-13
Please run lsmod and see if you have radeon kernel module loaded or not?

---

### Post by finferflu on 2007-02-13
I'm not sure, but I think it is:

> Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  3 
drm                    74644  4 radeon
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
ipv6                  272288  10 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  2 
ndiswrapper           204436  0 
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
lp                     12964  0 
joydev                 11200  0 
pcmcia                 40380  0 
8139cp                 24832  0 
snd_intel8x0           34844  2 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
tsdev                   9152  0 
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19584  2 snd_pcm_oss
8139too                29056  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
quickcam               75172  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mii                     6912  2 8139cp,8139too
videodev               10752  1 quickcam
usbhid                 45152  0 
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  2 snd
psmouse                41352  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4352  0 
serio_raw               8452  0 
evdev                  11392  4 
wbsd                   20488  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
floppy                 63044  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
mmc_core               32136  1 wbsd
ext3                  142728  2 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  6 ndiswrapper,quickcam,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  4 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by GoingDown on 2007-02-14
Yes, it seems to be there.

Have you ever tried to install ATI proprietary fglrx drivers? If yes, they should be uninstalled (with /usr/share/ati/fglrx-uninstall.sh) or radeon opengl acceleration doesn't work properly.

---

### Post by finferflu on 2007-02-14
Sorry, my mistake. I guess your question was addressed to the thread starter, not to me. I had answered you because I had thought you were the thread starter...
Well, AIGLX works for me, and I was suggesting the thread starter the guide I have used...

Sorry about that :D

---

### Post by ness0216 on 2007-02-14
I've had the same issues. Here's what worked for me. Hope this helps.
[http://ubuntuforums.org/showthread.php?t=361136](http://ubuntuforums.org/showthread.php?t=361136)

---

### Post by Jim March on 2007-03-24
I have another laptop with the infamous Radeon 7500 Mobility - mine is the Compaq Evo N610c with a high-res 1400x1050 LCD, damn near a worst-case scenario.

Somebody on the Feisty development board turned me on to a recipe that flat-out rocks - 1200fps in GLXGEARS, the highest I've EVER gotten and then I had Feisty's 3D desktop up briefly as a test (I don't want to push my luck TOO far though!).

Here's the combination:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
#	Driver		"fbdev"
#	Option		"Rotate" "CCW"
	BusID		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps" "true"
#	Option		"AllowGLXWithComposite" "true"
#	Option    "BIOSHotkeys" "on"
	Option    "ColorTiling"   "on"
	Option		"DynamicClocks"	"on"
	Option		"AGPMode"	"4"
	Option		"AGPFastWrite"	"yes"
        Option     "EnableDepthMoves"          "yes"
        Option     "EnablePageFlip"             "yes"
	Option          "Accel"
#	Option "AccelMethod" "EXA"
	Option "RenderAccel" "false"
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "Dac8Bit"                   # [<bool>]
        #Option     "ForcePCIMode"              # [<bool>]
        #Option     "BusType"                   # [<str>]
        #Option     "CPPIOMode"                 # [<bool>]
        #Option     "CPusecTimeout"             # <i>
        #Option     "AGPSize"                   # <i>
        #Option     "GARTSize"                  # <i>
        #Option     "RingSize"                  # <i>
        #Option     "BufferSize"                # <i>
        #Option     "NoBackBuffer"              # [<bool>]
        #Option     "DRIReinit"                 # [<bool>]
        #Option     "PanelOff"                  # [<bool>]
        #Option     "DDCMode"                    "yes"
        #Option     "MonitorLayout"             # [<str>]
        #Option     "IgnoreEDID"                # [<bool>]
        #Option     "OverlayOnCRTC2"            # [<bool>]
        #Option     "CloneMode"                 # [<str>]
        #Option     "CloneHSync"                # [<str>]
        #Option     "CloneVRefresh"             # [<str>]
	#Option     "UseFBDev"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "DisplayPriority"           # [<str>]
        #Option     "PanelSize"                 # [<str>]
        #Option     "ForceMinDotClock"          # <freq>
EndSection

Section "Monitor"
	Identifier	"Standard Skærm"
	Option		"DPMS"
	Option		"BlankTime" "0"
	Option		"StandbyTime" "0"
	Option		"SuspendTime" "0"
	Option		"OffTime" "7"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Standard Skærm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024"  "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option "AIGLX"	"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option	"Composite"	"Enable"
EndSection
```

To get this running on a different laptop: you'll have to splice your "imputdevices" stuff from your xorg.conf file into this!!!  You may also have to tweak some "serverlayout" inputdevice stuff to match actual "inputdevices" you have.  When I ran the original version of this from an IBM T42 my keyboard layout went wonky - things like the asterisk were skewed one over.

ALSO: the "font directory" stuff might be Feisty-specific and you'll have to splice in your Edgy section.  Dunno.  Shouldn't affect performance though.

The other part of this recipe was a file called /etc/drirc and I'll be damned if I know what it does - here it is though:

```
<driconf>
    <device screen="0" driver="radeon">
        <application name="all">
            <option name="hyperz" value="true" />
            <option name="tcl_mode" value="0" />
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>
```

I wish I could credit the guy who turned me onto this on the Feisty forum but the whole thread has been deleted, presumable since it's not Fiesty-specific enough?

---

