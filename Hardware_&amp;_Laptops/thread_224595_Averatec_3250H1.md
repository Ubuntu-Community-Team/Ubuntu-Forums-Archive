---
title: "Averatec 3250H1"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by spazsui on 2006-07-28
Hello!  Hopefully someone can help me.  I bought this laptop because what I have read on the internet that this was a good laptop for Ubuntu.  Everything just seems to work but from what I read it was with Breezy 5.10.  I got the laptop 2 days ago and installed Dapper 6.06 and everything does seem to work except internet access.  I can't seem to connect using the ethernet connection.  I am using a cable modem and it works fine with Dapper on a Dell Dimension 3000 but not the laptop.  Everything I read at LinuxOnLaptops said it would work fine but like I said that was with Breezy. Anyway, the hardware seems to be recognized but I have no access.  Any suggestions?  I am a total newbie so if there is a solution I will have to be walked through it step by step.   Please help!

---

### Post by wiresquire on 2006-07-28
I'm assuming your connecting from your laptop to the cable modem by wire and not wireless.

When you say the internet is not working, does that mean you can't get email, can't get to eg google in firefox or anything?

For the easiest approach, from the menu, open System/Administration/Networking.
Do you have an Ethernet connection showing on the Connections tab? Does it show as active? Right click on it and select properties. Is it using DHCP? Should it be using DHCP or are you required to fill out that information?
You also might try deactivating it, and then reactivating it.

If that doesn't work, here's some things to try to get us some more information:
From the terminal (Applications/Accessories/Terminal) do:
 lspci
-->This will give us the information on what network adapters and other hardware you have.

 ifconfig
-->This will show us the 'state' of your network adapters

 route
-->This will show us if your laptop thinks it is connected to something else

 dmesg|grep -i eth
-->This will show us what's happening with network adapters when your machine boots.

Post the information back here and we'll take it from there. It's good to post the above using the code tags

---

### Post by FamuLinux on 2006-07-28
Ok, I *just* got my wired connection (eth0)up and running.
I am running the Dapper Drake release 6.06 on an Averatec 3250HX-01.

The install went off without a hitch but when I tried to go online and download the updates, the monkey started flinging poo in my eye!

To make a long story (about 3 days of work) short, this is what happened:

1. The Dapper release basically caused a regression fault that the developers aren't really worried about at the moment.

2. There are a couple ways mentioned to fix it, but they involve messing with the kernel modules and power management which I don't recommend.

*Solution*

When you boot up hit [ESC] before the Ubuntu splash screen loads. This will take you to the Grub bootloader menu. Hit 'E' to edit the boot configuration. Highlight the entry that corresponds to your kerel. Hit 'E' to edit it. At the very end add 'irqpoll' without the single quotes. Hit [Enter] to save the change. This will take you back to the original Grub boot screen. Press 'B' to boot and normal booting will resume. This is a one-time temporary change. When you log in, you should now be able to use the graphical network config tools to set your IP, DNS, Gateway, etc... If this works, you can make it permanent by editing: /boot/grub/menu.lst

Scroll down until you find the entry that matches the one you changed from the Grub bootloader screen. Simply add 'irqpoll' and save the file. 

All is right with the world once more.

---

### Post by spazsui on 2006-07-30
Wiresquire, Okay, thanks for helping me out.  Here's is the information you requested.  I tried going into the system and I deactivated it and reactivated it.  No luck still no connection.  It was set as DCHP also which is what it's suppose to be.  If this doesn't work I'm going to try what Farmulinux suggested.  Anyway, here is the info you requested it.

jp2@jp2-laptop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:09.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

jp2@jp2-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:19:EA:1E
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:5451 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

