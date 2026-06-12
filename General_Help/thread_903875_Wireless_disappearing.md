---
title: "Wireless disappearing"
date: 2008-08-28
forum: General Help
---

### Post by Bliepo32 on 2008-08-28
I have a laptop which is running xubuntu 8.04. I am using a wireless USB adapter (you know, looks like a USB stick, you plug them in, and you have a working wireless). When I plugged it in, it immediately showed up in the network manager, and I only had to configure it. And it worked. I could browse, use IRC, you name the lot.

But suddenly, the wireless connection was gone. So I opened the Network manager, only to discover that not only the wireless connection had gone, but that the wireless USB adapter didn't show up anymore either.

Anyway, it is a fresh install of xubuntu. I installed it using USB, because the CD-ROM drive isn't working. The installation went fine. No problems at all. The wireless AP is hidden, 802.11g, using channel 4, and encrypted using WPA2 Personal. The wireless USB adapter is from the brand König (don't bother Googling it, you will find nothing useful).

If you need additional information to help solve the problem just ask me. I will be happy to provide it.

---

### Post by ugm6hr on 2008-08-28
Include details as explained here: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

Also - what do you mean by "suddenly" gone?  After a reboot, upgrade, installation etc?

---

### Post by Bliepo32 on 2008-08-29
> **ugm6hr said:**
> Also - what do you mean by "suddenly" gone?  After a reboot, upgrade, installation etc?
Like I said. For example, one time I was just browsing (searching the forums here), and suddenly I got an error page.

When opening the network manager, I usually see something like this:
[LIST]
[*]Wireless connection (roaming mode enabled)
[*]Wired connection (roaming mode enabled)
[*]Point to point connection (roaming mode enabled)
[/LIST]

When the wireless network disappears I only see this in the network manager:
[LIST]
[*]Wired connection (roaming mode enabled)
[*]Point to point connection (roaming mode enabled)
[/LIST]

> **ugm6hr said:**
> Include details as explained here: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)
[LIST=1]
[*]I am trying to get online using a wireless USB adapter to connect to a wireless router (hidden access point, 802.11g, WPA2 Personal).
[*]I am using a König wireless USB adapter (cmp-WNUSB10). The wireless roputer was provided by my Internet Service Provider (Tele2). It doesn't not show any brand.
[*]My Internet Service Provider is tele2 (Netherlands/holland).
[*]I am using Xubuntu 8.04.
[*]Yes, I can get online using ethernet. But I want my laptop to be portable.
[*]I get online using another (desktop) computer which is connected by ethernet.
[*]
lspic:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)

```

lsusb:
```

Bus 004 Device 004: ID 148f:2573 Ralink Technology, Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04f3:0214 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

lshw (-class network):
```

  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:40:7a:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:0f:b8:f6:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.8 multicast=yes wireless=IEEE 802.11g

```
[*]No, I am not dual-booting at all.
[/LIST]

Things I tried are:
[LIST]
[*]Using wicd (which caused my wired network to stop working as well, so I reinstalled xubuntu)
[*]Using ndiswrapper, because I was told that even though it worked out of the box, using the windows drivers might stabilise the wireless USB adapter.
[*]Running modprobe -a, hoping that it would redetect the USB, but it didn't.
[/LIST]

---

### Post by Criminal.Sausage on 2008-08-29
I'm having the exact same problem! I'm using a linksys usb adapter. It works on other desktops, but my ubuntu fails to recognise it for some weird reason.. Like bliepo said, it just vanished. A temporary workaround for me was to simply do a 'lsusb' for some reason. But now it doesn't show up there either and my workaround is gone. Anyone know what the problem might be?

---

### Post by Bliepo32 on 2008-08-30
Allright, I have an update. I have been asked (IRC, ubuntu channel), if I had already run dmesg when the wireless disappeared. 
I had not done so yet, so when the wireless stopped, I ran the dmesg command. Strangely enough, that caused the wireless to work again.

