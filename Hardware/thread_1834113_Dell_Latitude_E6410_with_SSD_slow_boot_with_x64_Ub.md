---
title: "Dell Latitude E6410 with SSD slow boot with x64 Ubuntu 11.04"
date: 2011-08-27
forum: Hardware
---

### Post by b0ngokarl on 2011-08-27
Hi,

I hope I don't get my butt kicked because I repost this in a diffrent categorie.

My Laptop is a Dell Latitude E6410 and I have some performance problems with it.

Please see here:[http://ubuntuforums.org/showthread.php?t=1833241](http://ubuntuforums.org/showthread.php?t=1833241)

Did a couple of reinstalls already but this didn't solve it.

I know the SSD is SATA 6G but I bought it for future computers :)

Thanks!

Jonas

---

### Post by b0ngokarl on 2011-08-27
Maybe this is worth to mention?


/dev/sda1:
 Timing cached reads:   6726 MB in  2.00 seconds = 3363.54 MB/sec
 Timing buffered disk reads: 788 MB in  3.01 seconds = 261.94 MB/sec

I uploaded bootchart.png - I don't get it :(

Also another question please - what is happening from 0-3.5 and from 7-15 and 19-30? 

```

[    3.403626] libata version 3.00 loaded.
[    3.403665] usbcore: registered new interface driver usbfs
[    3.403672] usbcore: registered new interface driver hub
[    3.403692] usbcore: registered new device driver usb
[    3.403843] wmi: Mapper loaded
[    3.403845] PCI: Using ACPI for IRQ routing
[    3.403847] PCI: pci_cache_line_size set to 64 bytes
[    3.403937] reserve RAM buffer: 0000000000095c00 - 000000000009ffff 
[    3.403939] reserve RAM buffer: 00000000db25f000 - 00000000dbffffff 
[    3.404014] NetLabel: Initializing
[    3.404016] NetLabel:  domain hash size = 128
[    3.404017] NetLabel:  protocols = UNLABELED CIPSOv4
[    3.404026] NetLabel:  unlabeled traffic allowed by default
[    3.404060] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    3.404065] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    3.406081] Switching to clocksource hpet
[    3.410874] AppArmor: AppArmor Filesystem Enabled
[    3.410903] pnp: PnP ACPI init
[    3.410921] ACPI: bus type pnp registered
[    3.411244] pnp 00:00: [bus 00-3e]
[    3.411247] pnp 00:00: [io  0x0000-0x0cf7 window]
[    3.411248] pnp 00:00: [io  0x0cf8-0x0cff]
[    3.411249] pnp 00:00: [io  0x0d00-0xffff window]
[    3.411252] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    3.411254] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    3.411255] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    3.411257] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    3.411258] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    3.411259] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    3.411261] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    3.411262] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    3.411264] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    3.411265] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    3.411266] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    3.411268] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    3.411269] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    3.411270] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    3.411272] pnp 00:00: [mem 0xe0000000-0xfeafffff window]
[    3.411273] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    3.411353] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    3.411375] pnp 00:01: [io  0x0000-0x001f]
[    3.411377] pnp 00:01: [io  0x0081-0x0091]
[    3.411378] pnp 00:01: [io  0x0093-0x009f]
[    3.411379] pnp 00:01: [io  0x00c0-0x00df]
[    3.411381] pnp 00:01: [dma 4]
[    3.411398] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    3.411406] pnp 00:02: [mem 0xff000000-0xffffffff]
[    3.411425] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    3.411487] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    3.411506] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    3.411514] pnp 00:04: [io  0x00f0]
[    3.411525] pnp 00:04: [irq 13]
[    3.411545] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    3.411553] pnp 00:05: [io  0x002e-0x002f]
[    3.411554] pnp 00:05: [io  0x004e-0x004f]
[    3.411555] pnp 00:05: [io  0x0061]
[    3.411556] pnp 00:05: [io  0x0063]
[    3.411558] pnp 00:05: [io  0x0065]
[    3.411559] pnp 00:05: [io  0x0067]
[    3.411560] pnp 00:05: [io  0x0070]
[    3.411561] pnp 00:05: [io  0x0080]
[    3.411562] pnp 00:05: [io  0x0092]
[    3.411563] pnp 00:05: [io  0x00b2-0x00b3]
[    3.411564] pnp 00:05: [io  0x0680-0x069f]
[    3.411565] pnp 00:05: [io  0x1000-0x1003]
[    3.411567] pnp 00:05: [io  0x1004-0x1013]
[    3.411568] pnp 00:05: [io  0xffff]
[    3.411569] pnp 00:05: [io  0x0400-0x047f]
[    3.411570] pnp 00:05: [io  0x0500-0x057f]
[    3.411571] pnp 00:05: [io  0x164e-0x164f]
[    3.411626] system 00:05: [io  0x0680-0x069f] has been reserved
[    3.411628] system 00:05: [io  0x1000-0x1003] has been reserved
[    3.411630] system 00:05: [io  0x1004-0x1013] has been reserved
[    3.411631] system 00:05: [io  0xffff] has been reserved
[    3.411633] system 00:05: [io  0x0400-0x047f] has been reserved
[    3.411635] system 00:05: [io  0x0500-0x057f] has been reserved
[    3.411636] system 00:05: [io  0x164e-0x164f] has been reserved
[    3.411639] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.411646] pnp 00:06: [io  0x0070-0x0077]
[    3.411651] pnp 00:06: [irq 8]
[    3.411671] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.411678] pnp 00:07: [io  0x0060]
[    3.411679] pnp 00:07: [io  0x0064]
[    3.411684] pnp 00:07: [irq 1]
[    3.411702] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    3.411729] pnp 00:08: [mem 0xfed40000-0xfed44fff]
[    3.411751] pnp 00:08: Plug and Play ACPI device, IDs BCM0102 PNP0c31 (active)
[    3.414846] Switched to NOHz mode on CPU #0
[    3.414950] Switched to NOHz mode on CPU #1
[    3.414974] Switched to NOHz mode on CPU #2
[    3.414977] Switched to NOHz mode on CPU #3
[    3.417481] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (disabled)
[    3.417493] pnp 00:0a: [irq 12]
[    3.417516] pnp 00:0a: Plug and Play ACPI device, IDs DLL040a PNP0f13 (active)
[    3.417716] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    3.417718] pnp 00:0b: [mem 0xfed10000-0xfed13fff]
[    3.417720] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    3.417721] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    3.417722] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    3.417723] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    3.417725] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    3.417726] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    3.417727] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    3.417729] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    3.417730] pnp 00:0b: [mem 0xf69c0000-0xf69c0fff]
[    3.417775] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    3.417777] system 00:0b: [mem 0xfed10000-0xfed13fff] has been reserved
[    3.417779] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    3.417781] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    3.417782] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    3.417784] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    3.417786] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    3.417788] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    3.417789] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
[    3.417791] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    3.417793] system 00:0b: [mem 0xf69c0000-0xf69c0fff] has been reserved
[    3.417795] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.417854] pnp 00:0c: [irq 23]
[    3.417885] pnp 00:0c: Plug and Play ACPI device, IDs SMO8800 (active)
[    3.418998] pnp 00:0d: [bus 3f]
[    3.419038] pnp 00:0d: Plug and Play ACPI device, IDs PNP0a03 (active)
[    3.420172] pnp: PnP ACPI: found 14 devices
[    3.420174] ACPI: ACPI bus type pnp unregistered
[    3.425918] pci 0000:00:1c.2: BAR 15: can't assign mem pref (size 0x4000000)
[    3.425922] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf6a00000-0xf6bfffff 64bit pref]
[    3.425926] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf6c00000-0xf6dfffff 64bit pref]
[    3.425929] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf6e00000-0xf6ffffff 64bit pref]
[    3.425931] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    3.425934] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    3.425939] pci 0000:00:1c.0:   bridge window [mem 0xf5500000-0xf68fffff]
[    3.425944] pci 0000:00:1c.0:   bridge window [mem 0xf6a00000-0xf6bfffff 64bit pref]
[    3.425951] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    3.425954] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    3.425959] pci 0000:00:1c.1:   bridge window [mem 0xf4100000-0xf54fffff]
[    3.425964] pci 0000:00:1c.1:   bridge window [mem 0xf6c00000-0xf6dfffff 64bit pref]
[    3.425973] pci 0000:03:00.0: BAR 15: can't assign mem pref (size 0x4000000)
[    3.425974] pci 0000:03:00.0: BAR 16: can't assign mem (size 0x4000000)
[    3.425976] pci 0000:03:00.0: BAR 13: assigned [io  0x2000-0x20ff]
[    3.425978] pci 0000:03:00.0: BAR 14: assigned [io  0x2400-0x24ff]
[    3.425979] pci 0000:03:00.0: CardBus bridge to [bus 04-07]
[    3.425981] pci 0000:03:00.0:   bridge window [io  0x2000-0x20ff]
[    3.425987] pci 0000:03:00.0:   bridge window [io  0x2400-0x24ff]
[    3.425992] pci 0000:00:1c.2: PCI bridge to [bus 03-04]
[    3.425995] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
[    3.426001] pci 0000:00:1c.2:   bridge window [mem 0xf0400000-0xf2cfffff]
[    3.426005] pci 0000:00:1c.2:   bridge window [mem pref disabled]
[    3.426012] pci 0000:00:1c.3: PCI bridge to [bus 05-0a]
[    3.426015] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    3.426020] pci 0000:00:1c.3:   bridge window [mem 0xf2d00000-0xf40fffff]
[    3.426025] pci 0000:00:1c.3:   bridge window [mem 0xf6e00000-0xf6ffffff 64bit pref]
[    3.426032] pci 0000:00:1e.0: PCI bridge to [bus 0b-0b]
[    3.426033] pci 0000:00:1e.0:   bridge window [io  disabled]
[    3.426038] pci 0000:00:1e.0:   bridge window [mem disabled]
[    3.426070] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    3.426090] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.426094] pci 0000:00:1c.0: setting latency timer to 64
[    3.426105] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.426109] pci 0000:00:1c.1: setting latency timer to 64
[    3.426118] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.426122] pci 0000:00:1c.2: setting latency timer to 64
[    3.426132] pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.426138] pci 0000:03:00.0: setting latency timer to 64
[    3.426148] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.426152] pci 0000:00:1c.3: setting latency timer to 64
[    3.426160] pci 0000:00:1e.0: setting latency timer to 64
[    3.426164] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    3.426166] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    3.426167] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    3.426169] pci_bus 0000:00: resource 7 [mem 0xe0000000-0xfeafffff]
[    3.426170] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    3.426172] pci_bus 0000:01: resource 1 [mem 0xf5500000-0xf68fffff]
[    3.426173] pci_bus 0000:01: resource 2 [mem 0xf6a00000-0xf6bfffff 64bit pref]
[    3.426175] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    3.426176] pci_bus 0000:02: resource 1 [mem 0xf4100000-0xf54fffff]
[    3.426178] pci_bus 0000:02: resource 2 [mem 0xf6c00000-0xf6dfffff 64bit pref]
[    3.426179] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
[    3.426181] pci_bus 0000:03: resource 1 [mem 0xf0400000-0xf2cfffff]
[    3.426183] pci_bus 0000:04: resource 0 [io  0x2000-0x20ff]
[    3.426184] pci_bus 0000:04: resource 1 [io  0x2400-0x24ff]
[    3.426186] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    3.426187] pci_bus 0000:05: resource 1 [mem 0xf2d00000-0xf40fffff]
[    3.426188] pci_bus 0000:05: resource 2 [mem 0xf6e00000-0xf6ffffff 64bit pref]
[    3.426190] pci_bus 0000:0b: resource 4 [io  0x0000-0x0cf7]
[    3.426192] pci_bus 0000:0b: resource 5 [io  0x0d00-0xffff]
[    3.426193] pci_bus 0000:0b: resource 6 [mem 0x000a0000-0x000bffff]
[    3.426195] pci_bus 0000:0b: resource 7 [mem 0xe0000000-0xfeafffff]
[    3.426221] NET: Registered protocol family 2
[    3.426403] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    3.427341] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    3.428984] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.429178] TCP: Hash tables configured (established 524288 bind 65536)
[    3.429180] TCP reno registered
[    3.429192] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    3.429226] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    3.429344] NET: Registered protocol family 1
[    3.429358] pci 0000:00:02.0: Boot video device
[    3.429487] PCI: CLS 64 bytes, default 64
[    3.429492] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.429494] Placing 64MB software IO TLB between ffff8800d7000000 - ffff8800db000000
[    3.429496] software IO TLB at phys 0xd7000000 - 0xdb000000
[    3.429528] Simple Boot Flag at 0xf1 set to 0x1
[    3.429907] audit: initializing netlink socket (disabled)
[    3.429915] type=2000 audit(1314439951.300:1): initialized
[    3.440913] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.442209] VFS: Disk quotas dquot_6.5.2
[    3.442250] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.442716] fuse init (API version 7.16)
[    3.442781] msgmni has been set to 15586
[    3.442976] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.442998] io scheduler noop registered
[    3.443000] io scheduler deadline registered
[    3.443033] io scheduler cfq registered (default)
[    3.443332] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.443349] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.443381] intel_idle: MWAIT substates: 0x1120
[    3.443383] intel_idle: v0.4 model 0x25
[    3.443384] intel_idle: lapic_timer_reliable_states 0xffffffff
[    3.443773] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    3.444086] ACPI: AC Adapter [AC] (off-line)
[    3.444186] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    3.655505] ACPI: Lid Switch [LID]
[    3.655585] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    3.745327] ACPI: Power Button [PBTN]
[    3.745383] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    3.745386] ACPI: Sleep Button [SBTN]
[    3.745412] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    3.745414] ACPI: Power Button [PWRF]
[    3.745571] ACPI: acpi_idle yielding to intel_idle
[    3.750553] ERST: Table is not found!
[    3.750625] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.761497] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    3.761501] ACPI: Battery Slot [BAT0] (battery present)
[    4.154611] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.154618] ACPI: Battery Slot [BAT1] (battery absent)
[    4.165687] serial 0000:00:16.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.186162] 0000:00:16.3: ttyS4 at I/O 0x70a0 (irq = 19) is a 16550A
[    4.186371] Linux agpgart interface v0.103
[    4.186436] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    4.186514] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    4.187008] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    4.187150] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    4.187941] brd: module loaded
[    4.188292] loop: module loaded
[    4.188365] i2c-core: driver [adp5520] using legacy suspend method
[    4.188366] i2c-core: driver [adp5520] using legacy resume method
[    4.188653] Fixed MDIO Bus: probed
[    4.188672] PPP generic driver version 2.4.2
[    4.188699] tun: Universal TUN/TAP device driver, 1.6
[    4.188701] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.188757] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.188776] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.188796] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.188800] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    4.188831] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.188898] ehci_hcd 0000:00:1a.0: debug port 2
[    4.192765] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    4.192783] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf6970000
[    4.214134] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    4.214276] hub 1-0:1.0: USB hub found
[    4.214281] hub 1-0:1.0: 3 ports detected
[    4.214340] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.214351] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.214354] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    4.214383] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.214430] ehci_hcd 0000:00:1d.0: debug port 2
[    4.218305] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    4.218318] ehci_hcd 0000:00:1d.0: irq 17, io mem 0xf6950000
[    4.234086] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    4.234205] hub 2-0:1.0: USB hub found
[    4.234208] hub 2-0:1.0: 3 ports detected
[    4.234256] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.234264] uhci_hcd: USB Universal Host Controller Interface driver
[    4.234339] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.234547] i8042: Warning: Keylock active
[    4.235795] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.235801] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.235883] mousedev: PS/2 mouse device common for all mice
[    4.236014] rtc_cmos 00:06: RTC can wake from S4
[    4.236095] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    4.236123] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    4.236197] device-mapper: uevent: version 1.0.3
[    4.236260] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    4.236330] device-mapper: multipath: version 1.2.0 loaded
[    4.236334] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.236516] cpuidle: using governor ladder
[    4.236627] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.236813] cpuidle: using governor menu
[    4.236990] TCP cubic registered
[    4.237076] NET: Registered protocol family 10
[    4.237445] NET: Registered protocol family 17
[    4.237456] Registering the dns_resolver key type
[    4.239061] PM: Hibernation image not present or could not be loaded.
[    4.239072] registered taskstats version 1
[    4.239499]   Magic number: 7:269:225
[    4.239663] rtc_cmos 00:06: setting system clock to 2011-08-27 10:12:32 UTC (1314439952)
[    4.239666] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.239667] EDD information not available.
[    4.241654] Freeing unused kernel memory: 956k freed
[    4.241809] Write protecting the kernel read-only data: 10240k
[    4.244125] Freeing unused kernel memory: 184k freed
[    4.249189] Freeing unused kernel memory: 1440k freed
[    4.281474] <30>udev[88]: starting version 167
[    4.309355] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    4.309359] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    4.309414] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.309428] e1000e 0000:00:19.0: setting latency timer to 64
[    4.309571] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    4.329395] [drm] Initialized drm 1.1.0 20060810
[    4.340036] sdhci: Secure Digital Host Controller Interface driver
[    4.340040] sdhci: Copyright(c) Pierre Ossman
[    4.342946] sdhci-pci 0000:03:00.1: SDHCI controller found [1180:e822] (rev 3)
[    4.342968] sdhci-pci 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.343009] sdhci-pci 0000:03:00.1: setting latency timer to 64
[    4.343036] mmc0: no vmmc regulator found
[    4.343077] Registered led device: mmc0::
[    4.343142] mmc0: SDHCI controller on PCI [0000:03:00.1] using DMA
[    4.378200] firewire_ohci 0000:03:00.4: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    4.378209] firewire_ohci 0000:03:00.4: setting latency timer to 64
[    4.423737] Refined TSC clocksource calibration: 2660.153 MHz.
[    4.423747] Switching to clocksource tsc
[    4.463778] firewire_ohci 0000:03:00.4: irq 41 for MSI/MSI-X
[    4.463824] firewire_ohci: Added fw-ohci device 0000:03:00.4, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x1
[    4.543395] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.560179] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 5c:26:0a:15:86:3f
[    4.560181] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.560232] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 10, PBA No: 3041FF-0FF
[    4.560250] ahci 0000:00:1f.2: version 3.0
[    4.560266] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.560396] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    4.560485] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl RAID mode
[    4.560489] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems sxs apst 
[    4.560494] ahci 0000:00:1f.2: setting latency timer to 64
[    4.613769] scsi0 : ahci
[    4.613893] scsi1 : ahci
[    4.613993] scsi2 : ahci
[    4.614097] scsi3 : ahci
[    4.614241] scsi4 : ahci
[    4.614376] scsi5 : ahci
[    4.614774] ata1: SATA max UDMA/133 abar m2048@0xf6940000 port 0xf6940100 irq 42
[    4.614778] ata2: SATA max UDMA/133 abar m2048@0xf6940000 port 0xf6940180 irq 42
[    4.614780] ata3: DUMMY
[    4.614780] ata4: DUMMY
[    4.614783] ata5: SATA max UDMA/133 abar m2048@0xf6940000 port 0xf6940300 irq 42
[    4.614786] ata6: SATA max UDMA/133 abar m2048@0xf6940000 port 0xf6940380 irq 42
[    4.614840] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.614843] i915 0000:00:02.0: setting latency timer to 64
[    4.656961] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[    4.656964] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    4.657248] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    4.657252] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.657253] [drm] Driver supports precise vblank timestamp query.
[    4.680407] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    4.693729] hub 1-1:1.0: USB hub found
[    4.693931] hub 1-1:1.0: 6 ports detected
[    4.812737] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    4.962373] ata6: SATA link down (SStatus 0 SControl 300)
[    4.962410] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.962445] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.962478] ata5: SATA link down (SStatus 0 SControl 300)
[    4.962482] firewire_core: created device fw0: GUID 07ee7a81444fc000, S400
[    4.963195] hub 2-1:1.0: USB hub found
[    4.963409] hub 2-1:1.0: 8 ports detected
[    4.973975] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-U633J, D100, max UDMA/100
[    4.986561] ata2.00: configured for UDMA/100
[    5.052336] usb 1-1.4: new high speed USB device using ehci_hcd and address 3
[    5.073665] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    5.097569] ata1.00: ATA-9: OCZ-VERTEX3 MI, 2.02, max UDMA/133
[    5.097573] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.226198] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    5.241904] usb 2-1.7: new full speed USB device using ehci_hcd and address 3
[    5.249282] ata1.00: configured for UDMA/133
[    5.249460] scsi 0:0:0:0: Direct-Access     ATA      OCZ-VERTEX3 MI   2.02 PQ: 0 ANSI: 5
[    5.249688] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.249789] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    5.249937] sd 0:0:0:0: [sda] Write Protect is off
[    5.249942] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.249982] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.250636]  sda: sda1 sda2 < sda5 >
[    5.251042] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.251948] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-U633J D100 PQ: 0 ANSI: 5
[    5.258960] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.258965] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.259119] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.259177] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.431399] usb 2-1.8: new full speed USB device using ehci_hcd and address 4
[    5.564457] usb 2-1.8: config 0 descriptor??
[    5.855837] fbcon: inteldrmfb (fb0) is primary device
[    5.855898] Console: switching to colour frame buffer device 180x56
[    5.855930] fb0: inteldrmfb frame buffer device
[    5.855931] drm: registered panic notifier
[    8.483840] acpi device:3d: registered as cooling_device4
[    8.643721] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[    8.643778] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    8.643937] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.230215] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.528998] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.579267] <30>udev[415]: starting version 167
[   15.622535] lp: driver loaded but no devices found
[   15.664297] type=1400 audit(1314432763.939:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=531 comm="apparmor_parser"
[   15.664907] type=1400 audit(1314432763.939:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=531 comm="apparmor_parser"
[   15.665315] type=1400 audit(1314432763.939:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=531 comm="apparmor_parser"
[   15.668411] parport_pc 00:09: [io  0x0378-0x037b]
[   15.668444] parport_pc 00:09: [io  0x0278-0x027b]
[   15.668483] parport_pc 00:09: [io  0x03bc-0x03bf]
[   15.668519] parport_pc 00:09: [io  0x0378-0x037b]
[   15.668589] parport_pc 00:09: [irq 7]
[   15.713968] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   15.713983] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   15.715603] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   15.724226] yenta_cardbus 0000:03:00.0: CardBus bridge found [1028:040a]
[   15.724259] yenta_cardbus 0000:03:00.0: CardBus bridge to [bus 04-07]
[   15.724262] yenta_cardbus 0000:03:00.0:   bridge window [io  0x2000-0x20ff]
[   15.724269] yenta_cardbus 0000:03:00.0:   bridge window [io  0x2400-0x24ff]
[   15.724276] yenta_cardbus 0000:03:00.0:   bridge window [mem 0xf0400000-0xf17fffff pref]
[   15.724282] yenta_cardbus 0000:03:00.0:   bridge window [mem 0xf1800000-0xf1bfffff]
[   15.737474] cfg80211: Calling CRDA to update world regulatory domain
[   15.856496] yenta_cardbus 0000:03:00.0: ISA IRQ mask 0x0000, PCI irq 18
[   15.856501] yenta_cardbus 0000:03:00.0: Socket status: 30000006
[   15.856504] pci_bus 0000:04: Upper limit for fixing this bridge's parent bridge: #04
[   15.856510] yenta_cardbus 0000:03:00.0: pcmcia: parent PCI bridge window: [io  0x2000-0x3fff]
[   15.856513] yenta_cardbus 0000:03:00.0: pcmcia: parent PCI bridge window: [mem 0xf0400000-0xf2cfffff]
[   15.856515] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf0400000-0xf2cfffff: excluding 0xf0400000-0xf1d9ffff 0xf2a70000-0xf2cfffff
[   15.914599] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.923433] type=1400 audit(1314432764.199:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=843 comm="apparmor_parser"
[   15.924038] type=1400 audit(1314432764.199:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=843 comm="apparmor_parser"
[   15.924454] type=1400 audit(1314432764.199:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=843 comm="apparmor_parser"
[   15.925615] type=1400 audit(1314432764.209:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=842 comm="apparmor_parser"
[   15.928268] type=1400 audit(1314432764.209:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=848 comm="apparmor_parser"
[   15.935739] type=1400 audit(1314432764.219:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=846 comm="apparmor_parser"
[   15.936486] type=1400 audit(1314432764.219:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=846 comm="apparmor_parser"
[   15.938198] ppdev: user-space parallel port driver
[   15.939880] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   15.939922] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   15.939962] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   15.955183] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   15.980208] cfg80211: World regulatory domain updated:
[   15.980212] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.980215] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.980218] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.980220] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.980222] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.980224] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.999879] Bluetooth: Core ver 2.15
[   15.999917] NET: Registered protocol family 31
[   15.999919] Bluetooth: HCI device and connection manager initialized
[   15.999922] Bluetooth: HCI socket layer initialized
[   16.038006] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   16.038272] usbcore: registered new interface driver btusb
[   16.085361] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   16.145083] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   16.145782] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.180151] Linux video capture interface: v2.00
[   16.193016] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_3M (05ca:1814)
[   16.194615] input: Laptop_Integrated_Webcam_3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7
[   16.194772] usbcore: registered new interface driver uvcvideo
[   16.194774] USB Video Class driver (v1.0.0)
[   16.209492] parport_pc 00:09: activated
[   16.209499] parport_pc 00:09: reported by Plug and Play ACPI
[   16.209620] parport_pc 00:09: disabled
[   16.210465] tpm_tis 00:08: 1.2 TPM (device-id 0x2001, rev-id 32)
[   16.228029] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.228033] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   16.228176] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.228185] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.228229] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   16.230139] Bluetooth: L2CAP ver 2.15
[   16.230142] Bluetooth: L2CAP socket layer initialized
[   16.244563] iwlagn 0000:02:00.0: device EEPROM VER=0x43a, CALIB=0x6
[   16.244567] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   16.245273] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.245360] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
[   16.254020] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.254023] Bluetooth: BNEP filters: protocol multicast
[   16.289954] alps.c: Enabled hardware quirk, falling back to psmouse-core
[   16.302417] input: ImPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   16.402747] iwlagn 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   16.403046] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   16.407400] Bluetooth: SCO (Voice Link) ver 0.6
[   16.407404] Bluetooth: SCO socket layer initialized
[   16.426312] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.453372] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.453436] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.453462] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.460806] Bluetooth: RFCOMM TTY layer initialized
[   16.460812] Bluetooth: RFCOMM socket layer initialized
[   16.460814] Bluetooth: RFCOMM ver 1.11
[   16.513636] vboxdrv: Found 4 processor cores.
[   16.513952] vboxdrv: fAsync=0 offMin=0x1f4 offMax=0xa8f
[   16.514638] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.514640] vboxdrv: Successfully loaded version 4.0.12 (interface 0x00180000).
[   16.575269] input: HDA Intel Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.575354] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.575424] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.575497] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.735851] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.915138] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   17.923536] padlock_aes: VIA PadLock not detected.
[   17.927497] padlock_sha: VIA PadLock Hash Engine not detected.
[   18.037918] Adding 8175612k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:8175612k 
[   19.856745] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   30.530324] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[   35.844529] wlan0: authenticate with 00:1f:3f:d7:50:b7 (try 1)
[   36.036295] wlan0: authenticate with 00:1f:3f:d7:50:b7 (try 2)
[   36.039375] wlan0: authenticated
[   36.039816] wlan0: associate with 00:1f:3f:d7:50:b7 (try 1)
[   36.043593] wlan0: RX AssocResp from 00:1f:3f:d7:50:b7 (capab=0x431 status=0 aid=2)
[   36.043597] wlan0: associated
[   36.047715] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.534206] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 2
[   56.231536] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = 00:1f:3f:d7:50:b7 tid = 0

```



Thanks!

Jonas

---