jp2@jp2-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (013c2000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1658.913 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.621000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294670.622000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.640000] Memory: 476468k/491456k available (1976k kernel code, 14388k reserved, 606k data, 288k init, 0k highmem)
[4294670.640000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.701000] Calibrating delay using timer specific routine.. 3320.00 BogoMIPS (lpj=1660003)
[4294670.701000] Security Framework v1.0.0 initialized
[4294670.701000] SELinux:  Disabled at boot.
[4294670.701000] Mount-cache hash table entries: 512
[4294670.701000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294670.701000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294670.701000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294670.701000] CPU: L2 Cache: 512K (64 bytes/line)
[4294670.701000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000020 00000000 00000000 00000000
[4294670.701000] mtrr: v2.0 (20020519)
[4294670.701000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294670.701000] Enabling fast FPU save and restore... done.
[4294670.701000] Enabling unmasked SIMD FPU exception support... done.
[4294670.701000] Checking 'hlt' instruction... OK.
[4294670.705000] checking if image is initramfs... it is
[4294671.371000] Freeing initrd memory: 6836k freed
[4294671.389000] ACPI: Looking for DSDT ... not found!
[4294671.391000] ACPI: setting ELCR to 0200 (from 0c00)
[4294671.403000] NET: Registered protocol family 16
[4294671.403000] EISA bus registered
[4294671.403000] ACPI: bus type pci registered
[4294671.404000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294671.404000] PCI: Using configuration type 1
[4294671.404000] ACPI: Subsystem revision 20051216
[4294671.409000] ACPI: Interpreter enabled
[4294671.409000] ACPI: Using PIC for interrupt routing
[4294671.410000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.410000] PCI: Probing PCI hardware (bus 00)
[4294671.411000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294671.411000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294671.411000] Boot video device is 0000:01:00.0
[4294671.411000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.416000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294671.417000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294671.418000] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *11 14 15)
[4294671.418000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 5 9 14 15) *0, disabled.
[4294671.418000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12)
[4294671.418000] ACPI: PCI Interrupt Link [LNKD] (IRQs 6 7) *0, disabled.
[4294671.419000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.419000] pnp: PnP ACPI init
[4294671.420000] pnp: PnP ACPI: found 8 devices
[4294671.420000] PnPBIOS: Disabled by ACPI PNP
[4294671.420000] PCI: Using ACPI for IRQ routing
[4294671.420000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.423000] PCI: Bridge: 0000:00:01.0
[4294671.423000]   IO window: disabled.
[4294671.423000]   MEM window: dde00000-dfefffff
[4294671.423000]   PREFETCH window: d5d00000-ddcfffff
[4294671.423000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294671.423000]   IO window: 00001000-000010ff
[4294671.423000]   IO window: 00001400-000014ff
[4294671.423000]   PREFETCH window: 20000000-21ffffff
[4294671.423000]   MEM window: 22000000-23ffffff
[4294671.423000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.423000] **** SET: Misaligned resource pointer: dd9ee6e2 Type 07 Len 0
[4294671.424000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294671.424000] PCI: setting IRQ 10 as level-triggered
[4294671.424000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294671.424000] audit: initializing netlink socket (disabled)
[4294671.424000] audit(1154302789.423:1): initialized
[4294671.424000] VFS: Disk quotas dquot_6.5.1
[4294671.424000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.424000] Initializing Cryptographic API
[4294671.424000] io scheduler noop registered
[4294671.424000] io scheduler anticipatory registered
[4294671.424000] io scheduler deadline registered
[4294671.424000] io scheduler cfq registered
[4294671.425000] isapnp: Scanning for PnP cards...
[4294671.782000] isapnp: No Plug & Play device found
[4294671.796000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.798000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294671.799000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294671.799000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294671.799000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294671.799000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294671.800000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.800000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.802000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.802000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.802000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.802000] mice: PS/2 mouse device common for all mice
[4294671.803000] EISA: Probing bus 0 at eisa.0
[4294671.803000] Cannot allocate resource for EISA slot 1
[4294671.803000] EISA: Detected 0 cards.
[4294671.803000] NET: Registered protocol family 2
[4294671.813000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294671.813000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.813000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.813000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.813000] TCP reno registered
[4294671.813000] TCP bic registered
[4294671.813000] NET: Registered protocol family 1
[4294671.813000] NET: Registered protocol family 8
[4294671.813000] NET: Registered protocol family 20
[4294671.813000] Using IPI Shortcut mode
[4294671.813000] ACPI wakeup devices:
[4294671.813000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294671.813000] ACPI: (supports S0 S3 S4 S5)
[4294671.813000] Freeing unused kernel memory: 288k freed
[4294671.869000] vga16fb: initializing
[4294671.869000] vga16fb: mapped to 0xc00a0000
[4294671.961000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.009000] Console: switching to colour frame buffer device 80x25
[4294672.009000] fb0: VGA16 VGA frame buffer device
[4294673.101000] Capability LSM initialized
[4294673.137000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294673.160000] ACPI: Thermal Zone [THRM] (0 C)
[4294673.584000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294673.584000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294673.584000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[4294673.584000] VP_IDE: chipset revision 6
[4294673.584000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.584000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294673.584000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294673.584000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294673.584000] Probing IDE interface ide0...
[4294673.970000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294674.276000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.299000] Probing IDE interface ide1...
[4294675.093000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294675.705000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.712000] hda: max request size: 1024KiB
[4294675.721000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294675.721000] hda: cache flushes supported
[4294675.721000]  hda: hda1 hda2 < hda5 >
[4294675.783000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294675.783000] Uniform CD-ROM driver Revision: 3.20
[4294676.100000] usbcore: registered new driver usbfs
[4294676.100000] usbcore: registered new driver hub
[4294676.102000] USB Universal Host Controller Interface driver v2.3
[4294676.102000] **** SET: Misaligned resource pointer: ddd665e2 Type 07 Len 0
[4294676.102000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[4294676.102000] PCI: setting IRQ 7 as level-triggered
[4294676.102000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294676.102000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 7
[4294676.102000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294676.103000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294676.103000] uhci_hcd 0000:00:10.0: irq 7, io base 0x0000e400
[4294676.103000] hub 1-0:1.0: USB hub found
[4294676.103000] hub 1-0:1.0: 2 ports detected
[4294676.204000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294676.204000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 7
[4294676.204000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294676.204000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294676.204000] uhci_hcd 0000:00:10.1: irq 7, io base 0x0000e800
[4294676.204000] hub 2-0:1.0: USB hub found
[4294676.204000] hub 2-0:1.0: 2 ports detected
[4294676.305000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294676.305000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 7
[4294676.305000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294676.305000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294676.305000] uhci_hcd 0000:00:10.2: irq 7, io base 0x0000ec00
[4294676.305000] hub 3-0:1.0: USB hub found
[4294676.305000] hub 3-0:1.0: 2 ports detected
[4294676.408000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294676.408000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 7
[4294676.408000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294676.408000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294676.408000] ehci_hcd 0000:00:10.3: irq 7, io mem 0xdfffdf00
[4294676.408000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.408000] hub 4-0:1.0: USB hub found
[4294676.408000] hub 4-0:1.0: 6 ports detected
[4294676.653000] Attempting manual resume
[4294676.723000] EXT3-fs: mounted filesystem with ordered data mode.
[4294676.737000] kjournald starting.  Commit interval 5 seconds
[4294690.445000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.451000] agpgart: Detected VIA KM400/KM400A chipset
[4294690.456000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294690.602000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294690.608000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294690.953000] **** SET: Misaligned resource pointer: dd5c0b22 Type 07 Len 0
[4294690.953000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294690.953000] PCI: setting IRQ 11 as level-triggered
[4294690.953000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294690.953000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294691.097000] irda_init()
[4294691.097000] NET: Registered protocol family 23
[4294691.111000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294691.111000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294691.115000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294691.116000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[4294691.276000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294691.277000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294691.297000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294691.297000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294691.371000] Real Time Clock Driver v1.12
[4294691.372000] input: PC Speaker as /class/input/input1
[4294691.571000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294691.571000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294691.571000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294691.571000] Yenta O2: enabling read prefetch/write burst
[4294691.693000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[4294691.693000] Socket status: 30000007
[4294691.909000] eth0: link down
[4294692.024000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294692.063000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294692.294000] cs: IO port probe 0x100-0x3af: clean.
[4294692.296000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294692.297000] cs: IO port probe 0x820-0x8ff: clean.
[4294692.297000] cs: IO port probe 0xc00-0xcf7: clean.
[4294692.298000] cs: IO port probe 0xa00-0xaff: clean.
[4294692.630000] ts: Compaq touchscreen protocol output
[4294692.976000] NET: Registered protocol family 17
[4294693.137000] lp: driver loaded but no devices found
[4294693.200000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294693.334000] EXT3 FS on hda1, internal journal
[4294693.530000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294693.530000] md: bitmap version 4.39
[4294694.142000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.797000] cdrom: open failed.
[4294701.017000] ACPI: AC Adapter [AC] (on-line)
[4294701.083000] ACPI: Battery Slot [BAT0] (battery present)
[4294701.151000] ACPI: Power Button (FF) [PWRF]
[4294701.151000] ACPI: Power Button (CM) [PWRB]
[4294701.151000] ACPI: Sleep Button (CM) [SLPB]
[4294701.151000] ACPI: Lid Switch [LIDD]
[4294701.288000] ibm_acpi: ec object not found
[4294701.314000] pcc_acpi: loading...
[4294701.414000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294701.852000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294701.857000] Detected 1659.162 MHz processor.
[4294701.861000] powernow: SGTC: 13333
[4294701.861000] powernow: Minimum speed 398 MHz. Maximum speed 1659 MHz.
[4294706.074000] [drm] Initialized drm 1.0.1 20051102
[4294706.092000] **** SET: Misaligned resource pointer: d9a09522 Type 07 Len 0
[4294706.093000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[4294706.093000] PCI: setting IRQ 9 as level-triggered
[4294706.093000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4294706.094000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 9
[4294706.094000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294706.095000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294706.610000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294706.610000] agpgart: Device is in legacy mode, falling back to 2.x
[4294706.610000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294706.610000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294707.820000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294707.820000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294707.820000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294707.820000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294707.820000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294707.820000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294707.820000]  [<c0121520>] __do_softirq+0x30/0xb0
[4294707.820000]  [<c01215d5>] do_softirq+0x35/0x40
[4294707.820000]  [<c0121685>] irq_exit+0x35/0x40
[4294707.820000]  [<c010597f>] do_IRQ+0x1f/0x30
[4294707.820000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294707.820000] handlers:
[4294707.820000] [<de94e6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294707.820000] Disabling IRQ #11
[4294709.366000] ppdev: user-space parallel port driver
[4294709.693000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294709.693000] apm: overridden by ACPI.
[4294710.408000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294713.069000] Bluetooth: Core ver 2.8
[4294713.069000] NET: Registered protocol family 31
[4294713.069000] Bluetooth: HCI device and connection manager initialized
[4294713.069000] Bluetooth: HCI socket layer initialized
[4294713.172000] Bluetooth: L2CAP ver 2.8
[4294713.172000] Bluetooth: L2CAP socket layer initialized
[4294713.204000] Bluetooth: RFCOMM socket layer initialized
[4294713.204000] Bluetooth: RFCOMM TTY layer initialized
[4294713.204000] Bluetooth: RFCOMM ver 1.7
[4294730.155000] NET: Registered protocol family 10
[4294730.155000] lo: Disabled Privacy Extensions
[4294730.155000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4294730.156000] IPv6 over IPv4 tunneling driver
[4295016.049000] ibm_acpi: ec object not found
[4299763.590000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4299763.590000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4299763.590000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4299763.590000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4299763.590000]  [<c010597a>] do_IRQ+0x1a/0x30
[4299763.590000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4299763.590000]  [<c0121520>] __do_softirq+0x30/0xb0
[4299763.590000]  [<c01215d5>] do_softirq+0x35/0x40
[4299763.590000]  [<c0121685>] irq_exit+0x35/0x40
[4299763.590000]  [<c010597f>] do_IRQ+0x1f/0x30
[4299763.590000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4299763.590000]  [<c013ea7c>] setup_irq+0x9c/0x120
[4299763.590000]  [<de94e6f0>] rhine_interrupt+0x0/0x240 [via_rhine]
[4299763.590000]  [<c013ec5b>] request_irq+0x7b/0xa0
[4299763.590000]  [<de94e2e2>] rhine_open+0x32/0xf0 [via_rhine]
[4299763.590000]  [<de94e6f0>] rhine_interrupt+0x0/0x240 [via_rhine]
[4299763.590000]  [<c027eebe>] dev_open+0x2e/0x80
[4299763.590000]  [<c0280740>] dev_change_flags+0xe0/0x130
[4299763.590000]  [<c02c714e>] devinet_ioctl+0x57e/0x5f0
[4299763.590000]  [<c0172ed2>] do_ioctl+0x22/0x80
[4299763.590000]  [<c01730b1>] vfs_ioctl+0x51/0x1f0
[4299763.590000]  [<c01732ad>] sys_ioctl+0x5d/0x90
[4299763.590000]  [<c010302b>] sysenter_past_esp+0x54/0x79
[4299763.590000] handlers:
[4299763.590000] [<de94e6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4299763.590000] Disabling IRQ #11
[4299763.621000] eth0: link down
[4299763.621000] ADDRCONF(NETDEV_UP): eth0: link is not ready

I hope you can get a glimmer of what might be the problem.  Like I said I may try also what Farmulinux said but messing around with that kind of scares me.  I am a newb afterall.:confused:

---

### Post by wiresquire on 2006-07-31
Spazsui

The info that you provided suggests that the hardware is being detected OK, but the driver is not being loaded correctly.

Funnily enough, I have the same network card (different laptop).

From comparing info, the difference is in the line:
```

[4294691.116000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.

```
The Link should not be 0000...

Famulinux's instructions are perfectly safe. Just follow those instructions and add irqpoll to the end of the line: eg
```

*/boot/vmlinuz-2.6.15-26-k7* root=*/dev/hda4* ro quiet splash irqpoll

```
note that the things in italics may be different for you. That's OK, just leave them as you have them and add the irqpoll to the end.

If you happen to make a mistake, you will still be able to reboot and change it back. And you can always use the 'Recovery Mode' boot :cool: 

Let us know how you get on.

Good luck
ws

---

### Post by spazsui on 2006-07-31
Well people, didn't work.  Still can't get online.  I am at wits end now.  I followed the directions to a tee without screwing anything up.  Just no connection.  So what next?

---

### Post by wiresquire on 2006-08-01
OK, I think we have some options here, and it *feels* like one or more can surely work! I get the impression our time zones aren't matching too well. So please be patient. 

1. In looking back at the info you provided, I noticed that APIC was not enabled. There may be a configuration option in your BIOS settings to enable this, but we're going to try the lazy approach. Well, lazy for me :-D
The same instructions as Famulinux provided above, except we'll try 'lapic' instead of the 'irqpoll' from above. So your grub line should read
```

/boot/*vmlinuz-2.6.15-26-k7* root=*/dev/hda4* ro quiet splash lapic

```
(italics may be different for you - just leave everything as is)
That's LAPIC in lower case.

Let us know :
- as you're booting up, they should have some sort of version or release number for the BIOS. What does it say?
- did it fix it so network works :eek: 
- please post the dmesg output

2. I came across [this post](https://launchpad.net/distros/ubuntu/+source/linux-image-2.6.15-23-386/+bug/48263) in the bug forums. It's supposedly fixed, but you never know.

The same instructions as Famulinux provided above, except we'll try 'acpi=noirq' instead of the 'lapic' from above. So your grub line should read
```

/boot/*vmlinuz-2.6.15-26-k7* root=*/dev/hda4* ro quiet splash acpi=noirq

```
(italics may be different for you - just leave everything as is)

See if that works. Pls post the output of the dmesg for this.

3. By this stage you are a guru in editing grub boot options! So if the above doesn't work, please try adding lapic AND the irqpoll options at the same time!
I don't know if that will actually help, but I like trying some permutations ;-)

Again post the output of dmesg for this.

Good luck (again!)
ws

---

### Post by spazsui on 2006-08-01
Okay, here is all of the dmegs in the order that you suggested the fixes.  Sadly, none of them seemed to work.

jp2@jp2-laptop:~$ dmeg
bash: dmeg: command not found
jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash lapic
[4294667.296000] Local APIC disabled by BIOS -- reenabling.
[4294667.296000] Found and enabled local APIC!
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1658.742 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.333000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294669.334000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.352000] Memory: 476468k/491456k available (1976k kernel code, 14384k reserved, 606k data, 288k init, 0k highmem)
[4294669.352000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.412000] Calibrating delay using timer specific routine.. 3320.02 BogoMIPS (lpj=1660014)
[4294669.412000] Security Framework v1.0.0 initialized
[4294669.412000] SELinux:  Disabled at boot.
[4294669.412000] Mount-cache hash table entries: 512
[4294669.412000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294669.412000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294669.412000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294669.412000] CPU: L2 Cache: 512K (64 bytes/line)
[4294669.412000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000020 00000000 00000000 00000000
[4294669.412000] mtrr: v2.0 (20020519)
[4294669.412000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294669.412000] Enabling fast FPU save and restore... done.
[4294669.412000] Enabling unmasked SIMD FPU exception support... done.
[4294669.412000] Checking 'hlt' instruction... OK.
[4294669.416000] checking if image is initramfs... it is
[4294670.083000] Freeing initrd memory: 6836k freed
[4294670.100000] ACPI: Looking for DSDT ... not found!
[4294670.102000] ACPI: setting ELCR to 0200 (from 0c00)
[4294670.215000] NET: Registered protocol family 16
[4294670.215000] EISA bus registered
[4294670.215000] ACPI: bus type pci registered
[4294670.216000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294670.216000] PCI: Using configuration type 1
[4294670.216000] ACPI: Subsystem revision 20051216
[4294670.221000] ACPI: Interpreter enabled
[4294670.221000] ACPI: Using PIC for interrupt routing
[4294670.221000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.221000] PCI: Probing PCI hardware (bus 00)
[4294670.223000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294670.223000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294670.223000] Boot video device is 0000:01:00.0
[4294670.223000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.227000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294670.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294670.229000] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *11 14 15)
[4294670.230000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 5 9 14 15) *0, disabled.
[4294670.230000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12)
[4294670.230000] ACPI: PCI Interrupt Link [LNKD] (IRQs 6 7) *0, disabled.
[4294670.230000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.230000] pnp: PnP ACPI init
[4294670.232000] pnp: PnP ACPI: found 8 devices
[4294670.232000] PnPBIOS: Disabled by ACPI PNP
[4294670.232000] PCI: Using ACPI for IRQ routing
[4294670.232000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.235000] PCI: Bridge: 0000:00:01.0
[4294670.235000]   IO window: disabled.
[4294670.235000]   MEM window: dde00000-dfefffff
[4294670.235000]   PREFETCH window: d5d00000-ddcfffff
[4294670.235000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294670.235000]   IO window: 00001000-000010ff
[4294670.235000]   IO window: 00001400-000014ff
[4294670.235000]   PREFETCH window: 20000000-21ffffff
[4294670.235000]   MEM window: 22000000-23ffffff
[4294670.235000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294670.235000] **** SET: Misaligned resource pointer: ddf3a6e2 Type 07 Len 0
[4294670.235000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294670.235000] PCI: setting IRQ 10 as level-triggered
[4294670.235000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294670.236000] audit: initializing netlink socket (disabled)
[4294670.236000] audit(1154475556.235:1): initialized
[4294670.236000] VFS: Disk quotas dquot_6.5.1
[4294670.236000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.236000] Initializing Cryptographic API
[4294670.236000] io scheduler noop registered
[4294670.236000] io scheduler anticipatory registered
[4294670.236000] io scheduler deadline registered
[4294670.236000] io scheduler cfq registered
[4294670.236000] isapnp: Scanning for PnP cards...
[4294670.593000] isapnp: No Plug & Play device found
[4294670.604000] spurious 8259A interrupt: IRQ7.
[4294670.608000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.610000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294670.611000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294670.611000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294670.612000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294670.612000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294670.612000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.612000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.614000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.614000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.614000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.614000] mice: PS/2 mouse device common for all mice
[4294670.615000] EISA: Probing bus 0 at eisa.0
[4294670.615000] Cannot allocate resource for EISA slot 1
[4294670.615000] EISA: Detected 0 cards.
[4294670.615000] NET: Registered protocol family 2
[4294670.625000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294670.625000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.625000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.625000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.625000] TCP reno registered
[4294670.625000] TCP bic registered
[4294670.625000] NET: Registered protocol family 1
[4294670.625000] NET: Registered protocol family 8
[4294670.625000] NET: Registered protocol family 20
[4294670.625000] Using IPI Shortcut mode
[4294670.625000] ACPI wakeup devices:
[4294670.625000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294670.625000] ACPI: (supports S0 S3 S4 S5)
[4294670.625000] Freeing unused kernel memory: 288k freed
[4294670.682000] vga16fb: initializing
[4294670.682000] vga16fb: mapped to 0xc00a0000
[4294670.773000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.822000] Console: switching to colour frame buffer device 80x25
[4294670.822000] fb0: VGA16 VGA frame buffer device
[4294671.909000] Capability LSM initialized
[4294671.946000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294672.070000] ACPI: Thermal Zone [THRM] (0 C)
[4294672.487000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294672.487000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294672.487000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[4294672.487000] VP_IDE: chipset revision 6
[4294672.487000] VP_IDE: not 100% native mode: will probe irqs later
[4294672.487000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294672.487000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294672.487000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294672.487000] Probing IDE interface ide0...
[4294672.873000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294673.179000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.463000] Probing IDE interface ide1...
[4294674.257000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294674.869000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.876000] hda: max request size: 1024KiB
[4294674.885000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.885000] hda: cache flushes supported
[4294674.885000]  hda: hda1 hda2 < hda5 >
[4294674.952000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294674.952000] Uniform CD-ROM driver Revision: 3.20
[4294675.270000] usbcore: registered new driver usbfs
[4294675.271000] usbcore: registered new driver hub
[4294675.311000] **** SET: Misaligned resource pointer: ddd5f5e2 Type 07 Len 0
[4294675.312000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[4294675.312000] PCI: setting IRQ 7 as level-triggered
[4294675.312000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.312000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 7
[4294675.312000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294675.312000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[4294675.312000] ehci_hcd 0000:00:10.3: irq 7, io mem 0xdfffdf00
[4294675.312000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294675.313000] hub 1-0:1.0: USB hub found
[4294675.313000] hub 1-0:1.0: 6 ports detected
[4294675.313000] USB Universal Host Controller Interface driver v2.3
[4294675.314000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.314000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 7
[4294675.314000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294675.414000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[4294675.414000] uhci_hcd 0000:00:10.0: irq 7, io base 0x0000e400
[4294675.415000] hub 2-0:1.0: USB hub found
[4294675.415000] hub 2-0:1.0: 2 ports detected
[4294675.516000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.516000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 7
[4294675.516000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294675.516000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[4294675.516000] uhci_hcd 0000:00:10.1: irq 7, io base 0x0000e800
[4294675.516000] hub 3-0:1.0: USB hub found
[4294675.516000] hub 3-0:1.0: 2 ports detected
[4294675.617000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.617000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 7
[4294675.617000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294675.617000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[4294675.617000] uhci_hcd 0000:00:10.2: irq 7, io base 0x0000ec00
[4294675.617000] hub 4-0:1.0: USB hub found
[4294675.617000] hub 4-0:1.0: 2 ports detected
[4294675.878000] Attempting manual resume
[4294675.948000] EXT3-fs: mounted filesystem with ordered data mode.
[4294675.962000] kjournald starting.  Commit interval 5 seconds
[4294689.647000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294689.647000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294689.647000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294689.647000] Yenta O2: enabling read prefetch/write burst
[4294689.769000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[4294689.769000] Socket status: 30000007
[4294689.952000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294689.952000] **** SET: Misaligned resource pointer: da1ffc22 Type 07 Len 0
[4294689.952000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294689.952000] PCI: setting IRQ 11 as level-triggered
[4294689.952000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294689.956000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294689.957000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[4294689.969000] Linux agpgart interface v0.101 (c) Dave Jones
[4294689.989000] agpgart: Detected VIA KM400/KM400A chipset
[4294689.993000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294690.018000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294690.018000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294690.691000] irda_init()
[4294690.691000] NET: Registered protocol family 23
[4294690.742000] input: PC Speaker as /class/input/input1
[4294690.749000] Real Time Clock Driver v1.12
[4294690.765000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294690.771000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294690.800000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294690.840000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294691.007000] cs: IO port probe 0x100-0x3af: clean.
[4294691.009000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294691.010000] cs: IO port probe 0x820-0x8ff: clean.
[4294691.010000] cs: IO port probe 0xc00-0xcf7: clean.
[4294691.011000] cs: IO port probe 0xa00-0xaff: clean.
[4294691.080000] ts: Compaq touchscreen protocol output
[4294691.320000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294691.321000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294691.347000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294691.347000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294691.397000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294692.433000] lp: driver loaded but no devices found
[4294692.456000] NET: Registered protocol family 17
[4294692.508000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294692.701000] EXT3 FS on hda1, internal journal
[4294692.911000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294692.911000] md: bitmap version 4.39
[4294693.466000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.121000] cdrom: open failed.
[4294700.283000] ACPI: AC Adapter [AC] (on-line)
[4294700.348000] ACPI: Battery Slot [BAT0] (battery present)
[4294700.426000] ACPI: Power Button (FF) [PWRF]
[4294700.426000] ACPI: Power Button (CM) [PWRB]
[4294700.426000] ACPI: Sleep Button (CM) [SLPB]
[4294700.426000] ACPI: Lid Switch [LIDD]
[4294700.570000] ibm_acpi: ec object not found
[4294700.595000] pcc_acpi: loading...
[4294700.695000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294701.147000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294701.152000] Detected 1658.963 MHz processor.
[4294701.156000] powernow: SGTC: 13333
[4294701.156000] powernow: Minimum speed 398 MHz. Maximum speed 1658 MHz.
[4294705.468000] [drm] Initialized drm 1.0.1 20051102
[4294705.487000] **** SET: Misaligned resource pointer: c15f0522 Type 07 Len 0
[4294705.488000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[4294705.488000] PCI: setting IRQ 9 as level-triggered
[4294705.488000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4294705.489000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 9
[4294705.489000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294705.490000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294705.977000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294705.977000] agpgart: Device is in legacy mode, falling back to 2.x
[4294705.977000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294705.978000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294714.429000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294714.429000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294714.429000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294714.429000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294714.429000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294714.429000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294714.429000]  [<c0121520>] __do_softirq+0x30/0xb0
[4294714.429000]  [<c01215d5>] do_softirq+0x35/0x40
[4294714.429000]  [<c0121685>] irq_exit+0x35/0x40
[4294714.429000]  [<c010597f>] do_IRQ+0x1f/0x30
[4294714.429000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294714.429000]  [<c0144688>] buffered_rmqueue+0x218/0x250
[4294714.429000]  [<c01447f1>] get_page_from_freelist+0x71/0xd0
[4294714.429000]  [<c014489e>] __alloc_pages+0x4e/0x2e0
[4294714.429000]  [<c014ff71>] do_wp_page+0x221/0x350
[4294714.429000]  [<c015095f>] do_anonymous_page+0x7f/0x190
[4294714.429000]  [<c0150f95>] __handle_mm_fault+0x1d5/0x210
[4294714.429000]  [<c0116a36>] do_page_fault+0x216/0x61a
[4294714.429000]  [<c0116820>] do_page_fault+0x0/0x61a
[4294714.429000]  [<c01041df>] error_code+0x4f/0x60
[4294714.429000] handlers:
[4294714.429000] [<de90f6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294714.429000] Disabling IRQ #11
[4294716.463000] ppdev: user-space parallel port driver
[4294716.818000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294716.819000] apm: overridden by ACPI.
[4294717.887000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294720.749000] Bluetooth: Core ver 2.8
[4294720.749000] NET: Registered protocol family 31
[4294720.749000] Bluetooth: HCI device and connection manager initialized
[4294720.749000] Bluetooth: HCI socket layer initialized
[4294721.056000] Bluetooth: L2CAP ver 2.8
[4294721.056000] Bluetooth: L2CAP socket layer initialized
[4294721.082000] Bluetooth: RFCOMM socket layer initialized
[4294721.082000] Bluetooth: RFCOMM TTY layer initialized
[4294721.082000] Bluetooth: RFCOMM ver 1.7
[4294740.573000] NET: Registered protocol family 10
[4294740.573000] lo: Disabled Privacy Extensions
[4294740.573000] IPv6 over IPv4 tunneling driver
[4294751.220000] eth0: no IPv6 routers present
[4294754.429000] NETDEV WATCHDOG: eth0: transmit timed out
[4294754.429000] eth0: Transmit timed out, status 1003, PHY status 786d, resetting...
[4294754.429000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294755.654000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294755.654000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294755.654000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294755.654000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294755.654000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294755.654000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294755.654000]  [<c0121520>] __do_softirq+0x30/0xb0
[4294755.654000]  [<c01215d5>] do_softirq+0x35/0x40
[4294755.654000]  [<c0121685>] irq_exit+0x35/0x40
[4294755.654000]  [<c010597f>] do_IRQ+0x1f/0x30
[4294755.654000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294755.654000]  [<c013e900>] enable_irq+0x50/0xd0
[4294755.654000]  [<de90f44c>] rhine_tx_timeout_task+0x9c/0x100 [via_rhine]
[4294755.654000]  [<c012caca>] worker_thread+0x1ba/0x290
[4294755.654000]  [<de90f3b0>] rhine_tx_timeout_task+0x0/0x100 [via_rhine]
[4294755.654000]  [<c0118940>] default_wake_function+0x0/0x20
[4294755.654000]  [<c012c910>] worker_thread+0x0/0x290
[4294755.654000]  [<c0130d53>] kthread+0x93/0xa0
[4294755.654000]  [<c0130cc0>] kthread+0x0/0xa0
[4294755.654000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4294755.654000] handlers:
[4294755.654000] [<de90f6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294755.654000] Disabling IRQ #11
[4294886.667000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294886.667000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294886.667000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294886.667000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294886.667000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294886.667000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294886.667000]  [<c0121520>] __do_softirq+0x30/0xb0
[4294886.667000]  [<c01215d5>] do_softirq+0x35/0x40
[4294886.667000]  [<c0121685>] irq_exit+0x35/0x40
[4294886.667000]  [<c010597f>] do_IRQ+0x1f/0x30
[4294886.667000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294886.667000]  [<c013ea7c>] setup_irq+0x9c/0x120
[4294886.667000]  [<de90f6f0>] rhine_interrupt+0x0/0x240 [via_rhine]
[4294886.667000]  [<c013ec5b>] request_irq+0x7b/0xa0
[4294886.667000]  [<de90f2e2>] rhine_open+0x32/0xf0 [via_rhine]
[4294886.667000]  [<de90f6f0>] rhine_interrupt+0x0/0x240 [via_rhine]
[4294886.667000]  [<c027eebe>] dev_open+0x2e/0x80
[4294886.667000]  [<c0280740>] dev_change_flags+0xe0/0x130
[4294886.667000]  [<c02c714e>] devinet_ioctl+0x57e/0x5f0
[4294886.667000]  [<c0172ed2>] do_ioctl+0x22/0x80
[4294886.667000]  [<c01730b1>] vfs_ioctl+0x51/0x1f0
[4294886.667000]  [<c01732ad>] sys_ioctl+0x5d/0x90
[4294886.667000]  [<c010302b>] sysenter_past_esp+0x54/0x79
[4294886.667000] handlers:
[4294886.667000] [<de90f6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294886.667000] Disabling IRQ #11
[4294886.697000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294897.458000] eth0: no IPv6 routers present
[4294914.697000] NETDEV WATCHDOG: eth0: transmit timed out
[4294914.697000] eth0: Transmit timed out, status 1003, PHY status 786d, resetting...
[4294914.697000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294916.135000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294916.135000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294916.135000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294916.135000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294916.135000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294916.135000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294916.135000]  [<c0121520>] __do_softirq+0x30/0xb0
[4294916.135000]  [<c01215d5>] do_softirq+0x35/0x40
[4294916.135000]  [<c0121685>] irq_exit+0x35/0x40
[4294916.135000]  [<c010597f>] do_IRQ+0x1f/0x30
[4294916.135000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294916.135000]  [<c013e900>] enable_irq+0x50/0xd0
[4294916.135000]  [<de90f44c>] rhine_tx_timeout_task+0x9c/0x100 [via_rhine]
[4294916.135000]  [<c012caca>] worker_thread+0x1ba/0x290
[4294916.135000]  [<de90f3b0>] rhine_tx_timeout_task+0x0/0x100 [via_rhine]
[4294916.135000]  [<c0118940>] default_wake_function+0x0/0x20

---

### Post by spazsui on 2006-08-01
[429491jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash acpi=noirq
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (013c2000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1659.902 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294671.102000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294671.103000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.121000] Memory: 476468k/491456k available (1976k kernel code, 14388k reserved, 606k data, 288k init, 0k highmem)
[4294671.121000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294671.181000] Calibrating delay using timer specific routine.. 3320.00 BogoMIPS (lpj=1660003)
[4294671.181000] Security Framework v1.0.0 initialized
[4294671.181000] SELinux:  Disabled at boot.
[4294671.181000] Mount-cache hash table entries: 512
[4294671.181000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294671.181000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294671.181000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294671.181000] CPU: L2 Cache: 512K (64 bytes/line)
[4294671.181000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000020 00000000 00000000 00000000
[4294671.181000] mtrr: v2.0 (20020519)
[4294671.181000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294671.181000] Enabling fast FPU save and restore... done.
[4294671.181000] Enabling unmasked SIMD FPU exception support... done.
[4294671.181000] Checking 'hlt' instruction... OK.
[4294671.185000] checking if image is initramfs... it is
[4294671.851000] Freeing initrd memory: 6836k freed
[4294671.868000] ACPI: Looking for DSDT ... not found!
[4294671.871000] ACPI: setting ELCR to 0e00 (from 0c00)
[4294671.883000] NET: Registered protocol family 16
[4294671.883000] EISA bus registered
[4294671.883000] ACPI: bus type pci registered
[4294671.884000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294671.884000] PCI: Using configuration type 1
[4294671.884000] ACPI: Subsystem revision 20051216
[4294671.889000] ACPI: Interpreter enabled
[4294671.889000] ACPI: Using PIC for interrupt routing
[4294671.889000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.889000] PCI: Probing PCI hardware (bus 00)
[4294671.891000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294671.891000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294671.891000] Boot video device is 0000:01:00.0
[4294671.891000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.895000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294671.896000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294671.898000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.898000] pnp: PnP ACPI init
[4294671.899000] pnp: PnP ACPI: found 8 devices
[4294671.899000] PnPBIOS: Disabled by ACPI PNP
[4294671.899000] PCI: Probing PCI hardware
[4294671.899000] PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
[4294671.899000] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.899000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294671.899000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294671.899000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294671.899000] PCI: IRQ 0 for device 0000:00:10.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.899000] PCI: IRQ 0 for device 0000:00:10.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.899000] PCI: IRQ 0 for device 0000:00:10.2 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.899000] PCI: IRQ 0 for device 0000:00:10.3 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.899000] PCI: IRQ 0 for device 0000:00:11.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.899000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294671.903000] PCI: Bridge: 0000:00:01.0
[4294671.903000]   IO window: disabled.
[4294671.903000]   MEM window: dde00000-dfefffff
[4294671.903000]   PREFETCH window: d5d00000-ddcfffff
[4294671.903000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294671.903000]   IO window: 00001000-000010ff
[4294671.903000]   IO window: 00001400-000014ff
[4294671.903000]   PREFETCH window: 20000000-21ffffff
[4294671.903000]   MEM window: 22000000-23ffffff
[4294671.903000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.903000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294671.903000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294671.903000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294671.903000] audit: initializing netlink socket (disabled)
[4294671.903000] audit(1154476631.902:1): initialized
[4294671.903000] VFS: Disk quotas dquot_6.5.1
[4294671.904000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.904000] Initializing Cryptographic API
[4294671.904000] io scheduler noop registered
[4294671.904000] io scheduler anticipatory registered
[4294671.904000] io scheduler deadline registered
[4294671.904000] io scheduler cfq registered
[4294671.904000] isapnp: Scanning for PnP cards...
[4294672.261000] isapnp: No Plug & Play device found
[4294672.275000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294672.277000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294672.278000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294672.278000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294672.278000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294672.278000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294672.279000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.279000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294672.281000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.281000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.281000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.281000] mice: PS/2 mouse device common for all mice
[4294672.282000] EISA: Probing bus 0 at eisa.0
[4294672.282000] Cannot allocate resource for EISA slot 1
[4294672.282000] EISA: Detected 0 cards.
[4294672.282000] NET: Registered protocol family 2
[4294672.292000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294672.292000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.292000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.292000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.292000] TCP reno registered
[4294672.292000] TCP bic registered
[4294672.292000] NET: Registered protocol family 1
[4294672.292000] NET: Registered protocol family 8
[4294672.292000] NET: Registered protocol family 20
[4294672.292000] Using IPI Shortcut mode
[4294672.292000] ACPI wakeup devices:
[4294672.292000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294672.292000] ACPI: (supports S0 S3 S4 S5)
[4294672.292000] Freeing unused kernel memory: 288k freed
[4294672.348000] vga16fb: initializing
[4294672.349000] vga16fb: mapped to 0xc00a0000
[4294672.440000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.489000] Console: switching to colour frame buffer device 80x25
[4294672.489000] fb0: VGA16 VGA frame buffer device
[4294673.576000] Capability LSM initialized
[4294673.611000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294673.736000] ACPI: Thermal Zone [THRM] (0 C)
[4294674.177000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294674.177000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294674.177000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 14
[4294674.177000] VP_IDE: chipset revision 6
[4294674.177000] VP_IDE: not 100% native mode: will probe irqs later
[4294674.177000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294674.177000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294674.177000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294674.177000] Probing IDE interface ide0...
[4294674.563000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294674.869000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.892000] Probing IDE interface ide1...
[4294675.686000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294676.298000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.305000] hda: max request size: 1024KiB
[4294676.314000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294676.314000] hda: cache flushes supported
[4294676.314000]  hda: hda1 hda2 < hda5 >
[4294676.380000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294676.380000] Uniform CD-ROM driver Revision: 3.20
[4294676.696000] usbcore: registered new driver usbfs
[4294676.697000] usbcore: registered new driver hub
[4294676.698000] USB Universal Host Controller Interface driver v2.3
[4294676.699000] PCI: IRQ 0 for device 0000:00:10.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294676.699000] PCI: setting IRQ 6 as level-triggered
[4294676.699000] PCI: Assigned IRQ 6 for device 0000:00:10.0
[4294676.699000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.699000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.699000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.699000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 6
[4294676.699000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294676.699000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294676.699000] uhci_hcd 0000:00:10.0: irq 6, io base 0x0000e400
[4294676.732000] hub 1-0:1.0: USB hub found
[4294676.732000] hub 1-0:1.0: 2 ports detected
[4294676.833000] PCI: Found IRQ 6 for device 0000:00:10.1
[4294676.833000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.833000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.833000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.833000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 6
[4294676.833000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294676.833000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294676.833000] uhci_hcd 0000:00:10.1: irq 6, io base 0x0000e800
[4294676.833000] hub 2-0:1.0: USB hub found
[4294676.833000] hub 2-0:1.0: 2 ports detected
[4294676.934000] PCI: Found IRQ 6 for device 0000:00:10.2
[4294676.934000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.934000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.934000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.934000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 6
[4294676.934000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294676.934000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294676.934000] uhci_hcd 0000:00:10.2: irq 6, io base 0x0000ec00
[4294676.934000] hub 3-0:1.0: USB hub found
[4294676.934000] hub 3-0:1.0: 2 ports detected
[4294677.037000] PCI: Found IRQ 6 for device 0000:00:10.3
[4294677.037000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294677.037000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294677.037000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294677.037000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 6
[4294677.037000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294677.037000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294677.037000] ehci_hcd 0000:00:10.3: irq 6, io mem 0xdfffdf00
[4294677.037000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294677.037000] hub 4-0:1.0: USB hub found
[4294677.037000] hub 4-0:1.0: 6 ports detected
[4294677.039000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294677.278000] Attempting manual resume
[4294677.348000] EXT3-fs: mounted filesystem with ordered data mode.
[4294677.362000] kjournald starting.  Commit interval 5 seconds
[4294677.827000] usb 4-1: new high speed USB device using ehci_hcd and address 2[4294691.083000] Linux agpgart interface v0.101 (c) Dave Jones
[4294691.089000] agpgart: Detected VIA KM400/KM400A chipset
[4294691.258000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294691.268000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.274000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.576000] PCI: Found IRQ 11 for device 0000:00:09.0
[4294691.577000] PCI: Sharing IRQ 11 with 0000:00:12.0
[4294691.577000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294691.791000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294691.791000] PCI: Found IRQ 11 for device 0000:00:12.0
[4294691.791000] PCI: Sharing IRQ 11 with 0000:00:09.0
[4294691.795000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294691.796000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[4294691.828000] PCI: Found IRQ 10 for device 0000:00:11.6
[4294691.828000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294691.828000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294691.830000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294691.978000] PCI: Found IRQ 10 for device 0000:00:11.5
[4294691.978000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294691.978000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294691.978000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294692.013000] input: PC Speaker as /class/input/input1
[4294692.060000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294692.060000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294692.060000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294692.060000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294692.060000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294692.060000] Yenta O2: enabling read prefetch/write burst
[4294692.076000] Real Time Clock Driver v1.12
[4294692.134000] irda_init()
[4294692.134000] NET: Registered protocol family 23
[4294692.182000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[4294692.182000] Socket status: 30000007
[4294692.682000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294692.692000] SCSI subsystem initialized
[4294692.708000] Initializing USB Mass Storage driver...
[4294692.709000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294692.709000] usb-storage: device found at 2
[4294692.709000] usb-storage: waiting for device to settle before scanning
[4294692.709000] usbcore: registered new driver usb-storage
[4294692.709000] USB Mass Storage support registered.
[4294692.722000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294692.760000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294693.279000] ts: Compaq touchscreen protocol output
[4294693.471000] cs: IO port probe 0x100-0x3af: clean.
[4294693.473000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294693.474000] cs: IO port probe 0x820-0x8ff: clean.
[4294693.474000] cs: IO port probe 0xc00-0xcf7: clean.
[4294693.475000] cs: IO port probe 0xa00-0xaff: clean.
[4294693.803000] lp: driver loaded but no devices found
[4294693.826000] NET: Registered protocol family 17
[4294693.878000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294694.014000] EXT3 FS on hda1, internal journal
[4294694.224000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.224000] md: bitmap version 4.39
[4294694.808000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294695.448000] cdrom: open failed.
[4294697.709000]   Vendor: CREATIVE  Model: MuVo TX FM        Rev: 1182
[4294697.709000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294697.711000] usb-storage: device scan complete
[4294697.784000] Driver 'sd' needs updating - please use bus_type methods
[4294697.785000] SCSI device sda: 496896 512-byte hdwr sectors (254 MB)
[4294697.786000] sda: Write Protect is off
[4294697.786000] sda: Mode Sense: 38 00 00 00
[4294697.786000] sda: assuming drive cache: write through
[4294697.791000] SCSI device sda: 496896 512-byte hdwr sectors (254 MB)
[4294697.792000] sda: Write Protect is off
[4294697.792000] sda: Mode Sense: 38 00 00 00
[4294697.792000] sda: assuming drive cache: write through
[4294697.792000]  sda: sda1
[4294697.794000] sd 0:0:0:0: Attached scsi removable disk sda
[4294697.805000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294701.596000] ACPI: AC Adapter [AC] (on-line)
[4294701.662000] ACPI: Battery Slot [BAT0] (battery present)
[4294701.731000] ACPI: Power Button (FF) [PWRF]
[4294701.731000] ACPI: Power Button (CM) [PWRB]
[4294701.731000] ACPI: Sleep Button (CM) [SLPB]
[4294701.731000] ACPI: Lid Switch [LIDD]
[4294701.854000] ibm_acpi: ec object not found
[4294701.879000] pcc_acpi: loading...
[4294701.981000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294702.403000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294702.408000] Detected 1659.442 MHz processor.
[4294702.412000] powernow: SGTC: 13333
[4294702.412000] powernow: Minimum speed 398 MHz. Maximum speed 1659 MHz.
[4294706.695000] [drm] Initialized drm 1.0.1 20051102
[4294706.714000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294706.715000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294707.245000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294707.245000] agpgart: Device is in legacy mode, falling back to 2.x
[4294707.246000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294707.246000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294708.879000] ppdev: user-space parallel port driver
[4294709.248000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294709.249000] apm: overridden by ACPI.
[4294710.268000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294713.008000] Bluetooth: Core ver 2.8
[4294713.008000] NET: Registered protocol family 31
[4294713.008000] Bluetooth: HCI device and connection manager initialized
[4294713.008000] Bluetooth: HCI socket layer initialized
[4294713.110000] Bluetooth: L2CAP ver 2.8
[4294713.110000] Bluetooth: L2CAP socket layer initialized
[4294713.142000] Bluetooth: RFCOMM socket layer initialized
[4294713.142000] Bluetooth: RFCOMM TTY layer initialized
[4294713.142000] Bluetooth: RFCOMM ver 1.7
[4294728.428000] NET: Registered protocol family 10
[4294728.428000] lo: Disabled Privacy Extensions
[4294728.429000] IPv6 over IPv4 tunneling driver
[4294733.976000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294738.838000] eth0: no IPv6 routers present
[4294856.262000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294866.708000] eth0: no IPv6 routers present6.135000]  [<c012c910>] worker_thread+0x0/0x290
[4294916.135000]  [<c0130d53>] kthread+0x93/0xa0
[4294916.135000]  [<c0130cc0>] kthread+0x0/0xa0
[4294916.135000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4294916.135000] handlers:
[4294916.135000] [<de90f6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294916.135000] Disabling IRQ #11

---

### Post by spazsui on 2006-08-01
And finally the last one trying both together:

jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash lapc ircpoll
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (013c2000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1658.612 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.780000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294669.781000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.799000] Memory: 476468k/491456k available (1976k kernel code, 14388k reserved, 606k data, 288k init, 0k highmem)
[4294669.799000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.859000] Calibrating delay using timer specific routine.. 3320.02 BogoMIPS (lpj=1660011)
[4294669.859000] Security Framework v1.0.0 initialized
[4294669.859000] SELinux:  Disabled at boot.
[4294669.859000] Mount-cache hash table entries: 512
[4294669.859000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294669.859000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294669.859000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294669.859000] CPU: L2 Cache: 512K (64 bytes/line)
[4294669.859000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000020 00000000 00000000 00000000
[4294669.859000] mtrr: v2.0 (20020519)
[4294669.859000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294669.859000] Enabling fast FPU save and restore... done.
[4294669.859000] Enabling unmasked SIMD FPU exception support... done.
[4294669.859000] Checking 'hlt' instruction... OK.
[4294669.863000] checking if image is initramfs... it is
[4294670.529000] Freeing initrd memory: 6836k freed
[4294670.547000] ACPI: Looking for DSDT ... not found!
[4294670.549000] ACPI: setting ELCR to 0200 (from 0c00)
[4294670.561000] NET: Registered protocol family 16
[4294670.561000] EISA bus registered
[4294670.561000] ACPI: bus type pci registered
[4294670.562000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294670.562000] PCI: Using configuration type 1
[4294670.562000] ACPI: Subsystem revision 20051216
[4294670.567000] ACPI: Interpreter enabled
[4294670.567000] ACPI: Using PIC for interrupt routing
[4294670.567000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.567000] PCI: Probing PCI hardware (bus 00)
[4294670.569000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294670.569000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294670.569000] Boot video device is 0000:01:00.0
[4294670.569000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.574000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294670.574000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294670.576000] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *11 14 15)
[4294670.576000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 5 9 14 15) *0, disabled.
[4294670.576000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12)
[4294670.576000] ACPI: PCI Interrupt Link [LNKD] (IRQs 6 7) *0, disabled.
[4294670.577000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.577000] pnp: PnP ACPI init
[4294670.578000] pnp: PnP ACPI: found 8 devices
[4294670.578000] PnPBIOS: Disabled by ACPI PNP
[4294670.578000] PCI: Using ACPI for IRQ routing
[4294670.578000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.581000] PCI: Bridge: 0000:00:01.0
[4294670.581000]   IO window: disabled.
[4294670.581000]   MEM window: dde00000-dfefffff
[4294670.581000]   PREFETCH window: d5d00000-ddcfffff
[4294670.581000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294670.581000]   IO window: 00001000-000010ff
[4294670.581000]   IO window: 00001400-000014ff
[4294670.581000]   PREFETCH window: 20000000-21ffffff
[4294670.581000]   MEM window: 22000000-23ffffff
[4294670.581000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294670.581000] **** SET: Misaligned resource pointer: dd9ee6e2 Type 07 Len 0
[4294670.582000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294670.582000] PCI: setting IRQ 10 as level-triggered
[4294670.582000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294670.582000] audit: initializing netlink socket (disabled)
[4294670.582000] audit(1154477472.581:1): initialized
[4294670.582000] VFS: Disk quotas dquot_6.5.1
[4294670.582000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.582000] Initializing Cryptographic API
[4294670.582000] io scheduler noop registered
[4294670.582000] io scheduler anticipatory registered
[4294670.582000] io scheduler deadline registered
[4294670.582000] io scheduler cfq registered
[4294670.583000] isapnp: Scanning for PnP cards...
[4294670.940000] isapnp: No Plug & Play device found
[4294670.954000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.956000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294670.957000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294670.957000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294670.957000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294670.957000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294670.958000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.958000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.960000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.960000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.960000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.960000] mice: PS/2 mouse device common for all mice
[4294670.961000] EISA: Probing bus 0 at eisa.0
[4294670.961000] Cannot allocate resource for EISA slot 1
[4294670.961000] EISA: Detected 0 cards.
[4294670.961000] NET: Registered protocol family 2
[4294670.971000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294670.971000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.971000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.971000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.971000] TCP reno registered
[4294670.971000] TCP bic registered
[4294670.971000] NET: Registered protocol family 1
[4294670.971000] NET: Registered protocol family 8
[4294670.971000] NET: Registered protocol family 20
[4294670.971000] Using IPI Shortcut mode
[4294670.971000] ACPI wakeup devices:
[4294670.971000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294670.971000] ACPI: (supports S0 S3 S4 S5)
[4294670.971000] Freeing unused kernel memory: 288k freed
[4294671.027000] vga16fb: initializing
[4294671.027000] vga16fb: mapped to 0xc00a0000
[4294671.119000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.167000] Console: switching to colour frame buffer device 80x25
[4294671.167000] fb0: VGA16 VGA frame buffer device
[4294672.253000] Capability LSM initialized
[4294672.290000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294672.414000] ACPI: Thermal Zone [THRM] (0 C)
[4294672.843000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294672.843000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294672.843000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[4294672.843000] VP_IDE: chipset revision 6
[4294672.843000] VP_IDE: not 100% native mode: will probe irqs later
[4294672.843000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294672.843000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294672.843000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294672.843000] Probing IDE interface ide0...
[4294673.229000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294673.535000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.559000] Probing IDE interface ide1...
[4294674.353000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294674.965000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.972000] hda: max request size: 1024KiB
[4294674.981000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.981000] hda: cache flushes supported
[4294674.981000]  hda: hda1 hda2 < hda5 >
[4294675.047000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294675.047000] Uniform CD-ROM driver Revision: 3.20
[4294675.360000] usbcore: registered new driver usbfs
[4294675.360000] usbcore: registered new driver hub
[4294675.362000] USB Universal Host Controller Interface driver v2.3
[4294675.362000] **** SET: Misaligned resource pointer: ddc245e2 Type 07 Len 0
[4294675.363000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[4294675.363000] PCI: setting IRQ 7 as level-triggered
[4294675.363000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.363000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 7
[4294675.363000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294675.363000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294675.363000] uhci_hcd 0000:00:10.0: irq 7, io base 0x0000e400
[4294675.364000] hub 1-0:1.0: USB hub found
[4294675.364000] hub 1-0:1.0: 2 ports detected
[4294675.465000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.465000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 7
[4294675.465000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294675.465000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294675.465000] uhci_hcd 0000:00:10.1: irq 7, io base 0x0000e800
[4294675.465000] hub 2-0:1.0: USB hub found
[4294675.465000] hub 2-0:1.0: 2 ports detected
[4294675.566000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.566000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 7
[4294675.566000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294675.566000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294675.566000] uhci_hcd 0000:00:10.2: irq 7, io base 0x0000ec00
[4294675.566000] hub 3-0:1.0: USB hub found
[4294675.566000] hub 3-0:1.0: 2 ports detected
[4294675.669000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.669000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 7
[4294675.669000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294675.669000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294675.669000] ehci_hcd 0000:00:10.3: irq 7, io mem 0xdfffdf00
[4294675.669000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294675.669000] hub 4-0:1.0: USB hub found
[4294675.669000] hub 4-0:1.0: 6 ports detected
[4294675.903000] Attempting manual resume
[4294675.973000] EXT3-fs: mounted filesystem with ordered data mode.
[4294675.987000] kjournald starting.  Commit interval 5 seconds
[4294690.119000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294690.119000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294690.119000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294690.119000] Yenta O2: enabling read prefetch/write burst
[4294690.134000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294690.173000] irda_init()
[4294690.173000] NET: Registered protocol family 23
[4294690.241000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[4294690.241000] Socket status: 30000007
[4294690.242000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294690.247000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.268000] **** SET: Misaligned resource pointer: ddec8822 Type 07 Len 0
[4294690.269000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294690.269000] PCI: setting IRQ 11 as level-triggered
[4294690.269000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294690.269000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294690.390000] agpgart: Detected VIA KM400/KM400A chipset
[4294690.395000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294690.500000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294690.500000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294690.504000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294690.505000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[4294690.561000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294690.562000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294690.629000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294690.630000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294690.871000] Real Time Clock Driver v1.12
[4294690.945000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294690.985000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[4294691.126000] ts: Compaq touchscreen protocol output
[4294691.285000] cs: IO port probe 0x100-0x3af: clean.
[4294691.287000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294691.288000] cs: IO port probe 0x820-0x8ff: clean.
[4294691.289000] cs: IO port probe 0xc00-0xcf7: clean.
[4294691.289000] cs: IO port probe 0xa00-0xaff: clean.
[4294691.327000] input: PC Speaker as /class/input/input2
[4294691.889000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294692.947000] NET: Registered protocol family 17
[4294693.109000] lp: driver loaded but no devices found
[4294693.172000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294693.306000] EXT3 FS on hda1, internal journal
[4294693.501000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294693.501000] md: bitmap version 4.39
[4294694.085000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.740000] cdrom: open failed.
[4294700.932000] ACPI: AC Adapter [AC] (on-line)
[4294701.004000] ACPI: Battery Slot [BAT0] (battery present)
[4294701.076000] ACPI: Power Button (FF) [PWRF]
[4294701.076000] ACPI: Power Button (CM) [PWRB]
[4294701.076000] ACPI: Sleep Button (CM) [SLPB]
[4294701.076000] ACPI: Lid Switch [LIDD]
[4294701.202000] ibm_acpi: ec object not found
[4294701.228000] pcc_acpi: loading...
[4294701.332000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294701.765000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294701.770000] Detected 1659.682 MHz processor.
[4294701.774000] powernow: SGTC: 13333
[4294701.774000] powernow: Minimum speed 398 MHz. Maximum speed 1659 MHz.
[4294706.015000] [drm] Initialized drm 1.0.1 20051102
[4294706.033000] **** SET: Misaligned resource pointer: dd5c2822 Type 07 Len 0
[4294706.034000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[4294706.034000] PCI: setting IRQ 9 as level-triggered
[4294706.034000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4294706.035000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 9
[4294706.036000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294706.036000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294706.551000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294706.551000] agpgart: Device is in legacy mode, falling back to 2.x
[4294706.551000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294706.552000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294708.916000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294708.916000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294708.916000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294708.916000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294708.916000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294708.916000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294708.916000]  [<c0121520>] __do_softirq+0x30/0xb0
[4294708.916000]  [<c01215d5>] do_softirq+0x35/0x40
[4294708.916000]  [<c0121685>] irq_exit+0x35/0x40
[4294708.916000]  [<c010597f>] do_IRQ+0x1f/0x30
[4294708.916000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294708.916000] handlers:
[4294708.916000] [<de9976f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294708.916000] Disabling IRQ #11
[4294710.841000] ppdev: user-space parallel port driver
[4294711.182000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294711.183000] apm: overridden by ACPI.
[4294712.185000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294715.055000] Bluetooth: Core ver 2.8
[4294715.055000] NET: Registered protocol family 31
[4294715.055000] Bluetooth: HCI device and connection manager initialized
[4294715.055000] Bluetooth: HCI socket layer initialized
[4294715.139000] Bluetooth: L2CAP ver 2.8
[4294715.139000] Bluetooth: L2CAP socket layer initialized
[4294715.161000] Bluetooth: RFCOMM socket layer initialized
[4294715.161000] Bluetooth: RFCOMM TTY layer initialized
[4294715.161000] Bluetooth: RFCOMM ver 1.7
[4294730.560000] NET: Registered protocol family 10
[4294730.560000] lo: Disabled Privacy Extensions
[4294730.561000] IPv6 over IPv4 tunneling driver
[4294740.566000] eth0: no IPv6 routers present
[4294746.917000] NETDEV WATCHDOG: eth0: transmit timed out
[4294746.917000] eth0: Transmit timed out, status 1003, PHY status 786d, resetting...
[4294746.917000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294748.299000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294748.299000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294748.299000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294748.299000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294748.299000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294748.299000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294748.299000]  [<c0121520>] __do_softirq+0x30/0xb0
[4294748.299000]  [<c01215d5>] do_softirq+0x35/0x40
[4294748.299000]  [<c0121685>] irq_exit+0x35/0x40
[4294748.299000]  [<c010597f>] do_IRQ+0x1f/0x30
[4294748.299000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294748.299000]  [<c013e900>] enable_irq+0x50/0xd0
[4294748.299000]  [<de99744c>] rhine_tx_timeout_task+0x9c/0x100 [via_rhine]
[4294748.299000]  [<c012caca>] worker_thread+0x1ba/0x290
[4294748.299000]  [<de9973b0>] rhine_tx_timeout_task+0x0/0x100 [via_rhine]
[4294748.299000]  [<c0118940>] default_wake_function+0x0/0x20
[4294748.299000]  [<c012c910>] worker_thread+0x0/0x290
[4294748.299000]  [<c0130d53>] kthread+0x93/0xa0
[4294748.299000]  [<c0130cc0>] kthread+0x0/0xa0
[4294748.299000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4294748.299000] handlers:
[4294748.299000] [<de9976f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294748.299000] Disabling IRQ #11
[4294796.006000] usb 4-1: new high speed USB device using ehci_hcd and address 2[4294796.512000] SCSI subsystem initialized
[4294796.556000] Initializing USB Mass Storage driver...
[4294796.558000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294796.559000] usb-storage: device found at 2
[4294796.559000] usb-storage: waiting for device to settle before scanning
[4294796.560000] usbcore: registered new driver usb-storage
[4294796.560000] USB Mass Storage support registered.
[4294801.559000]   Vendor: CREATIVE  Model: MuVo TX FM        Rev: 1182
[4294801.559000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294801.568000] usb-storage: device scan complete
[4294801.690000] Driver 'sd' needs updating - please use bus_type methods
[4294801.695000] SCSI device sda: 496896 512-byte hdwr sectors (254 MB)
[4294801.697000] sda: Write Protect is off
[4294801.697000] sda: Mode Sense: 38 00 00 00
[4294801.698000] sda: assuming drive cache: write through
[4294801.706000] SCSI device sda: 496896 512-byte hdwr sectors (254 MB)
[4294801.708000] sda: Write Protect is off
[4294801.708000] sda: Mode Sense: 38 00 00 00
[4294801.709000] sda: assuming drive cache: write through
[4294801.709000]  sda: sda1
[4294801.713000] sd 0:0:0:0: Attached scsi removable disk sda
[4294802.046000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294802.762000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


So what am I doing wrong exactly?  Am I suppose to edit the networking?  I went in and deactivated and then reactivated the eth0.  I am at a loss.

---

### Post by wiresquire on 2006-08-02
OK, that's good. With both the lapic option and the acpi=noirq option  we are definitely making progress !! You can even see where the eth0 was 'up':
```

[4294886.697000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```
But something funky with the IRQ causes it to go down again
```

[4294714.429000] Disabling IRQ #11

```
which seems to be related to a reassignment of IRQs
```

[4294705.489000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 9

```

I think we are very close!

3. Can you please try no 3 (lapic + irqpoll) again?

I think you had 2 typos of lapc and not lapic, and ircpoll instead of irqpoll. I hope you weren't drinking !!:mrgreen: From the above dmesg:
```

[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash lapc ircpoll

```
These need to be : lapic irqpoll
Please post the dmesg for this.

4. If the above doesn't work, please try enabling lapic AND acpi=noirq.
Please post the dmesg.

5. If 4 doesn't work, let's try them all - enable lapic, irqpoll and acpi=noirq and post the dmesg

6. I hope you don't make it this far :???: 


Good Luck
ws

---

### Post by spazsui on 2006-08-02
Okay, I will try when I get home.  I'm at work right now.  When/If I get the connection do you see any problems with it allowing me to use the wireless?  Do you think this will correct that as well?

---

### Post by spazsui on 2006-08-02
Okay, I tried them all and got the same results.  Here are the dmesg in the order again as I tried them.

jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash lapic irqpoll
[4294667.296000] Misrouted IRQ fixup and polling support enabled
[4294667.296000] This may significantly impact system performance
[4294667.296000] Local APIC disabled by BIOS -- reenabling.
[4294667.296000] Found and enabled local APIC!
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1658.842 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.284000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294669.284000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.304000] Memory: 476468k/491456k available (1976k kernel code, 14384k reserved, 606k data, 288k init, 0k highmem)
[4294669.304000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.364000] Calibrating delay using timer specific routine.. 3321.06 BogoMIPS (lpj=1660530)
[4294669.364000] Security Framework v1.0.0 initialized
[4294669.364000] SELinux:  Disabled at boot.
[4294669.364000] Mount-cache hash table entries: 512
[4294669.364000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294669.364000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294669.364000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294669.364000] CPU: L2 Cache: 512K (64 bytes/line)
[4294669.364000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000020 00000000 00000000 00000000
[4294669.364000] mtrr: v2.0 (20020519)
[4294669.364000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294669.364000] Enabling fast FPU save and restore... done.
[4294669.364000] Enabling unmasked SIMD FPU exception support... done.
[4294669.364000] Checking 'hlt' instruction... OK.
[4294669.368000] checking if image is initramfs... it is
[4294670.041000] Freeing initrd memory: 6836k freed
[4294670.061000] ACPI: Looking for DSDT ... not found!
[4294670.063000] ACPI: setting ELCR to 0200 (from 0c00)
[4294670.176000] NET: Registered protocol family 16
[4294670.176000] EISA bus registered
[4294670.176000] ACPI: bus type pci registered
[4294670.177000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294670.177000] PCI: Using configuration type 1
[4294670.177000] ACPI: Subsystem revision 20051216
[4294670.182000] ACPI: Interpreter enabled
[4294670.182000] ACPI: Using PIC for interrupt routing
[4294670.182000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.182000] PCI: Probing PCI hardware (bus 00)
[4294670.184000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294670.184000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294670.184000] Boot video device is 0000:01:00.0
[4294670.184000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.188000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294670.189000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294670.191000] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *11 14 15)
[4294670.191000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 5 9 14 15) *0, disabled.
[4294670.191000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12)
[4294670.191000] ACPI: PCI Interrupt Link [LNKD] (IRQs 6 7) *0, disabled.
[4294670.192000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.192000] pnp: PnP ACPI init
[4294670.193000] pnp: PnP ACPI: found 8 devices
[4294670.193000] PnPBIOS: Disabled by ACPI PNP
[4294670.193000] PCI: Using ACPI for IRQ routing
[4294670.193000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.196000] PCI: Bridge: 0000:00:01.0
[4294670.196000]   IO window: disabled.
[4294670.196000]   MEM window: dde00000-dfefffff
[4294670.196000]   PREFETCH window: d5d00000-ddcfffff
[4294670.196000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294670.196000]   IO window: 00001000-000010ff
[4294670.196000]   IO window: 00001400-000014ff
[4294670.196000]   PREFETCH window: 20000000-21ffffff
[4294670.196000]   MEM window: 22000000-23ffffff
[4294670.196000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294670.196000] **** SET: Misaligned resource pointer: ddf3a6e2 Type 07 Len 0
[4294670.197000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294670.197000] PCI: setting IRQ 10 as level-triggered
[4294670.197000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294670.197000] audit: initializing netlink socket (disabled)
[4294670.197000] audit(1154565109.196:1): initialized
[4294670.197000] VFS: Disk quotas dquot_6.5.1
[4294670.197000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.197000] Initializing Cryptographic API
[4294670.197000] io scheduler noop registered
[4294670.197000] io scheduler anticipatory registered
[4294670.197000] io scheduler deadline registered
[4294670.197000] io scheduler cfq registered
[4294670.198000] isapnp: Scanning for PnP cards...
[4294670.501000] spurious 8259A interrupt: IRQ7.
[4294670.555000] isapnp: No Plug & Play device found
[4294670.569000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.571000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294670.572000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294670.573000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294670.573000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294670.573000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294670.573000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.573000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.575000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.575000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.575000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.576000] mice: PS/2 mouse device common for all mice
[4294670.576000] EISA: Probing bus 0 at eisa.0
[4294670.576000] Cannot allocate resource for EISA slot 1
[4294670.576000] EISA: Detected 0 cards.
[4294670.576000] NET: Registered protocol family 2
[4294670.586000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294670.586000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.586000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.586000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.586000] TCP reno registered
[4294670.586000] TCP bic registered
[4294670.586000] NET: Registered protocol family 1
[4294670.586000] NET: Registered protocol family 8
[4294670.586000] NET: Registered protocol family 20
[4294670.586000] Using IPI Shortcut mode
[4294670.586000] ACPI wakeup devices:
[4294670.586000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294670.586000] ACPI: (supports S0 S3 S4 S5)
[4294670.586000] Freeing unused kernel memory: 288k freed
[4294670.642000] vga16fb: initializing
[4294670.642000] vga16fb: mapped to 0xc00a0000
[4294670.735000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.783000] Console: switching to colour frame buffer device 80x25
[4294670.783000] fb0: VGA16 VGA frame buffer device
[4294671.874000] Capability LSM initialized
[4294671.910000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294672.036000] ACPI: Thermal Zone [THRM] (0 C)
[4294672.473000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294672.473000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294672.473000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[4294672.473000] VP_IDE: chipset revision 6
[4294672.473000] VP_IDE: not 100% native mode: will probe irqs later
[4294672.473000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294672.473000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294672.473000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294672.473000] Probing IDE interface ide0...
[4294672.859000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294673.165000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.477000] Probing IDE interface ide1...
[4294674.271000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294674.883000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.890000] hda: max request size: 1024KiB
[4294674.899000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.899000] hda: cache flushes supported
[4294674.899000]  hda: hda1 hda2 < hda5 >
[4294674.966000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294674.966000] Uniform CD-ROM driver Revision: 3.20
[4294675.279000] usbcore: registered new driver usbfs
[4294675.279000] usbcore: registered new driver hub
[4294675.312000] **** SET: Misaligned resource pointer: ddd195e2 Type 07 Len 0
[4294675.313000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[4294675.313000] PCI: setting IRQ 7 as level-triggered
[4294675.313000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.313000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 7
[4294675.313000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294675.313000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[4294675.313000] ehci_hcd 0000:00:10.3: irq 7, io mem 0xdfffdf00
[4294675.313000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294675.314000] hub 1-0:1.0: USB hub found
[4294675.314000] hub 1-0:1.0: 6 ports detected
[4294675.315000] USB Universal Host Controller Interface driver v2.3
[4294675.315000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.315000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 7
[4294675.315000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294675.415000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[4294675.415000] uhci_hcd 0000:00:10.0: irq 7, io base 0x0000e400
[4294675.416000] hub 2-0:1.0: USB hub found
[4294675.416000] hub 2-0:1.0: 2 ports detected
[4294675.517000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.517000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 7
[4294675.517000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294675.517000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[4294675.517000] uhci_hcd 0000:00:10.1: irq 7, io base 0x0000e800
[4294675.517000] hub 3-0:1.0: USB hub found
[4294675.517000] hub 3-0:1.0: 2 ports detected
[4294675.618000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294675.618000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 7
[4294675.618000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294675.618000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[4294675.618000] uhci_hcd 0000:00:10.2: irq 7, io base 0x0000ec00
[4294675.618000] hub 4-0:1.0: USB hub found
[4294675.618000] hub 4-0:1.0: 2 ports detected
[4294675.878000] Attempting manual resume
[4294675.935000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294675.935000] EXT3-fs: write access will be enabled during recovery.
[4294677.733000] EXT3-fs: recovery complete.
[4294677.733000] kjournald starting.  Commit interval 5 seconds
[4294677.734000] EXT3-fs: mounted filesystem with ordered data mode.
[4294690.168000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.174000] agpgart: Detected VIA KM400/KM400A chipset
[4294690.179000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294690.314000] **** SET: Misaligned resource pointer: d916af22 Type 07 Len 0
[4294690.314000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294690.314000] PCI: setting IRQ 11 as level-triggered
[4294690.314000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294690.314000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294690.592000] irda_init()
[4294690.592000] NET: Registered protocol family 23
[4294690.895000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294690.896000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294690.923000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294690.974000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294690.974000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294690.974000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294690.974000] Yenta O2: enabling read prefetch/write burst
[4294691.096000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[4294691.096000] Socket status: 30000007
[4294691.361000] Real Time Clock Driver v1.12
[4294691.410000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.410000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294691.411000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294691.412000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294691.452000] input: PC Speaker as /class/input/input1
[4294691.919000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294691.923000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294691.924000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[4294691.974000] cs: IO port probe 0x100-0x3af: clean.
[4294691.976000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294691.977000] cs: IO port probe 0x820-0x8ff: clean.
[4294691.978000] cs: IO port probe 0xc00-0xcf7: clean.
[4294691.978000] cs: IO port probe 0xa00-0xaff: clean.
[4294692.042000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294692.082000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294692.118000] ts: Compaq touchscreen protocol output
[4294692.503000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294692.803000] lp: driver loaded but no devices found
[4294692.870000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294693.000000] EXT3 FS on hda1, internal journal
[4294693.167000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294693.167000] md: bitmap version 4.39
[4294693.842000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294693.935000] NET: Registered protocol family 17
[4294694.560000] cdrom: open failed.
[4294700.844000] ACPI: AC Adapter [AC] (on-line)
[4294700.913000] ACPI: Battery Slot [BAT0] (battery present)
[4294700.983000] ACPI: Power Button (FF) [PWRF]
[4294700.983000] ACPI: Power Button (CM) [PWRB]
[4294700.983000] ACPI: Sleep Button (CM) [SLPB]
[4294700.983000] ACPI: Lid Switch [LIDD]
[4294701.111000] ibm_acpi: ec object not found
[4294701.137000] pcc_acpi: loading...
[4294701.242000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294701.660000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294701.665000] Detected 1658.852 MHz processor.
[4294701.669000] powernow: SGTC: 13333
[4294701.669000] powernow: Minimum speed 398 MHz. Maximum speed 1658 MHz.
[4294706.024000] [drm] Initialized drm 1.0.1 20051102
[4294706.042000] **** SET: Misaligned resource pointer: d7c97522 Type 07 Len 0
[4294706.043000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[4294706.043000] PCI: setting IRQ 9 as level-triggered
[4294706.044000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4294706.044000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 9
[4294706.045000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294706.046000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294706.572000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294706.572000] agpgart: Device is in legacy mode, falling back to 2.x
[4294706.572000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294706.572000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294708.179000] ppdev: user-space parallel port driver
[4294708.535000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294708.535000] apm: overridden by ACPI.
[4294709.868000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294721.639000] BUG: soft lockup detected on CPU#0!
[4294721.639000]
[4294721.639000] Pid: 0, comm:              swapper
[4294721.639000] EIP: 0060:[<c01f78b8>] CPU: 0
[4294721.639000] EIP is at acpi_os_release_lock+0x6/0x1d
[4294721.639000]  EFLAGS: 00000282    Not tainted  (2.6.15-23-386)
[4294721.639000] EAX: 00000282 EBX: 00000060 ECX: c0387f1c EDX: 00000002
[4294721.639000] ESI: 00000008 EDI: dd9306fb EBP: 00000000 DS: 007b ES: 007b
[4294721.639000] CR0: 8005003b CR2: b7e237d0 CR3: 19b91000 CR4: 00000690
[4294721.639000]  [<c01fcb9c>] acpi_ev_gpe_detect+0xe4/0xf1
[4294721.639000]  [<c01fb635>] acpi_ev_sci_xrupt_handler+0x11/0x18
[4294721.639000]  [<c01f70fa>] acpi_irq+0xc/0x16
[4294721.639000]  [<c013e705>] handle_IRQ_event+0x35/0x70
[4294721.639000]  [<c01f70ee>] acpi_irq+0x0/0x16
[4294721.639000]  [<c013e7b3>] __do_IRQ+0x73/0xe0
[4294721.639000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294721.639000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294721.639000]  [<de86fa17>] acpi_safe_halt+0x15/0x1b [processor]
[4294721.639000]  [<de86fb4f>] acpi_processor_idle+0x132/0x2bc [processor]
[4294721.639000]  [<c01010dc>] cpu_idle+0x1c/0x60
[4294721.639000]  [<c03887c6>] start_kernel+0x176/0x1d0
[4294733.244000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294733.244000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294733.244000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294733.244000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294733.244000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294733.244000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294733.244000]  [<c01f78b8>] acpi_os_release_lock+0x6/0x1d
[4294733.244000]  [<c01fcb9c>] acpi_ev_gpe_detect+0xe4/0xf1
[4294733.244000]  [<c01fb635>] acpi_ev_sci_xrupt_handler+0x11/0x18
[4294733.244000]  [<c01f70fa>] acpi_irq+0xc/0x16
[4294733.244000]  [<c013e705>] handle_IRQ_event+0x35/0x70
[4294733.244000]  [<c01f70ee>] acpi_irq+0x0/0x16
[4294733.244000]  [<c013e7b3>] __do_IRQ+0x73/0xe0
[4294733.244000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294733.244000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294733.244000]  [<de86fa17>] acpi_safe_halt+0x15/0x1b [processor]
[4294733.244000]  [<de86fb4f>] acpi_processor_idle+0x132/0x2bc [processor]
[4294733.244000]  [<c01010dc>] cpu_idle+0x1c/0x60
[4294733.244000]  [<c03887c6>] start_kernel+0x176/0x1d0
[4294733.244000] handlers:
[4294733.244000] [<deafa6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294733.244000] Disabling IRQ #11
[4294735.516000] Bluetooth: Core ver 2.8
[4294735.516000] NET: Registered protocol family 31
[4294735.516000] Bluetooth: HCI device and connection manager initialized
[4294735.516000] Bluetooth: HCI socket layer initialized
[4294735.586000] Bluetooth: L2CAP ver 2.8
[4294735.586000] Bluetooth: L2CAP socket layer initialized
[4294735.608000] Bluetooth: RFCOMM socket layer initialized
[4294735.608000] Bluetooth: RFCOMM TTY layer initialized
[4294735.608000] Bluetooth: RFCOMM ver 1.7
[4294752.230000] NET: Registered protocol family 10
[4294752.230000] lo: Disabled Privacy Extensions
[4294752.230000] IPv6 over IPv4 tunneling driver
[4294762.250000] eth0: no IPv6 routers present
[4294867.102000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294877.564000] eth0: no IPv6 routers present
[4294928.948000] BUG: soft lockup detected on CPU#0!
[4294928.948000]
[4294928.948000] Pid: 0, comm:              swapper
[4294928.948000] EIP: 0060:[<c013e6e5>] CPU: 0
[4294928.948000] EIP is at handle_IRQ_event+0x15/0x70
[4294928.948000]  EFLAGS: 00000246    Not tainted  (2.6.15-23-386)
[4294928.948000] EAX: 00000009 EBX: ddfc2260 ECX: ddfc2260 EDX: c0387f8c
[4294928.948000] ESI: 00000000 EDI: c0387f8c EBP: ddfc2260 DS: 007b ES: 007b
[4294928.948000] CR0: 8005003b CR2: b7fbf000 CR3: 19b91000 CR4: 00000690
[4294928.948000]  [<c013e7b3>] __do_IRQ+0x73/0xe0
[4294928.948000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294928.948000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294928.948000]  [<de86fa17>] acpi_safe_halt+0x15/0x1b [processor]
[4294928.948000]  [<de86fb4f>] acpi_processor_idle+0x132/0x2bc [processor]
[4294928.948000]  [<c01010dc>] cpu_idle+0x1c/0x60
[4294928.948000]  [<c03887c6>] start_kernel+0x176/0x1d0
[4294988.322000] irq 11: nobody cared (try booting with the "irqpoll" option)
[4294988.322000]  [<c013ee42>] __report_bad_irq+0x22/0x80
[4294988.322000]  [<c013ef38>] note_interrupt+0x68/0xc0
[4294988.322000]  [<c013e7fc>] __do_IRQ+0xbc/0xe0
[4294988.322000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294988.322000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294988.322000]  [<c013e6e5>] handle_IRQ_event+0x15/0x70
[4294988.322000]  [<c013e7b3>] __do_IRQ+0x73/0xe0
[4294988.322000]  [<c010597a>] do_IRQ+0x1a/0x30
[4294988.322000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4294988.322000]  [<de86fa17>] acpi_safe_halt+0x15/0x1b [processor]
[4294988.322000]  [<de86fb4f>] acpi_processor_idle+0x132/0x2bc [processor]
[4294988.322000]  [<c01010dc>] cpu_idle+0x1c/0x60
[4294988.322000]  [<c03887c6>] start_kernel+0x176/0x1d0
[4294988.322000] handlers:
[4294988.322000] [<deafa6f0>] (rhine_interrupt+0x0/0x240 [via_rhine])
[4294988.322000] Disabling IRQ #11
[4294988.332000] eth0: link down
[4294994.017000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

---

### Post by spazsui on 2006-08-02
jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash lapic acpi=noirq
[4294667.296000] Local APIC disabled by BIOS -- reenabling.
[4294667.296000] Found and enabled local APIC!
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1658.683 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.829000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294670.829000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.848000] Memory: 476468k/491456k available (1976k kernel code, 14384k reserved, 606k data, 288k init, 0k highmem)
[4294670.848000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.908000] Calibrating delay using timer specific routine.. 3320.05 BogoMIPS (lpj=1660027)
[4294670.908000] Security Framework v1.0.0 initialized
[4294670.908000] SELinux:  Disabled at boot.
[4294670.908000] Mount-cache hash table entries: 512
[4294670.908000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294670.908000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294670.908000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294670.908000] CPU: L2 Cache: 512K (64 bytes/line)
[4294670.908000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000020 00000000 00000000 00000000
[4294670.908000] mtrr: v2.0 (20020519)
[4294670.908000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294670.908000] Enabling fast FPU save and restore... done.
[4294670.908000] Enabling unmasked SIMD FPU exception support... done.
[4294670.908000] Checking 'hlt' instruction... OK.
[4294670.912000] checking if image is initramfs... it is
[4294671.579000] Freeing initrd memory: 6836k freed
[4294671.596000] ACPI: Looking for DSDT ... not found!
[4294671.598000] ACPI: setting ELCR to 0e00 (from 0c00)
[4294671.711000] NET: Registered protocol family 16
[4294671.711000] EISA bus registered
[4294671.711000] ACPI: bus type pci registered
[4294671.712000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294671.712000] PCI: Using configuration type 1
[4294671.712000] ACPI: Subsystem revision 20051216
[4294671.717000] ACPI: Interpreter enabled
[4294671.717000] ACPI: Using PIC for interrupt routing
[4294671.717000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.717000] PCI: Probing PCI hardware (bus 00)
[4294671.719000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294671.719000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294671.719000] Boot video device is 0000:01:00.0
[4294671.719000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.723000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294671.724000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294671.726000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.726000] pnp: PnP ACPI init
[4294671.727000] pnp: PnP ACPI: found 8 devices
[4294671.727000] PnPBIOS: Disabled by ACPI PNP
[4294671.727000] PCI: Probing PCI hardware
[4294671.727000] PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
[4294671.727000] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.727000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294671.727000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294671.727000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294671.727000] PCI: IRQ 0 for device 0000:00:10.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.727000] PCI: IRQ 0 for device 0000:00:10.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.727000] PCI: IRQ 0 for device 0000:00:10.2 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.727000] PCI: IRQ 0 for device 0000:00:10.3 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.727000] PCI: IRQ 0 for device 0000:00:11.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.727000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294671.731000] PCI: Bridge: 0000:00:01.0
[4294671.731000]   IO window: disabled.
[4294671.731000]   MEM window: dde00000-dfefffff
[4294671.731000]   PREFETCH window: d5d00000-ddcfffff
[4294671.731000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294671.731000]   IO window: 00001000-000010ff
[4294671.731000]   IO window: 00001400-000014ff
[4294671.731000]   PREFETCH window: 20000000-21ffffff
[4294671.731000]   MEM window: 22000000-23ffffff
[4294671.731000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.731000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294671.731000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294671.731000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294671.731000] audit: initializing netlink socket (disabled)
[4294671.731000] audit(1154565874.730:1): initialized
[4294671.731000] VFS: Disk quotas dquot_6.5.1
[4294671.731000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.732000] Initializing Cryptographic API
[4294671.732000] io scheduler noop registered
[4294671.732000] io scheduler anticipatory registered
[4294671.732000] io scheduler deadline registered
[4294671.732000] io scheduler cfq registered
[4294671.732000] isapnp: Scanning for PnP cards...
[4294672.089000] isapnp: No Plug & Play device found
[4294672.103000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294672.105000] spurious 8259A interrupt: IRQ7.
[4294672.105000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294672.106000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294672.106000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294672.107000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294672.107000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294672.107000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.107000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294672.109000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.109000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.109000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.110000] mice: PS/2 mouse device common for all mice
[4294672.110000] EISA: Probing bus 0 at eisa.0
[4294672.110000] Cannot allocate resource for EISA slot 1
[4294672.110000] EISA: Detected 0 cards.
[4294672.110000] NET: Registered protocol family 2
[4294672.120000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294672.120000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.120000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.120000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.120000] TCP reno registered
[4294672.120000] TCP bic registered
[4294672.120000] NET: Registered protocol family 1
[4294672.120000] NET: Registered protocol family 8
[4294672.120000] NET: Registered protocol family 20
[4294672.120000] Using IPI Shortcut mode
[4294672.120000] ACPI wakeup devices:
[4294672.120000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294672.120000] ACPI: (supports S0 S3 S4 S5)
[4294672.120000] Freeing unused kernel memory: 288k freed
[4294672.176000] vga16fb: initializing
[4294672.176000] vga16fb: mapped to 0xc00a0000
[4294672.269000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.317000] Console: switching to colour frame buffer device 80x25
[4294672.317000] fb0: VGA16 VGA frame buffer device
[4294673.405000] Capability LSM initialized
[4294673.441000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294673.565000] ACPI: Thermal Zone [THRM] (0 C)
[4294673.981000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294673.981000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294673.981000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 14
[4294673.981000] VP_IDE: chipset revision 6
[4294673.981000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.981000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294673.981000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294673.981000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294673.981000] Probing IDE interface ide0...
[4294674.367000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294674.673000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.696000] Probing IDE interface ide1...
[4294675.490000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294676.102000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.109000] hda: max request size: 1024KiB
[4294676.118000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294676.118000] hda: cache flushes supported
[4294676.118000]  hda: hda1 hda2 < hda5 >
[4294676.190000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294676.190000] Uniform CD-ROM driver Revision: 3.20
[4294676.500000] usbcore: registered new driver usbfs
[4294676.501000] usbcore: registered new driver hub
[4294676.533000] PCI: IRQ 0 for device 0000:00:10.3 doesn't match PIRQ mask - try pci=usepirqmask
[4294676.533000] PCI: setting IRQ 6 as level-triggered
[4294676.533000] PCI: Assigned IRQ 6 for device 0000:00:10.3
[4294676.533000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.533000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.533000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.533000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 6
[4294676.534000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294676.534000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[4294676.534000] ehci_hcd 0000:00:10.3: irq 6, io mem 0xdfffdf00
[4294676.534000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.534000] hub 1-0:1.0: USB hub found
[4294676.534000] hub 1-0:1.0: 6 ports detected
[4294676.534000] USB Universal Host Controller Interface driver v2.3
[4294676.535000] PCI: Found IRQ 6 for device 0000:00:10.0
[4294676.535000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.535000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.535000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.535000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 6
[4294676.535000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294676.635000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[4294676.636000] uhci_hcd 0000:00:10.0: irq 6, io base 0x0000e400
[4294676.636000] hub 2-0:1.0: USB hub found
[4294676.636000] hub 2-0:1.0: 2 ports detected
[4294676.737000] PCI: Found IRQ 6 for device 0000:00:10.1
[4294676.737000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.737000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.737000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.737000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 6
[4294676.737000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294676.737000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[4294676.737000] uhci_hcd 0000:00:10.1: irq 6, io base 0x0000e800
[4294676.737000] hub 3-0:1.0: USB hub found
[4294676.737000] hub 3-0:1.0: 2 ports detected
[4294676.838000] PCI: Found IRQ 6 for device 0000:00:10.2
[4294676.838000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.838000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.838000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.838000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 6
[4294676.838000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294676.838000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[4294676.838000] uhci_hcd 0000:00:10.2: irq 6, io base 0x0000ec00
[4294676.838000] hub 4-0:1.0: USB hub found
[4294676.838000] hub 4-0:1.0: 2 ports detected
[4294676.841000] usb 1-1: new high speed USB device using ehci_hcd and address 2[4294676.995000] SCSI subsystem initialized
[4294676.998000] Initializing USB Mass Storage driver...
[4294677.164000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294677.164000] usb-storage: device found at 2
[4294677.164000] usb-storage: waiting for device to settle before scanning
[4294677.164000] usbcore: registered new driver usb-storage
[4294677.164000] USB Mass Storage support registered.
[4294677.301000] Attempting manual resume
[4294677.371000] EXT3-fs: mounted filesystem with ordered data mode.
[4294677.386000] kjournald starting.  Commit interval 5 seconds
[4294680.135000] usb 1-1: USB disconnect, address 2
[4294691.412000] PCI: Found IRQ 11 for device 0000:00:09.0
[4294691.412000] PCI: Sharing IRQ 11 with 0000:00:12.0
[4294691.412000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294691.463000] PCI: Found IRQ 10 for device 0000:00:11.6
[4294691.463000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294691.463000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294691.464000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294691.476000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294691.476000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294691.476000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294691.476000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294691.476000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294691.476000] Yenta O2: enabling read prefetch/write burst
[4294691.598000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[4294691.598000] Socket status: 30000007
[4294691.633000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.674000] Real Time Clock Driver v1.12
[4294691.689000] Linux agpgart interface v0.101 (c) Dave Jones
[4294691.695000] agpgart: Detected VIA KM400/KM400A chipset
[4294691.700000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294691.715000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294691.975000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.976000] PCI: Found IRQ 11 for device 0000:00:12.0
[4294691.976000] PCI: Sharing IRQ 11 with 0000:00:09.0
[4294691.980000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294691.981000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[4294692.054000] PCI: Found IRQ 10 for device 0000:00:11.5
[4294692.054000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294692.054000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294692.054000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294692.055000] input: PC Speaker as /class/input/input1
[4294692.209000] irda_init()
[4294692.209000] NET: Registered protocol family 23
[4294692.583000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294692.623000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294692.660000] ts: Compaq touchscreen protocol output
[4294692.855000] cs: IO port probe 0x100-0x3af: clean.
[4294693.251000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294693.252000] cs: IO port probe 0x820-0x8ff: clean.
[4294693.253000] cs: IO port probe 0xc00-0xcf7: clean.
[4294693.253000] cs: IO port probe 0xa00-0xaff: clean.
[4294693.394000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294694.153000] lp: driver loaded but no devices found
[4294694.216000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294694.350000] EXT3 FS on hda1, internal journal
[4294694.461000] NET: Registered protocol family 17
[4294694.560000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.560000] md: bitmap version 4.39
[4294695.187000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294695.827000] cdrom: open failed.
[4294702.091000] ACPI: AC Adapter [AC] (on-line)
[4294702.156000] ACPI: Battery Slot [BAT0] (battery present)
[4294702.226000] ACPI: Power Button (FF) [PWRF]
[4294702.226000] ACPI: Power Button (CM) [PWRB]
[4294702.226000] ACPI: Sleep Button (CM) [SLPB]
[4294702.226000] ACPI: Lid Switch [LIDD]
[4294702.347000] ibm_acpi: ec object not found
[4294702.372000] pcc_acpi: loading...
[4294702.474000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294702.910000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294702.915000] Detected 1658.952 MHz processor.
[4294702.919000] powernow: SGTC: 13333
[4294702.919000] powernow: Minimum speed 398 MHz. Maximum speed 1658 MHz.
[4294707.330000] [drm] Initialized drm 1.0.1 20051102
[4294707.350000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294707.351000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294707.881000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294707.881000] agpgart: Device is in legacy mode, falling back to 2.x
[4294707.881000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294707.881000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294709.514000] ppdev: user-space parallel port driver
[4294709.855000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294709.856000] apm: overridden by ACPI.
[4294711.002000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294713.771000] Bluetooth: Core ver 2.8
[4294713.771000] NET: Registered protocol family 31
[4294713.771000] Bluetooth: HCI device and connection manager initialized
[4294713.771000] Bluetooth: HCI socket layer initialized
[4294714.100000] Bluetooth: L2CAP ver 2.8
[4294714.100000] Bluetooth: L2CAP socket layer initialized
[4294714.133000] Bluetooth: RFCOMM socket layer initialized
[4294714.133000] Bluetooth: RFCOMM TTY layer initialized
[4294714.133000] Bluetooth: RFCOMM ver 1.7
[4294731.535000] NET: Registered protocol family 10
[4294731.535000] lo: Disabled Privacy Extensions
[4294731.535000] IPv6 over IPv4 tunneling driver
[4294742.477000] eth0: no IPv6 routers present
[4294746.841000] usb 1-3: new high speed USB device using ehci_hcd and address 3[4294746.957000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294746.957000] usb-storage: device found at 3
[4294746.957000] usb-storage: waiting for device to settle before scanning
[4294751.957000]   Vendor: CREATIVE  Model: MuVo TX FM        Rev: 1182
[4294751.957000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294751.964000] usb-storage: device scan complete
[4294752.095000] Driver 'sd' needs updating - please use bus_type methods
[4294752.100000] SCSI device sda: 496896 512-byte hdwr sectors (254 MB)
[4294752.101000] sda: Write Protect is off
[4294752.101000] sda: Mode Sense: 38 00 00 00
[4294752.101000] sda: assuming drive cache: write through
[4294752.106000] SCSI device sda: 496896 512-byte hdwr sectors (254 MB)
[4294752.109000] sda: Write Protect is off
[4294752.110000] sda: Mode Sense: 38 00 00 00
[4294752.110000] sda: assuming drive cache: write through
[4294752.110000]  sda: sda1
[4294752.112000] sd 1:0:0:0: Attached scsi removable disk sda
[4294752.154000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[4294753.170000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294866.999000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294877.771000] eth0: no IPv6 routers present

---

### Post by spazsui on 2006-08-02
jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash lapic irqpoll acpi=noirq
[4294667.296000] Misrouted IRQ fixup and polling support enabled
[4294667.296000] This may significantly impact system performance
[4294667.296000] Local APIC disabled by BIOS -- reenabling.
[4294667.296000] Found and enabled local APIC!
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1658.572 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.343000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294667.344000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294667.363000] Memory: 476468k/491456k available (1976k kernel code, 14384k reserved, 606k data, 288k init, 0k highmem)
[4294667.363000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.424000] Calibrating delay using timer specific routine.. 3321.07 BogoMIPS (lpj=1660538)
[4294667.424000] Security Framework v1.0.0 initialized
[4294667.424000] SELinux:  Disabled at boot.
[4294667.424000] Mount-cache hash table entries: 512
[4294667.424000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294667.424000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294667.424000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.424000] CPU: L2 Cache: 512K (64 bytes/line)
[4294667.424000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000020 00000000 00000000 00000000
[4294667.424000] mtrr: v2.0 (20020519)
[4294667.424000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294667.424000] Enabling fast FPU save and restore... done.
[4294667.424000] Enabling unmasked SIMD FPU exception support... done.
[4294667.424000] Checking 'hlt' instruction... OK.
[4294667.428000] checking if image is initramfs... it is
[4294668.101000] Freeing initrd memory: 6836k freed
[4294668.120000] ACPI: Looking for DSDT ... not found!
[4294668.122000] ACPI: setting ELCR to 0e00 (from 0c00)
[4294668.236000] NET: Registered protocol family 16
[4294668.236000] EISA bus registered
[4294668.236000] ACPI: bus type pci registered
[4294668.237000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294668.237000] PCI: Using configuration type 1
[4294668.237000] ACPI: Subsystem revision 20051216
[4294668.242000] ACPI: Interpreter enabled
[4294668.242000] ACPI: Using PIC for interrupt routing
[4294668.242000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.242000] PCI: Probing PCI hardware (bus 00)
[4294668.244000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294668.244000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294668.244000] Boot video device is 0000:01:00.0
[4294668.244000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.248000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294668.250000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294668.251000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.251000] pnp: PnP ACPI init
[4294668.253000] pnp: PnP ACPI: found 8 devices
[4294668.253000] PnPBIOS: Disabled by ACPI PNP
[4294668.253000] PCI: Probing PCI hardware
[4294668.253000] PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
[4294668.253000] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294668.253000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294668.253000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294668.253000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294668.253000] PCI: IRQ 0 for device 0000:00:10.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294668.253000] PCI: IRQ 0 for device 0000:00:10.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294668.253000] PCI: IRQ 0 for device 0000:00:10.2 doesn't match PIRQ mask - try pci=usepirqmask
[4294668.253000] PCI: IRQ 0 for device 0000:00:10.3 doesn't match PIRQ mask - try pci=usepirqmask
[4294668.253000] PCI: IRQ 0 for device 0000:00:11.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294668.253000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294668.256000] PCI: Bridge: 0000:00:01.0
[4294668.256000]   IO window: disabled.
[4294668.256000]   MEM window: dde00000-dfefffff
[4294668.256000]   PREFETCH window: d5d00000-ddcfffff
[4294668.256000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294668.256000]   IO window: 00001000-000010ff
[4294668.256000]   IO window: 00001400-000014ff
[4294668.256000]   PREFETCH window: 20000000-21ffffff
[4294668.256000]   MEM window: 22000000-23ffffff
[4294668.256000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294668.256000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294668.256000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294668.256000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294668.257000] audit: initializing netlink socket (disabled)
[4294668.257000] audit(1154566416.256:1): initialized
[4294668.257000] VFS: Disk quotas dquot_6.5.1
[4294668.257000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.257000] Initializing Cryptographic API
[4294668.257000] io scheduler noop registered
[4294668.257000] io scheduler anticipatory registered
[4294668.257000] io scheduler deadline registered
[4294668.257000] io scheduler cfq registered
[4294668.257000] isapnp: Scanning for PnP cards...
[4294668.615000] isapnp: No Plug & Play device found
[4294668.629000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294668.630000] spurious 8259A interrupt: IRQ7.
[4294668.631000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294668.632000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294668.633000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294668.633000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294668.633000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294668.633000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.633000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294668.635000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.635000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294668.635000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294668.636000] mice: PS/2 mouse device common for all mice
[4294668.636000] EISA: Probing bus 0 at eisa.0
[4294668.636000] Cannot allocate resource for EISA slot 1
[4294668.636000] EISA: Detected 0 cards.
[4294668.636000] NET: Registered protocol family 2
[4294668.646000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294668.646000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.646000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.646000] TCP: Hash tables configured (established 16384 bind 16384)
[4294668.646000] TCP reno registered
[4294668.646000] TCP bic registered
[4294668.646000] NET: Registered protocol family 1
[4294668.646000] NET: Registered protocol family 8
[4294668.646000] NET: Registered protocol family 20
[4294668.646000] Using IPI Shortcut mode
[4294668.646000] ACPI wakeup devices:
[4294668.646000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294668.646000] ACPI: (supports S0 S3 S4 S5)
[4294668.646000] Freeing unused kernel memory: 288k freed
[4294668.703000] vga16fb: initializing
[4294668.703000] vga16fb: mapped to 0xc00a0000
[4294668.795000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294668.844000] Console: switching to colour frame buffer device 80x25
[4294668.844000] fb0: VGA16 VGA frame buffer device
[4294669.937000] Capability LSM initialized
[4294669.973000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294670.097000] ACPI: Thermal Zone [THRM] (0 C)
[4294670.537000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294670.537000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294670.537000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 14
[4294670.537000] VP_IDE: chipset revision 6
[4294670.537000] VP_IDE: not 100% native mode: will probe irqs later
[4294670.537000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294670.537000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294670.537000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294670.537000] Probing IDE interface ide0...
[4294670.923000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294671.229000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.252000] Probing IDE interface ide1...
[4294672.046000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294672.658000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.665000] hda: max request size: 1024KiB
[4294672.674000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294672.675000] hda: cache flushes supported
[4294672.675000]  hda: hda1 hda2 < hda5 >
[4294672.748000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294672.748000] Uniform CD-ROM driver Revision: 3.20
[4294673.056000] usbcore: registered new driver usbfs
[4294673.057000] usbcore: registered new driver hub
[4294673.058000] USB Universal Host Controller Interface driver v2.3
[4294673.059000] PCI: IRQ 0 for device 0000:00:10.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294673.059000] PCI: setting IRQ 6 as level-triggered
[4294673.059000] PCI: Assigned IRQ 6 for device 0000:00:10.0
[4294673.059000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294673.059000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294673.059000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294673.059000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 6
[4294673.059000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294673.059000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294673.059000] uhci_hcd 0000:00:10.0: irq 6, io base 0x0000e400
[4294673.060000] hub 1-0:1.0: USB hub found
[4294673.060000] hub 1-0:1.0: 2 ports detected
[4294673.161000] PCI: Found IRQ 6 for device 0000:00:10.1
[4294673.161000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294673.161000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294673.161000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294673.161000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 6
[4294673.161000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294673.161000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294673.161000] uhci_hcd 0000:00:10.1: irq 6, io base 0x0000e800
[4294673.161000] hub 2-0:1.0: USB hub found
[4294673.161000] hub 2-0:1.0: 2 ports detected
[4294673.262000] PCI: Found IRQ 6 for device 0000:00:10.2
[4294673.262000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294673.262000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294673.262000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294673.262000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 6
[4294673.262000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294673.262000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294673.262000] uhci_hcd 0000:00:10.2: irq 6, io base 0x0000ec00
[4294673.262000] hub 3-0:1.0: USB hub found
[4294673.262000] hub 3-0:1.0: 2 ports detected
[4294673.365000] PCI: Found IRQ 6 for device 0000:00:10.3
[4294673.365000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294673.365000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294673.365000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294673.365000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 6
[4294673.365000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294673.365000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294673.365000] ehci_hcd 0000:00:10.3: irq 6, io mem 0xdfffdf00
[4294673.365000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294673.366000] hub 4-0:1.0: USB hub found
[4294673.366000] hub 4-0:1.0: 6 ports detected
[4294673.603000] Attempting manual resume
[4294673.673000] EXT3-fs: mounted filesystem with ordered data mode.
[4294673.687000] kjournald starting.  Commit interval 5 seconds
[4294673.991000] usb 4-3: new high speed USB device using ehci_hcd and address 2[4294680.967000] usb 4-3: USB disconnect, address 2
[4294687.579000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294687.585000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294687.719000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294687.719000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294687.719000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294687.719000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294687.719000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294687.719000] Yenta O2: enabling read prefetch/write burst
[4294687.756000] PCI: Found IRQ 11 for device 0000:00:09.0
[4294687.756000] PCI: Sharing IRQ 11 with 0000:00:12.0
[4294687.756000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294687.841000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[4294687.841000] Socket status: 30000007
[4294688.380000] input: PC Speaker as /class/input/input1
[4294688.401000] Real Time Clock Driver v1.12
[4294688.573000] Linux agpgart interface v0.101 (c) Dave Jones
[4294688.599000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294688.599000] PCI: Found IRQ 11 for device 0000:00:12.0
[4294688.599000] PCI: Sharing IRQ 11 with 0000:00:09.0
[4294688.603000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294688.604000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[4294688.628000] irda_init()
[4294688.628000] NET: Registered protocol family 23
[4294688.650000] agpgart: Detected VIA KM400/KM400A chipset
[4294688.655000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294688.731000] PCI: Found IRQ 10 for device 0000:00:11.6
[4294688.731000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294688.731000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294688.732000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294688.921000] PCI: Found IRQ 10 for device 0000:00:11.5
[4294688.921000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294688.921000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294688.922000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294688.958000] cs: IO port probe 0x100-0x3af: clean.
[4294688.960000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294688.961000] cs: IO port probe 0x820-0x8ff: clean.
[4294688.961000] cs: IO port probe 0xc00-0xcf7: clean.
[4294688.962000] cs: IO port probe 0xa00-0xaff: clean.
[4294689.021000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294689.061000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294689.078000] ts: Compaq touchscreen protocol output
[4294689.568000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294690.071000] lp: driver loaded but no devices found
[4294690.138000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294690.353000] EXT3 FS on hda1, internal journal
[4294690.563000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294690.563000] md: bitmap version 4.39
[4294690.620000] NET: Registered protocol family 17
[4294691.176000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294691.816000] cdrom: open failed.
[4294698.099000] ACPI: AC Adapter [AC] (on-line)
[4294698.166000] ACPI: Battery Slot [BAT0] (battery present)
[4294698.239000] ACPI: Power Button (FF) [PWRF]
[4294698.239000] ACPI: Power Button (CM) [PWRB]
[4294698.239000] ACPI: Sleep Button (CM) [SLPB]
[4294698.239000] ACPI: Lid Switch [LIDD]
[4294698.392000] ibm_acpi: ec object not found
[4294698.418000] pcc_acpi: loading...
[4294698.524000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294698.970000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294698.975000] Detected 1659.522 MHz processor.
[4294698.979000] powernow: SGTC: 13333
[4294698.979000] powernow: Minimum speed 398 MHz. Maximum speed 1659 MHz.
[4294703.333000] [drm] Initialized drm 1.0.1 20051102
[4294703.352000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294703.353000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294703.867000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294703.867000] agpgart: Device is in legacy mode, falling back to 2.x
[4294703.867000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294703.867000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294705.602000] ppdev: user-space parallel port driver
[4294705.957000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294705.957000] apm: overridden by ACPI.
[4294707.291000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294710.143000] Bluetooth: Core ver 2.8
[4294710.143000] NET: Registered protocol family 31
[4294710.143000] Bluetooth: HCI device and connection manager initialized
[4294710.143000] Bluetooth: HCI socket layer initialized
[4294710.218000] Bluetooth: L2CAP ver 2.8
[4294710.218000] Bluetooth: L2CAP socket layer initialized
[4294710.249000] Bluetooth: RFCOMM socket layer initialized
[4294710.249000] Bluetooth: RFCOMM TTY layer initialized
[4294710.249000] Bluetooth: RFCOMM ver 1.7
[4294726.300000] NET: Registered protocol family 10
[4294726.301000] lo: Disabled Privacy Extensions
[4294726.301000] IPv6 over IPv4 tunneling driver
[4294736.676000] eth0: no IPv6 routers present
[4294812.965000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)


So what do you think?  The first one looks like it may have been enabled at least at one time.

---

### Post by wiresquire on 2006-08-03
Spazsui

Can you please try the #4 enabling lapic AND acpi=noirq again? Then go into the Network Settings (from the menu System/Administration/Networking). Deactivate the Ethernet connection, and then try re-enabling it.

Pls post the dmesg and also the result of ifconfig and route. Then try accessing the network.

Regards
ws

---

### Post by spazsui on 2006-08-03
This actually worked!  Here is the info you requested!  I am happy!:D 


jp2@jp2-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:45:19:EA:1E
          inet addr:65.60.234.154  Bcast:65.60.239.255  Mask:255.255.240.0
          inet6 addr: fe80::240:45ff:fe19:ea1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:342367 (334.3 KiB)  TX bytes:5641 (5.5 KiB)
          Interrupt:11 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

jp2@jp2-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
65.60.224.0     *               255.255.240.0   U     0      0        0 eth0
default         d60-65-1-224.co 0.0.0.0         UG    0      0        0 eth0
jp2@jp2-laptop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 479MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 122864
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 118768 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa2d0
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1dff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1dff0030
[4294667.296000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 INTL 0x02002024) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash lapic acpi=noirq
[4294667.296000] Local APIC disabled by BIOS -- reenabling.
[4294667.296000] Found and enabled local APIC!
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1658.683 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.380000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294670.381000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.399000] Memory: 476468k/491456k available (1976k kernel code, 14384k reserved, 606k data, 288k init, 0k highmem)
[4294670.399000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.459000] Calibrating delay using timer specific routine.. 3320.05 BogoMIPS (lpj=1660027)
[4294670.459000] Security Framework v1.0.0 initialized
[4294670.459000] SELinux:  Disabled at boot.
[4294670.459000] Mount-cache hash table entries: 512
[4294670.459000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294670.459000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[4294670.459000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294670.459000] CPU: L2 Cache: 512K (64 bytes/line)
[4294670.459000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000020 00000000 00000000 00000000
[4294670.459000] mtrr: v2.0 (20020519)
[4294670.459000] CPU: AMD mobile AMD Athlon(tm) XP-M (LV) 2200+ stepping 00
[4294670.459000] Enabling fast FPU save and restore... done.
[4294670.459000] Enabling unmasked SIMD FPU exception support... done.
[4294670.459000] Checking 'hlt' instruction... OK.
[4294670.463000] checking if image is initramfs... it is
[4294671.130000] Freeing initrd memory: 6836k freed
[4294671.147000] ACPI: Looking for DSDT ... not found!
[4294671.149000] ACPI: setting ELCR to 0e00 (from 0c00)
[4294671.262000] NET: Registered protocol family 16
[4294671.262000] EISA bus registered
[4294671.262000] ACPI: bus type pci registered
[4294671.263000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294671.263000] PCI: Using configuration type 1
[4294671.263000] ACPI: Subsystem revision 20051216
[4294671.268000] ACPI: Interpreter enabled
[4294671.268000] ACPI: Using PIC for interrupt routing
[4294671.268000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.268000] PCI: Probing PCI hardware (bus 00)
[4294671.270000] PCI quirk: region 0800-087f claimed by vt8235 PM
[4294671.270000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[4294671.270000] Boot video device is 0000:01:00.0
[4294671.270000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.274000] ACPI: Embedded Controller [ECD] (gpe 4) interrupt mode.
[4294671.275000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294671.277000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.277000] pnp: PnP ACPI init
[4294671.278000] pnp: PnP ACPI: found 8 devices
[4294671.278000] PnPBIOS: Disabled by ACPI PNP
[4294671.278000] PCI: Probing PCI hardware
[4294671.278000] PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
[4294671.278000] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.278000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294671.278000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294671.278000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294671.278000] PCI: IRQ 0 for device 0000:00:10.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.278000] PCI: IRQ 0 for device 0000:00:10.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.278000] PCI: IRQ 0 for device 0000:00:10.2 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.278000] PCI: IRQ 0 for device 0000:00:10.3 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.278000] PCI: IRQ 0 for device 0000:00:11.1 doesn't match PIRQ mask - try pci=usepirqmask
[4294671.278000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294671.282000] PCI: Bridge: 0000:00:01.0
[4294671.282000]   IO window: disabled.
[4294671.282000]   MEM window: dde00000-dfefffff
[4294671.282000]   PREFETCH window: d5d00000-ddcfffff
[4294671.282000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294671.282000]   IO window: 00001000-000010ff
[4294671.282000]   IO window: 00001400-000014ff
[4294671.282000]   PREFETCH window: 20000000-21ffffff
[4294671.282000]   MEM window: 22000000-23ffffff
[4294671.282000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.282000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294671.282000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294671.282000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294671.282000] audit: initializing netlink socket (disabled)
[4294671.282000] audit(1154648627.281:1): initialized
[4294671.282000] VFS: Disk quotas dquot_6.5.1
[4294671.283000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.283000] Initializing Cryptographic API
[4294671.283000] io scheduler noop registered
[4294671.283000] io scheduler anticipatory registered
[4294671.283000] io scheduler deadline registered
[4294671.283000] io scheduler cfq registered
[4294671.283000] isapnp: Scanning for PnP cards...
[4294671.640000] isapnp: No Plug & Play device found
[4294671.654000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.655000] spurious 8259A interrupt: IRQ7.
[4294671.656000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294671.657000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294671.658000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294671.658000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294671.658000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294671.658000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.658000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.660000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.660000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.660000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.661000] mice: PS/2 mouse device common for all mice
[4294671.661000] EISA: Probing bus 0 at eisa.0
[4294671.661000] Cannot allocate resource for EISA slot 1
[4294671.661000] EISA: Detected 0 cards.
[4294671.661000] NET: Registered protocol family 2
[4294671.671000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294671.671000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.671000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.671000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.671000] TCP reno registered
[4294671.671000] TCP bic registered
[4294671.671000] NET: Registered protocol family 1
[4294671.671000] NET: Registered protocol family 8
[4294671.671000] NET: Registered protocol family 20
[4294671.671000] Using IPI Shortcut mode
[4294671.671000] ACPI wakeup devices:
[4294671.671000] SLPB PCI0 USB1 USB2 USB3 EHCI  MC9 ILAN
[4294671.671000] ACPI: (supports S0 S3 S4 S5)
[4294671.671000] Freeing unused kernel memory: 288k freed
[4294671.728000] vga16fb: initializing
[4294671.728000] vga16fb: mapped to 0xc00a0000
[4294671.820000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.868000] Console: switching to colour frame buffer device 80x25
[4294671.868000] fb0: VGA16 VGA frame buffer device
[4294672.959000] Capability LSM initialized
[4294672.995000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294673.121000] ACPI: Thermal Zone [THRM] (0 C)
[4294673.552000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294673.552000] PCI: Hardcoded IRQ 14 for device 0000:00:11.1
[4294673.552000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 14
[4294673.552000] VP_IDE: chipset revision 6
[4294673.552000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.552000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294673.552000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294673.552000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294673.552000] Probing IDE interface ide0...
[4294673.938000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294674.244000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.544000] Probing IDE interface ide1...
[4294675.338000] hdc: QSI CD-RW/DVD-ROM SBW242B, ATAPI CD/DVD-ROM drive
[4294675.950000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.957000] hda: max request size: 1024KiB
[4294675.966000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294675.966000] hda: cache flushes supported
[4294675.966000]  hda: hda1 hda2 < hda5 >
[4294676.031000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294676.031000] Uniform CD-ROM driver Revision: 3.20
[4294676.347000] usbcore: registered new driver usbfs
[4294676.347000] usbcore: registered new driver hub
[4294676.349000] USB Universal Host Controller Interface driver v2.3
[4294676.349000] PCI: IRQ 0 for device 0000:00:10.0 doesn't match PIRQ mask - try pci=usepirqmask
[4294676.349000] PCI: setting IRQ 6 as level-triggered
[4294676.349000] PCI: Assigned IRQ 6 for device 0000:00:10.0
[4294676.349000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.349000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.349000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.349000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 6
[4294676.349000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294676.383000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294676.383000] uhci_hcd 0000:00:10.0: irq 6, io base 0x0000e400
[4294676.384000] hub 1-0:1.0: USB hub found
[4294676.384000] hub 1-0:1.0: 2 ports detected
[4294676.485000] PCI: Found IRQ 6 for device 0000:00:10.1
[4294676.485000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.485000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.485000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.485000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 6
[4294676.485000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294676.485000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294676.485000] uhci_hcd 0000:00:10.1: irq 6, io base 0x0000e800
[4294676.485000] hub 2-0:1.0: USB hub found
[4294676.485000] hub 2-0:1.0: 2 ports detected
[4294676.586000] PCI: Found IRQ 6 for device 0000:00:10.2
[4294676.586000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.586000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.586000] PCI: Sharing IRQ 6 with 0000:00:10.3
[4294676.586000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 6
[4294676.586000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294676.586000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294676.586000] uhci_hcd 0000:00:10.2: irq 6, io base 0x0000ec00
[4294676.586000] hub 3-0:1.0: USB hub found
[4294676.586000] hub 3-0:1.0: 2 ports detected
[4294676.689000] PCI: Found IRQ 6 for device 0000:00:10.3
[4294676.689000] PCI: Sharing IRQ 6 with 0000:00:10.2
[4294676.689000] PCI: Sharing IRQ 6 with 0000:00:10.1
[4294676.689000] PCI: Sharing IRQ 6 with 0000:00:10.0
[4294676.689000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 6
[4294676.689000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[4294676.689000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294676.689000] ehci_hcd 0000:00:10.3: irq 6, io mem 0xdfffdf00
[4294676.689000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.689000] hub 4-0:1.0: USB hub found
[4294676.689000] hub 4-0:1.0: 6 ports detected
[4294676.928000] Attempting manual resume
[4294676.998000] EXT3-fs: mounted filesystem with ordered data mode.
[4294677.012000] kjournald starting.  Commit interval 5 seconds
[4294690.749000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294690.811000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294690.903000] PCI: Found IRQ 10 for device 0000:00:0a.0
[4294690.903000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294690.903000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294690.903000] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[4294690.903000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294690.903000] Yenta O2: enabling read prefetch/write burst
[4294690.940000] PCI: Found IRQ 11 for device 0000:00:09.0
[4294690.940000] PCI: Sharing IRQ 11 with 0000:00:12.0
[4294690.940000] rt2500 1.1.0 BETA3 2005/07/31 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[4294691.025000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[4294691.025000] Socket status: 30000007
[4294691.349000] input: PC Speaker as /class/input/input1
[4294691.583000] PCI: Found IRQ 10 for device 0000:00:11.6
[4294691.583000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294691.583000] PCI: Sharing IRQ 10 with 0000:00:11.5
[4294691.657000] PCI: Found IRQ 10 for device 0000:00:11.5
[4294691.657000] PCI: Sharing IRQ 10 with 0000:00:0a.0
[4294691.657000] PCI: Sharing IRQ 10 with 0000:00:11.6
[4294691.657000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294691.671000] Real Time Clock Driver v1.12
[4294691.683000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294691.700000] Linux agpgart interface v0.101 (c) Dave Jones
[4294691.726000] irda_init()
[4294691.726000] NET: Registered protocol family 23
[4294691.763000] agpgart: Detected VIA KM400/KM400A chipset
[4294691.768000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294691.883000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294692.039000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294692.078000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294692.095000] ts: Compaq touchscreen protocol output
[4294692.213000] cs: IO port probe 0x100-0x3af: clean.
[4294692.215000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294692.216000] cs: IO port probe 0x820-0x8ff: clean.
[4294692.216000] cs: IO port probe 0xc00-0xcf7: clean.
[4294692.217000] cs: IO port probe 0xa00-0xaff: clean.
[4294692.404000] PCI: Found IRQ 11 for device 0000:00:12.0
[4294692.404000] PCI: Sharing IRQ 11 with 0000:00:09.0
[4294692.408000] eth0: VIA Rhine II at 0x1d800, 00:40:45:19:ea:1e, IRQ 11.
[4294692.409000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[4294692.979000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294693.156000] lp: driver loaded but no devices found
[4294693.219000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[4294693.423000] EXT3 FS on hda1, internal journal
[4294693.648000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294693.648000] md: bitmap version 4.39
[4294694.444000] NET: Registered protocol family 17
[4294694.501000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294695.423000] cdrom: open failed.
[4294695.564000] NET: Registered protocol family 10
[4294695.565000] lo: Disabled Privacy Extensions
[4294695.565000] IPv6 over IPv4 tunneling driver
[4294701.333000] ACPI: AC Adapter [AC] (on-line)
[4294701.407000] ACPI: Battery Slot [BAT0] (battery present)
[4294701.475000] ACPI: Power Button (FF) [PWRF]
[4294701.475000] ACPI: Power Button (CM) [PWRB]
[4294701.475000] ACPI: Sleep Button (CM) [SLPB]
[4294701.475000] ACPI: Lid Switch [LIDD]
[4294701.604000] ibm_acpi: ec object not found
[4294701.630000] pcc_acpi: loading...
[4294701.731000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294702.168000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294702.173000] Detected 1659.752 MHz processor.
[4294702.177000] powernow: SGTC: 13333
[4294702.177000] powernow: Minimum speed 398 MHz. Maximum speed 1659 MHz.
[4294705.698000] eth0: no IPv6 routers present
[4294706.489000] [drm] Initialized drm 1.0.1 20051102
[4294706.508000] [drm] Initialized via 2.7.4 20051116 on minor 0
[4294706.509000] mtrr: 0xd8000000,0x2000000 overlaps existing 0xd8000000,0x200000
[4294707.096000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294707.096000] agpgart: Device is in legacy mode, falling back to 2.x
[4294707.096000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294707.096000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294708.744000] ppdev: user-space parallel port driver
[4294709.085000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294709.085000] apm: overridden by ACPI.
[4294710.245000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294712.887000] Bluetooth: Core ver 2.8
[4294712.887000] NET: Registered protocol family 31
[4294712.887000] Bluetooth: HCI device and connection manager initialized
[4294712.887000] Bluetooth: HCI socket layer initialized
[4294712.994000] Bluetooth: L2CAP ver 2.8
[4294712.994000] Bluetooth: L2CAP socket layer initialized
[4294713.036000] Bluetooth: RFCOMM socket layer initialized
[4294713.036000] Bluetooth: RFCOMM TTY layer initialized
[4294713.036000] Bluetooth: RFCOMM ver 1.7
[4294840.612000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294851.293000] eth0: no IPv6 routers present

So I downloaded all of the updates.  Did they fix this bug in the new updates?  The way I read it sounds like they may have.  If they didn't how do I make this permanent every bootup?  I really appreciate your help wiresquire!  You da man!

Of course now I can't get easy ubuntu to do my updates now.  says there is a broken package.

---

### Post by wiresquire on 2006-08-04
Congratulations! :D 

I don't know whether the updates will have fixed your problem or not.

From what I have seen posted elsewhere regarding this machine, what I suspect is the problem is actually with the BIOS. Now, there may be later revisions of your BIOS that you can 'flash', or update to, that will fix the problem. But I would usually only try to recommend that if I could walk you through it. I don't know how Averatec updates their BIOS. Could be easy, could be really hard.

That's actually a pretty cool thing about linux. You can even work around bugs in the BIOS.

Anyways, to make it permanent with every boot up, you need to :
```

sudo gedit /boot/grub/menu.lst

```
This will open up the grub configuration file. Keep scrolling down until after the 
## ## End Default Options ##
You should see your first entry when you boot up.
Then it's a simple matter of editing the kernel line so it matches the changes that worked:
```

kernel          /boot/*vmlinuz-2.6.15-26-k7* root=*/dev/hda6* ro quiet splash lapic acpi=noirq

```
Italics may be different for your machine - just leave them as they are.

Save the file, and you are done!

One more thing. When there's a kernel update, a new entry is added to the grub list. It's possible that the new options you have added above are not added when you do a kernel update. So just keep an eye out. If there's a kernel update, you may need to do the same as the above.

Glad it worked out for you
ws

---

### Post by yigal.weinstein on 2006-08-06
Well you found a solution and I am happy for you.  However I use the same laptop and have for the last 1 1/2 years.  I have little problem setting up wifi and ethernet.  Attached are my 
/etc/network/interfaces
/etc/X11/xorg.conf

these two are very important in configuring the network interfaces.

Note 1:
1. ra0 is the designated wireless connection in Ubuntu.
2. eth0 usually refers to just what it seams to i.e. the ethernet.

Note 2: I have NO special options for my kernel in /boot/grub/menu.lst.  It just works. 
  
suspend2 works incredibly well for our computer you may - if you have not already - install it using the instructions here: 
[http://www.ubuntuforums.org/showthread.php?t=221088]("http://www.ubuntuforums.org/showthread.php?t=221088")

Best

---

### Post by markmaus on 2007-05-18
I have the Averatec 3225.  Mine has the S3 Unichrome graphics that is not very well supported in Linux.  Chances are your video driver ¨via¨ in /etc/X11/xorg.conf is probably messing up your IRQs.  Change it to ¨vesa¨ (then your network will work, but you will have crappy video).  Also, take out the irqpolling stuff.  Or just install MEPIS.  It handles the via video better and you will have 3D graphics and network, but your fan will run all the time.

---