Unfortunately, I closed the terminal, while I forgot to copy the output of dmesg ](*,)
Anyway. I waited for the wireless to disappear again, and it did. This time, I ran the dmesg command again, and didn't forget to copy it's output. Anyway, here it is:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001fefb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fefb000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130800) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130800
[    0.000000]   HighMem    130800 ->   130800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130800
[    0.000000] On node 0 totalpages: 130800
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125715 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6890 checksum 0
[    0.000000] ACPI: RSDP 000F6890, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1FEF5B3E, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1FEFAE74, 0074 (r1 KN400  PTLTW     6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 1FEF5B6A, 530A (r1  VIA   PTL_ACPI  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FEFBFC0, 0040
[    0.000000] ACPI: SSDT 1FEFAEE8, 0118 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dffe0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129779
[    0.000000] Kernel command line: root=UUID=6fc0270c-6a63-48d1-b8b0-bc44ff1f7b41 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 796.116 MHz processor.
[   29.206955] Console: colour VGA+ 80x25
[   29.206963] console [tty0] enabled
[   29.207693] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.208232] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.235831] Memory: 506628k/523200k available (2177k kernel code, 15968k reserved, 1006k data, 368k init, 0k highmem)
[   29.235851] virtual kernel memory layout:
[   29.235854]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   29.235857]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.235860]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   29.235863]     lowmem  : 0xc0000000 - 0xdfef0000   ( 510 MB)
[   29.235866]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   29.235869]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   29.235872]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   29.235879] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.235960] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   29.315980] Calibrating delay using timer specific routine.. 1594.27 BogoMIPS (lpj=3188556)
[   29.316042] Security Framework initialized
[   29.316053] SELinux:  Disabled at boot.
[   29.316089] AppArmor: AppArmor initialized
[   29.316099] Failure registering capabilities with primary security module.
[   29.316119] Mount-cache hash table entries: 512
[   29.316369] Initializing cgroup subsys ns
[   29.316378] Initializing cgroup subsys cpuacct
[   29.316399] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   29.316419] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.316425] CPU: L2 Cache: 512K (64 bytes/line)
[   29.316432] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   29.316454] Compat vDSO mapped to ffffe000.
[   29.316477] Checking 'hlt' instruction... OK.
[   29.332414] SMP alternatives: switching to UP code
[   29.334614] Freeing SMP alternatives: 11k freed
[   29.334870] Early unpacking initramfs... done
[   30.129851] ACPI: Core revision 20070126
[   30.130033] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.134032] ACPI: setting ELCR to 0400 (from 0a30)
[   30.144649] CPU0: AMD Mobile AMD Athlon(tm) XP 3000+ stepping 00
[   30.144662] SMP motherboard not detected.
[   30.144668] Local APIC not detected. Using dummy APIC emulation.
[   30.144781] Brought up 1 CPUs
[   30.144830] CPU0 attaching sched-domain:
[   30.144836]  domain 0: span 01
[   30.144840]   groups: 01
[   30.145273] net_namespace: 64 bytes
[   30.145287] Booting paravirtualized kernel on bare hardware
[   30.146375] Time: 22:00:39  Date: 08/29/08
[   30.146436] NET: Registered protocol family 16
[   30.146976] EISA bus registered
[   30.146999] ACPI: bus type pci registered
[   30.147447] PCI: PCI BIOS revision 2.10 entry at 0xfd65c, last bus=1
[   30.147453] PCI: Using configuration type 1
[   30.147468] Setting up standard PCI resources
[   30.151882] ACPI: EC: Look up EC in DSDT
[   30.157557] ACPI: Interpreter enabled
[   30.157564] ACPI: (supports S0 S3 S4 S5)
[   30.157590] ACPI: Using PIC for interrupt routing
[   30.170002] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[   30.170010] ACPI: EC: driver started in poll mode
[   30.170129] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.170777] PCI quirk: region 4000-407f claimed by vt8235 PM
[   30.170786] PCI quirk: region 8100-810f claimed by vt8235 SMB
[   30.171332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.184111] ACPI: PCI Interrupt Link [LNKA] (IRQs *4)
[   30.184330] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[   30.184549] ACPI: PCI Interrupt Link [LNKC] (IRQs *9)
[   30.184772] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[   30.185042] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.185123] pnp: PnP ACPI init
[   30.185140] ACPI: bus type pnp registered
[   30.192734] pnp: PnP ACPI: found 11 devices
[   30.192740] ACPI: ACPI bus type pnp unregistered
[   30.192748] PnPBIOS: Disabled by ACPI PNP
[   30.193341] PCI: Using ACPI for IRQ routing
[   30.193348] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.207875] NET: Registered protocol family 8
[   30.207881] NET: Registered protocol family 20
[   30.208057] AppArmor: AppArmor Filesystem Enabled
[   30.211832] Time: tsc clocksource has been installed.
[   30.219934] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[   30.219943] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[   30.219951] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
[   30.219958] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
[   30.219965] system 00:05: iomem range 0xfec00000-0xfec00fff has been reserved
[   30.219972] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
[   30.219980] system 00:05: iomem range 0xffc00000-0xffffffff could not be reserved
[   30.219993] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   30.220000] system 00:06: ioport range 0xfe10-0xfe11 has been reserved
[   30.220006] system 00:06: ioport range 0x600-0x60f has been reserved
[   30.220013] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   30.220020] system 00:06: ioport range 0x4000-0x407f has been reserved
[   30.220027] system 00:06: ioport range 0x8100-0x811f could not be reserved
[   30.251095] PCI: Bridge: 0000:00:01.0
[   30.251102]   IO window: 9000-9fff
[   30.251109]   MEM window: d0100000-d01fffff
[   30.251116]   PREFETCH window: d8000000-dfffffff
[   30.251123] PCI: Bus 2, cardbus bridge: 0000:00:07.0
[   30.251128]   IO window: 00002400-000024ff
[   30.251135]   IO window: 00002800-000028ff
[   30.251141]   PREFETCH window: 30000000-33ffffff
[   30.251148]   MEM window: 34000000-37ffffff
[   30.251175] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.251538] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   30.251546] PCI: setting IRQ 5 as level-triggered
[   30.251554] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   30.251567] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   30.251593] NET: Registered protocol family 2
[   30.288026] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   30.288591] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   30.288971] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   30.289326] TCP: Hash tables configured (established 16384 bind 16384)
[   30.289332] TCP reno registered
[   30.300106] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   31.006982]  it is
[   31.825348] Freeing initrd memory: 7325k freed
[   32.528589] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   32.530038] audit: initializing netlink socket (disabled)
[   32.530066] audit(1220047241.288:1): initialized
[   32.535604] VFS: Disk quotas dquot_6.5.1
[   32.535792] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.536104] io scheduler noop registered
[   32.536110] io scheduler anticipatory registered
[   32.536115] io scheduler deadline registered
[   32.536144] io scheduler cfq registered (default)
[   32.536167] PCI: VIA PCI bridge detected. Disabling DAC.
[   32.536254] Boot video device is 0000:01:00.0
[   32.536934] isapnp: Scanning for PnP cards...
[   32.891228] isapnp: No Plug & Play device found
[   32.965237] Real Time Clock Driver v1.12ac
[   32.965487] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.968352] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.968520] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   32.968753] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   32.997346] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.997359] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.011303] mice: PS/2 mouse device common for all mice
[   33.011599] EISA: Probing bus 0 at eisa.0
[   33.011612] Cannot allocate resource for EISA slot 1
[   33.011618] Cannot allocate resource for EISA slot 2
[   33.011631] Cannot allocate resource for EISA slot 4
[   33.011658] EISA: Detected 0 cards.
[   33.011665] cpuidle: using governor ladder
[   33.011669] cpuidle: using governor menu
[   33.011999] NET: Registered protocol family 1
[   33.012060] Using IPI No-Shortcut mode
[   33.012135] registered taskstats version 1
[   33.012344]   Magic number: 4:488:48
[   33.012709] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   33.012714] EDD information not available.
[   33.013483] Freeing unused kernel memory: 368k freed
[   33.079139] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   34.513148] fuse init (API version 7.9)
[   34.565263] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   34.574931] ACPI: Thermal Zone [THRM] (58 C)
[   35.326767] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   35.376772] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[d0004000-d00047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   35.767479] usbcore: registered new interface driver usbfs
[   35.767542] usbcore: registered new interface driver hub
[   35.795110] usbcore: registered new device driver usb
[   35.830554] USB Universal Host Controller Interface driver v3.0
[   35.831160] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 4
[   35.831168] PCI: setting IRQ 4 as level-triggered
[   35.831177] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
[   35.831190] PCI: VIA VLink IRQ fixup for 0000:00:10.0, from 0 to 4
[   35.831224] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   35.831699] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   35.831739] uhci_hcd 0000:00:10.0: irq 4, io base 0x00002000
[   35.832090] usb usb1: configuration #1 chosen from 1 choice
[   35.832153] hub 1-0:1.0: USB hub found
[   35.832168] hub 1-0:1.0: 2 ports detected
[   35.934797] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   35.934814] PCI: VIA VLink IRQ fixup for 0000:00:10.1, from 0 to 5
[   35.934848] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   35.934904] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   35.934941] uhci_hcd 0000:00:10.1: irq 5, io base 0x00002020
[   35.935223] usb usb2: configuration #1 chosen from 1 choice
[   35.935282] hub 2-0:1.0: USB hub found
[   35.935297] hub 2-0:1.0: 2 ports detected
[   36.039120] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   36.039131] PCI: setting IRQ 9 as level-triggered
[   36.039139] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   36.039153] PCI: VIA VLink IRQ fixup for 0000:00:10.2, from 0 to 9
[   36.039187] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   36.039255] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   36.039295] uhci_hcd 0000:00:10.2: irq 9, io base 0x00002040
[   36.039577] usb usb3: configuration #1 chosen from 1 choice
[   36.039656] hub 3-0:1.0: USB hub found
[   36.039671] hub 3-0:1.0: 2 ports detected
[   36.174499] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   36.283575] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   36.283586] PCI: setting IRQ 11 as level-triggered
[   36.283595] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   36.283608] PCI: VIA VLink IRQ fixup for 0000:00:10.3, from 0 to 11
[   36.283647] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   36.283717] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   36.283801] ehci_hcd 0000:00:10.3: irq 11, io mem 0xd0004c00
[   36.314344] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.314660] usb usb4: configuration #1 chosen from 1 choice
[   36.314724] hub 4-0:1.0: USB hub found
[   36.314741] hub 4-0:1.0: 6 ports detected
[   36.409077] SCSI subsystem initialized
[   36.572541] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   36.572663] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
[   36.577218] eth0: VIA Rhine II at 0xd0005000, 00:c0:9f:40:7a:ff, IRQ 4.
[   36.577938] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   36.585587] libata version 3.00 loaded.
[   36.602579] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
[   36.602597] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 0 to 4
[   36.602738] ACPI: PCI interrupt for device 0000:00:11.1 disabled
[   36.618728] pata_via 0000:00:11.1: version 0.3.3
[   36.618772] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
[   36.630313] scsi0 : pata_via
[   36.646300] scsi1 : pata_via
[   36.648000] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2060 irq 14
[   36.648009] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2068 irq 15
[   36.710265] usb 1-1: device not accepting address 2, error -71
[   36.788317] FDC 0 is a National Semiconductor PC87306
[   36.811487] ata1.00: ATA-6: ST94019A, 3.05, max UDMA/100
[   36.811497] ata1.00: 78140160 sectors, multi 16: LBA48 
[   36.828155] ata1.00: configured for UDMA/100
[   37.010506] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00001a7627]
[   37.302804] ata2.00: ATAPI: QSI     DVDRW SDW-042, DX70, max UDMA/33
[   37.474581] ata2.00: configured for UDMA/33
[   37.474852] scsi 0:0:0:0: Direct-Access     ATA      ST94019A         3.05 PQ: 0 ANSI: 5
[   37.477086] scsi 1:0:0:0: CD-ROM            QSI      DVDRW SDW-042    DX70 PQ: 0 ANSI: 5
[   37.859347] Driver 'sd' needs updating - please use bus_type methods
[   37.859540] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   37.859576] sd 0:0:0:0: [sda] Write Protect is off
[   37.859583] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.859635] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.859763] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   37.859794] sd 0:0:0:0: [sda] Write Protect is off
[   37.859801] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.859849] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.859858]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   38.013919] usb 4-4: new high speed USB device using ehci_hcd and address 4
[   38.088625]  sda1 sda2 < sda5 >
[   38.118443] sd 0:0:0:0: [sda] Attached SCSI disk
[   38.130495] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   38.130545] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   38.138268] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[   38.138281] Uniform CD-ROM driver Revision: 3.20
[   38.138403] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   38.285425] usb 4-4: configuration #1 chosen from 1 choice
[   38.525836] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   38.635430] Attempting manual resume
[   38.635439] swsusp: Resume From Partition 8:5
[   38.635443] PM: Checking swsusp image.
[   38.636621] PM: Resume from disk failed.
[   38.678405] EXT3-fs: INFO: recovery required on readonly filesystem.
[   38.678416] EXT3-fs: write access will be enabled during recovery.
[   38.795904] usb 1-1: configuration #1 chosen from 1 choice
[   39.041767] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   39.209987] usb 2-1: configuration #1 chosen from 1 choice
[   39.213001] usbcore: registered new interface driver hiddev
[   39.258521] input:   USB Keyboard as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/input/input2
[   39.269667] input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:10.0-1
[   39.328745] kjournald starting.  Commit interval 5 seconds
[   39.328777] EXT3-fs: sda1: orphan cleanup on readonly fs
[   39.328793] ext3_orphan_cleanup: deleting unreferenced inode 319966
[   39.328892] ext3_orphan_cleanup: deleting unreferenced inode 1114128
[   39.328923] EXT3-fs: sda1: 2 orphan inodes deleted
[   39.328927] EXT3-fs: recovery complete.
[   39.354390] EXT3-fs: mounted filesystem with ordered data mode.
[   39.358648] input:   USB Keyboard as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.1/input/input3
[   39.373750] input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:10.0-1
[   39.388197] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input4
[   39.401719] input,hidraw2: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:10.1-1
[   39.401763] usbcore: registered new interface driver usbhid
[   39.401773] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   53.314191] Linux agpgart interface v0.102
[   53.394243] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.458285] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.655052] Yenta: CardBus bridge found at 0000:00:07.0 [1025:0033]
[   53.655080] Yenta: Enabling burst memory read transactions
[   53.655088] Yenta: Using CSCINT to route CSC interrupts to PCI
[   53.655094] Yenta: Routing CardBus interrupts to PCI
[   53.655101] Yenta TI: socket 0000:00:07.0, mfunc 0x01201212, devctl 0x64
[   53.886257] Yenta: ISA IRQ mask 0x0088, PCI irq 5
[   53.886267] Socket status: 30000006
[   53.982350] agpgart: Detected VIA KM400/KM400A chipset
[   54.003074] agpgart: AGP aperture is 256M @ 0xe0000000
[   54.385944] irda_init()
[   54.385990] NET: Registered protocol family 23
[   55.489979] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   55.493604] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   55.565979] input: Power Button (FF) as /devices/virtual/input/input5
[   55.577616] ACPI: Power Button (FF) [PWRF]
[   55.577857] input: Power Button (CM) as /devices/virtual/input/input6
[   55.593575] ACPI: Power Button (CM) [PWRB]
[   55.593775] input: Sleep Button (CM) as /devices/virtual/input/input7
[   55.609573] ACPI: Sleep Button (CM) [SLPB]
[   55.609816] input: Lid Switch as /devices/virtual/input/input8
[   55.609960] ACPI: Lid Switch [LID]
[   55.641663] ACPI: AC Adapter [ACAD] (on-line)
[   55.766558] ACPI: Battery Slot [BAT1] (battery present)
[   56.461792] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   59.292271] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/LNXVIDEO:00/input/input10
[   59.308650] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   60.352836] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   60.352995] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   60.559219] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
[   60.594219] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   61.615060] parport_pc 00:09: reported by Plug and Play ACPI
[   61.615126] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   61.626037] ACPI: WMI-Acer: Mapper loaded
[   61.689253] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   61.689280] acer_acpi: No or unsupported WMI interface, unable to load.
[   62.142276] phy0: Selected rate control algorithm 'simple'
[   62.581383] usbcore: registered new interface driver rt73usb
[   62.616927] usbcore: registered new interface driver rt2500usb
[   64.547218] cs: IO port probe 0x100-0x3af: clean.
[   64.549424] cs: IO port probe 0x3e0-0x4ff: clean.
[   64.550381] cs: IO port probe 0x820-0x8ff: clean.
[   64.551187] cs: IO port probe 0xc00-0xcf7: clean.
[   64.552423] cs: IO port probe 0xa00-0xaff: clean.
[   67.054439] lp0: using parport0 (interrupt-driven).
[   67.186094] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   67.790320] EXT3 FS on sda1, internal journal
[   69.559764] ip_tables: (C) 2000-2006 Netfilter Core Team
[   70.346908] No dock devices found.
[   71.103781] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   71.106092] powernow: No PST tables match this cpuid (0x7a0)
[   71.106097] powernow: This is indicative of a broken BIOS.
[   71.106102] powernow: Trying ACPI perflib
[   71.106183] powernow: Minimum speed 796 MHz. Maximum speed 2189 MHz.
[   25.821637] Marking TSC unstable due to: cpufreq changes.
[   25.825076] Time: acpi_pm clocksource has been installed.
[   25.946880] Clocksource tsc unstable (delta = 219530263 ns)
[   26.856804] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   26.856812] apm: overridden by ACPI.
[   27.025381] ppdev: user-space parallel port driver
[   27.289893] audit(1220047281.964:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4864 profile="/usr/sbin/cupsd" namespace="default"
[   42.623299] eth0: link down
[   42.813792] Bluetooth: Core ver 2.11
[   42.818804] NET: Registered protocol family 31
[   42.818813] Bluetooth: HCI device and connection manager initialized
[   42.818819] Bluetooth: HCI socket layer initialized
[   42.875524] Bluetooth: L2CAP ver 2.9
[   42.875532] Bluetooth: L2CAP socket layer initialized
[   42.973338] Bluetooth: RFCOMM socket layer initialized
[   42.973366] Bluetooth: RFCOMM TTY layer initialized
[   42.973369] Bluetooth: RFCOMM ver 1.8
[   29.849721] [drm] Initialized drm 1.1.0 20060810
[   29.869156] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
[   29.869530] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   84.056797] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   84.057406] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   84.057860] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   85.396295] [drm] Setting GART location based on new memory map
[   85.396318] [drm] Loading R200 Microcode
[   85.396404] [drm] writeback test succeeded in 1 usecs
[   62.910822] NET: Registered protocol family 10
[   62.911142] lo: Disabled Privacy Extensions
[   62.911536] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.911953] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  112.277742] NET: Registered protocol family 17
[  310.682436] wlan0: Initial auth_alg=0
[  310.682451] wlan0: authenticate with AP 00:13:d4:6b:33:c6
[  310.684222] wlan0: RX authentication from 00:13:d4:6b:33:c6 (alg=0 transaction=2 status=0)
[  310.684232] wlan0: authenticated
[  310.684239] wlan0: associate with AP 00:13:d4:6b:33:c6
[  310.686584] wlan0: RX AssocResp from 00:13:d4:6b:33:c6 (capab=0x411 status=0 aid=3)
[  310.686594] wlan0: associated
[  310.687642] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  113.055641] padlock: VIA PadLock not detected.
[  328.515826] wlan0: no IPv6 routers present
[  487.761227] wlan0: switched to short barker preamble (BSSID=00:13:d4:6b:33:c6)
**[ 2071.120204] usb 4-4: USB disconnect, address 4**
[ 2071.132134] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[ 2071.132154] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[ 2071.132165] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 2071.132175] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[ 2071.132184] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[ 2071.132193] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[  752.310975] usb 4-4: new high speed USB device using ehci_hcd and address 5
[ 2089.026146] usb 4-4: new high speed USB device using ehci_hcd and address 6
[ 2112.488936] usb 4-4: new high speed USB device using ehci_hcd and address 7
[ 2128.240720] usb 4-4: new high speed USB device using ehci_hcd and address 8

```

---

### Post by Bliepo32 on 2008-08-30
Allright, I have read through the ouput of dmesg, and at one part it says "[ 2071.120204] usb 4-4: USB disconnect, address 4". But I didn't disconnect it at all! I think this is the problem, but how do I fix it?

---

### Post by nuddernuby on 2008-08-30
Glad to hear that I'm not the only one with this problem - will be watching this thread with interest.
Am running 2 USB wireless cards on 2 desktops, both with Hardy. One is a Ralink (under Canyon brand) and the other a Zydas WLA-54L.  Same problem: after some time they just get disconnected - while I'm on the net.  The only solution so far was to reconfigure the Wi-fi card and to reconnect to the ISP.  Needless to say, this is an untenable situation.

BTW, where is the basic configuration file for a wireless card?

---

### Post by Bliepo32 on 2008-08-31
> **nuddernuby said:**
> 
BTW, where is the basic configuration file for a wireless card?

It is located at /etc/network/interfaces

---

### Post by nuddernuby on 2008-08-31
Thanks, Bliepo32!

---

### Post by Bliepo32 on 2008-09-02
* bump *
I have been waiting for 4 days now, and not even one solution has been suggested. I will do almost anything to get it working, but I need to know how.

---

### Post by ugm6hr on 2008-09-02
I'm afraid I'm nor sure what's up, but I suspect it is an issue with the driver.

Is this relevant? [http://www.willdaniels.co.uk/articles/10-howto/15-rtl8180-hardy](http://www.willdaniels.co.uk/articles/10-howto/15-rtl8180-hardy)

---

### Post by Bliepo32 on 2008-09-05
Although the reply above has been the most usefull until now, it still didn't help me to solve my problem.

Please, I need to fix this. I know that many people here are trying to help, and that they do not have time for every thread, but I really need to fix this.

---

### Post by Bliepo32 on 2008-09-06
* bump *

Please, if you have **any** idea at all, please reply. If I have things I can try, I at least have the idea I am working towards a soultion. Now, I am just waiting, and it gives me the idea that I will never get it working... which is a horibble thought.

---

### Post by Bliepo32 on 2008-09-08
It seems that I have found the root of the problem. My wireless got disconnected again, and I immmediately opend syslog. This is what I found (shortened version):

> 
Sep  7 09:20:04 roy-laptop kernel: [ 1005.080997] **usb 4-2: USB disconnect, address 2**

Sep  7 09:20:04 roy-laptop kernel: [ 1005.102203] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19. <--- This one stood there 16 times

Sep  7 09:20:04 roy-laptop kernel: [  365.182206] usb 4-2: new high speed USB device using ehci_hcd and address 4


So how can this happen, and how do I fix it? Or is it maybe the USB device itself which is malfunctioning?

---

### Post by nuddernuby on 2008-09-08
Keep going, Bliepo32.  I would be most interested to see if we could find a solution to this.  
I recently saw something that made me wonder it could have a bearing on this problem. It was a howto on networks, where it was stated that a keep-alive signal (every 120 seconds in that case) should be built into the process to ensure that the connection does not time out and disconnect.  Do you think that this could be the case here?

---

### Post by Bliepo32 on 2008-09-09
I do not think that is the problem in my case. I made a little shellscript that pinged my router once every second, and wrote the time and the results of the ping to a file. It still went down however. But because it showed exactly when ping stopped working, I knew exactly where to look in the syslog.

If you want, I could make a script for you that does the same.

---

