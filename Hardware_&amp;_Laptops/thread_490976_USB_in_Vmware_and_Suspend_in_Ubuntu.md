---
title: "USB in Vmware and Suspend in Ubuntu"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by shick on 2007-07-03
I'm relatively new to Linux.   I'm currently running Feisty on a Toshiba Satellite laptop.  I'm experiencing two main problems:

1) I don't know if anyone is experiencing this, but I'm having trouble with the suspend option.  When I press suspend, it give me a message saying that the machine failed to suspend.  Someone told me that this has to do with kernel.  How would I go about updating a kernel or just rectifying this problem?

2) Also, I just installed Windows on vmware, and I'm having trouble getting Windows to recognize my usb/ flash drive.  Though I get a tab saying something about a sandisk mini cruzer, when I press the tab, wait and then go to "My Computer" on the desktop, hoping to see the USB, there's nothing.  I have the "C  Drive," a CD-DVD player, but nothing about a flash drive.  I hope all of this makes sense. 

Does anyone know what I should do about these problems.  Thanks.

---

### Post by scxtt on 2007-07-03
do you have a USB device added to your VM?  and are you connecting it to the running VM, so it has a little checkmark next to it? -- not sure what you're saying w/ the "tab" lingo ... are you using VMware server?

---

### Post by shick on 2007-07-04
Yeah I definitely have a USB device added to my VM, but I'm not using VMware server.  

When I boot up VM little tabs pop up like one for the cd drive, the ethernet, and for the sound card.  When I plug in the Flashdrive, a little Sandisk Mini Cruzer tab is at the top. I press the tab, but bor some reason, the machine doesn't seem to recognize or read the flashdrive.  

Any ideas?

---

### Post by scxtt on 2007-07-04
are you using player? (not that it should matter too much); but i forget how it handles "enabling" a plugged in device ... i'm also wondering if the usb flash drive is formatted *strangely* and the host is having trouble w/ it ... after it's plugged in, cause ubuntu read it fine?  what's the output of **sudo fdisk -l** and **dmesg**?

---

### Post by shick on 2007-07-05
Here's the output for sudo fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9528    76533628+  83  Linux
/dev/sda2            9529        9716     1510110    5  Extended
/dev/sda5            9529        9716     1510078+  82  Linux swap / Solaris
:
And here's what it says for sudo dmesg:

[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000004000 end: 00000000000d4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fe60000 end: 000000005ff60000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000005ff60000 size: 000000000000a000 end: 000000005ff6a000 type: 3
[    0.000000] copy_e820_map() start: 000000005ff6a000 size: 0000000000001000 end: 000000005ff6b000 type: 2
[    0.000000] copy_e820_map() start: 000000005ff6b000 size: 0000000000005000 end: 000000005ff70000 type: 4
[    0.000000] copy_e820_map() start: 000000005ff70000 size: 0000000000090000 end: 0000000060000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff60000 (usable)
[    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff6a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ff6a000 - 000000005ff6b000 (reserved)
[    0.000000]  BIOS-e820: 000000005ff6b000 - 000000005ff70000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005ff70000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 393056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393056
[    0.000000] On node 0 totalpages: 393056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1278 pages used for memmap
[    0.000000]   HighMem zone: 162402 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f8350
[    0.000000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 MASM 0x06110000) @ 0x5ff64a40
[    0.000000] ACPI: FADT (v002 TOSHIB 750      0x20030101 MASM 0x61100000) @ 0x5ff69d03
[    0.000000] ACPI: SSDT (v001 TOSHIB A0019    0x00970814 MSFT 0x0100000e) @ 0x5ff69d87
[    0.000000] ACPI: DBGP (v001 TOSHIB 750      0x00970814 MASM 0x61100000) @ 0x5ff69fa4
[    0.000000] ACPI: BOOT (v001 TOSHIB 750      0x00970814 MASM 0x06110000) @ 0x5ff69fd8
[    0.000000] ACPI: DSDT (v001 TOSHIB A0019    0x20040521 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9fb80000)
[    0.000000] Detected 1695.788 MHz processor.
[   10.198583] Built 1 zonelists.  Total pages: 389986
[   10.198587] Kernel command line: root=UUID=c5e3e4ba-d321-43f4-bd3f-2f3f804fd540 ro quiet splash
[   10.198752] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   10.198762] mapped APIC to ffffd000 (01c0f000)
[   10.198766] Enabling fast FPU save and restore... done.
[   10.198768] Enabling unmasked SIMD FPU exception support... done.
[   10.198779] Initializing CPU#0
[   10.198848] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   10.201051] Console: colour VGA+ 80x25
[   10.201656] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.202253] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.273478] Memory: 1547468k/1572224k available (1992k kernel code, 23564k reserved, 900k data, 328k init, 654720k highmem)
[   10.273490] virtual kernel memory layout:
[   10.273491]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   10.273492]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.273494]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.273495]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.273496]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   10.273498]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   10.273499]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   10.273502] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.350644] Calibrating delay using timer specific routine.. 3393.84 BogoMIPS (lpj=6787680)
[   10.350696] Security Framework v1.0.0 initialized
[   10.350710] SELinux:  Disabled at boot.
[   10.350729] Mount-cache hash table entries: 512
[   10.350918] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[   10.350932] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.350935] CPU: L2 cache: 2048K
[   10.350939] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[   10.350953] Compat vDSO mapped to ffffe000.
[   10.350960] Remapping vsyscall page to ffffe000
[   10.350974] Checking 'hlt' instruction... OK.
[   10.366795] SMP alternatives: switching to UP code
[   10.367139] Freeing SMP alternatives: 11k freed
[   10.367370] Early unpacking initramfs... done
[   10.700853] ACPI: Core revision 20060707
[   10.701078] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   10.704194] ACPI: setting ELCR to 0200 (from 0c98)
[   10.704335] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[   10.704341] SMP motherboard not detected.
[   10.704343] Local APIC not detected. Using dummy APIC emulation.
[   10.704378] Brought up 1 CPUs
[   10.704617] Booting paravirtualized kernel on bare hardware
[   10.704678] Time: 22:36:18  Date: 06/01/107
[   10.704706] NET: Registered protocol family 16
[   10.704787] EISA bus registered
[   10.704791] ACPI: bus type pci registered
[   10.704855] PCI: PCI BIOS revision 2.10 entry at 0xfd981, last bus=4
[   10.704858] PCI: Using configuration type 1
[   10.704859] Setting up standard PCI resources
[   10.707932] ACPI: Interpreter enabled
[   10.707935] ACPI: Using PIC for interrupt routing
[   10.708312] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 11)
[   10.708545] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 11)
[   10.708781] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *7 11)
[   10.709012] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *11)
[   10.709243] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 7 11)
[   10.709474] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *11)
[   10.709707] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[   10.709937] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 7 11)
[   10.710133] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.710138] PCI: Probing PCI hardware (bus 00)
[   10.710518] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   10.711070] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   10.711074] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   10.711268] Boot video device is 0000:01:00.0
[   10.711438] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   10.711566] PCI: Transparent bridge - 0000:00:1e.0
[   10.711618] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[   10.711621] Please report the result to linux-kernel to fix this permanently
[   10.711639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.712991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   10.713820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   10.715981] ACPI: Power Resource [PFAN] (off)
[   10.716058] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.716066] pnp: PnP ACPI init
[   10.717577] pnp: PnP ACPI: found 9 devices
[   10.717581] PnPBIOS: Disabled by ACPI PNP
[   10.717623] PCI: Using ACPI for IRQ routing
[   10.717626] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.725369] NET: Registered protocol family 8
[   10.725371] NET: Registered protocol family 20
[   10.725975] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
[   10.726033] PCI: Bridge: 0000:00:01.0
[   10.726034]   IO window: disabled.
[   10.726038]   MEM window: c1000000-c1ffffff
[   10.726041]   PREFETCH window: e0000000-efffffff
[   10.726050] PCI: Bus 3, cardbus bridge: 0000:02:0b.0
[   10.726052]   IO window: 00003400-000034ff
[   10.726056]   IO window: 00003800-000038ff
[   10.726061]   PREFETCH window: 70000000-73ffffff
[   10.726065]   MEM window: 78000000-7bffffff
[   10.726069] PCI: Bridge: 0000:00:1e.0
[   10.726072]   IO window: 3000-3fff
[   10.726077]   MEM window: c2000000-c20fffff
[   10.726081]   PREFETCH window: 70000000-73ffffff
[   10.726096] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.726109] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
[   10.726299] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[   10.726301] PCI: setting IRQ 3 as level-triggered
[   10.726305] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   10.726312] PCI: Setting latency timer of device 0000:02:0b.0 to 64
[   10.726332] NET: Registered protocol family 2
[   10.754146] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.754261] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.755206] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.755872] TCP: Hash tables configured (established 131072 bind 65536)
[   10.755876] TCP reno registered
[   10.766231] checking if image is initramfs... it is
[   11.417346] Freeing initrd memory: 6762k freed
[   11.417603] Simple Boot Flag at 0x36 set to 0x1
[   11.417791] audit: initializing netlink socket (disabled)
[   11.417807] audit(1183329378.404:1): initialized
[   11.417885] highmem bounce pool size: 64 pages
[   11.417954] VFS: Disk quotas dquot_6.5.1
[   11.417976] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.418029] io scheduler noop registered
[   11.418032] io scheduler anticipatory registered
[   11.418035] io scheduler deadline registered
[   11.418044] io scheduler cfq registered (default)
[   11.418340] isapnp: Scanning for PnP cards...
[   11.770693] isapnp: No Plug & Play device found
[   11.794277] Real Time Clock Driver v1.12ac
[   11.794334] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.795153] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[   11.795157] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   11.795167] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   11.795240] mice: PS/2 mouse device common for all mice
[   11.795741] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.795890] input: Macintosh mouse button emulation as /class/input/input0
[   11.795922] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.795926] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.796104] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.800026] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.800030] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.800128] EISA: Probing bus 0 at eisa.0
[   11.800134] Cannot allocate resource for EISA slot 1
[   11.800137] Cannot allocate resource for EISA slot 2
[   11.800139] Cannot allocate resource for EISA slot 3
[   11.800154] EISA: Detected 0 cards.
[   11.830212] TCP cubic registered
[   11.830221] NET: Registered protocol family 1
[   11.830242] Using IPI No-Shortcut mode
[   11.830316] ACPI: (supports S0 S3 S4 S5)
[   11.830357]   Magic number: 15:993:652
[   11.830714] Freeing unused kernel memory: 328k freed
[   11.832611] Time: tsc clocksource has been installed.
[   11.840207] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.044537] Capability LSM initialized
[   13.076007] ACPI: Transitioning device [FAN] to D3
[   13.076010] ACPI: Transitioning device [FAN] to D3
[   13.076013] ACPI: Fan [FAN] (off)
[   13.079767] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.080619] ACPI: Thermal Zone [THRM] (40 C)
[   13.412042] usbcore: registered new interface driver usbfs
[   13.412071] usbcore: registered new interface driver hub
[   13.412090] usbcore: registered new device driver usb
[   13.413011] USB Universal Host Controller Interface driver v3.0
[   13.413059] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   13.413070] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.413074] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.413217] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.413241] uhci_hcd 0000:00:1d.0: irq 3, io base 0x00001800
[   13.413342] usb usb1: configuration #1 chosen from 1 choice
[   13.413364] hub 1-0:1.0: USB hub found
[   13.413369] hub 1-0:1.0: 2 ports detected
[   13.478437] SCSI subsystem initialized
[   13.483518] libata version 2.20 loaded.
[   13.507786] ieee1394: Initialized config rom entry `ip1394'
[   13.514674] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   13.514679] PCI: setting IRQ 11 as level-triggered
[   13.514683] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.514694] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.514698] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.514721] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.514745] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[   13.514830] usb usb2: configuration #1 chosen from 1 choice
[   13.514854] hub 2-0:1.0: USB hub found
[   13.514860] hub 2-0:1.0: 2 ports detected
[   13.519236] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   13.519239] e100: Copyright(c) 1999-2006 Intel Corporation
[   13.618548] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 7
[   13.618553] PCI: setting IRQ 7 as level-triggered
[   13.618557] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[   13.618569] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.618573] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.618596] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.618622] uhci_hcd 0000:00:1d.2: irq 7, io base 0x00001840
[   13.618717] usb usb3: configuration #1 chosen from 1 choice
[   13.618744] hub 3-0:1.0: USB hub found
[   13.618750] hub 3-0:1.0: 2 ports detected
[    3.488000] Time: acpi_pm clocksource has been installed.
[    3.528000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 4
[    3.528000] PCI: setting IRQ 4 as level-triggered
[    3.528000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 4 (level, low) -> IRQ 4
[    3.528000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.528000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.528000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.528000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.528000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.528000] ehci_hcd 0000:00:1d.7: irq 4, io mem 0xc0000000
[    3.532000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.532000] usb usb4: configuration #1 chosen from 1 choice
[    3.532000] hub 4-0:1.0: USB hub found
[    3.532000] hub 4-0:1.0: 6 ports detected
[    3.636000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.636000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.636000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[    3.636000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.636000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    3.636000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    3.636000] scsi0 : ata_piix
[    3.800000] ata1.00: ata_hpa_resize 1: sectors = 156087541, hpa_sectors = 156301488
[    3.800000] ata1.00: Host Protected Area detected.
[    3.800000]      current size : 156087541 sectors (79916 MB)
[    3.800000]      native  size : 156301488 sectors (80026 MB)
[    3.808000] ata1.00: Native size increased to 156301488 sectors
[    3.808000] ata1.00: ATA-6: TOSHIBA MK8025GAS, KA024A, max UDMA/100
[    3.808000] ata1.00: 156301488 sectors, multi 16: LBA 
[    3.816000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.816000] ata1.00: configured for UDMA/100
[    3.816000] scsi1 : ata_piix
[    4.292000] ata2.00: ATAPI, max UDMA/33
[    4.456000] ata2.00: configured for UDMA/33
[    4.456000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8025GA KA02 PQ: 0 ANSI: 5
[    4.456000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-820S  1.00 PQ: 0 ANSI: 5
[    4.460000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    4.460000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[    4.512000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c2006000-c20067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.512000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 3
[    4.512000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[    4.536000] e100: eth0: e100_probe: addr 0xc2005000, irq 3, MAC addr 00:0E:7B:91:35:02
[    4.552000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.552000] sda: Write Protect is off
[    4.552000] sda: Mode Sense: 00 3a 00 00
[    4.552000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.552000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.552000] sda: Write Protect is off
[    4.552000] sda: Mode Sense: 00 3a 00 00
[    4.552000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.552000]  sda: sda1 sda2 < sda5 >
[    4.640000] sd 0:0:0:0: Attached scsi disk sda
[    4.644000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.644000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.652000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.652000] Uniform CD-ROM driver Revision: 3.20
[    4.652000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.888000] Attempting manual resume
[    4.888000] swsusp: Resume From Partition 8:5
[    4.888000] PM: Checking swsusp image.
[    4.888000] PM: Resume from disk failed.
[    4.936000] kjournald starting.  Commit interval 5 seconds
[    4.936000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.784000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000511279]
[   20.968000] iTCO_vendor_support: vendor-support=0
[   20.968000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.968000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.968000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.016000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.020000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.040000] intel_rng: FWH not detected
[   21.508000] NET: Registered protocol family 17
[   21.664000] input: PC Speaker as /class/input/input2
[   21.712000] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[   21.784000] ieee80211_crypt: registered algorithm 'NULL'
[   21.804000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.840000] Yenta: ISA IRQ mask 0x0420, PCI irq 3
[   21.840000] Socket status: 30000007
[   21.840000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   21.840000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   21.840000] cs: IO port probe 0x3000-0x3fff: clean.
[   21.840000] pcmcia: parent PCI bridge Memory window: 0xc2000000 - 0xc20fffff
[   21.840000] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x73ffffff
[   21.884000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.884000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.976000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   21.976000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.976000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   21.976000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   22.008000] nvidia: module license 'NVIDIA' taints kernel.
[   22.496000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   22.496000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   22.496000] PCI: setting IRQ 10 as level-triggered
[   22.496000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   22.496000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   22.564000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb1, caps: 0x804713/0x0
[   22.564000] synaptics: Toshiba Satellite M35 detected, limiting rate to 40pps.
[   22.608000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[   22.612000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.612000] cs: IO port probe 0x820-0x8ff: clean.
[   22.612000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.612000] cs: IO port probe 0xa00-0xaff: clean.
[   22.636000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   22.928000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   22.928000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   23.748000] intel8x0_measure_ac97_clock: measured 55489 usecs
[   23.748000] intel8x0: clocking to 48000
[   23.944000] fuse init (API version 7.8)
[   23.996000] lp: driver loaded but no devices found
[   24.036000] Adding 1510068k swap on /dev/disk/by-uuid/138b6ac5-10f0-4c7d-b1e3-c6a81befd04c.  Priority:-1 extents:1 across:1510068k
[   24.204000] EXT3 FS on sda1, internal journal
[   28.644000] input: Power Button (FF) as /class/input/input4
[   28.648000] ACPI: Power Button (FF) [PWRF]
[   28.680000] input: Lid Switch as /class/input/input5
[   28.684000] ACPI: Lid Switch [LID]
[   28.720000] input: Power Button (CM) as /class/input/input6
[   28.720000] ACPI: Power Button (CM) [PWRB]
[   28.788000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   28.788000] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   28.792000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   28.792000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   28.812000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   28.824000] ACPI: Battery Slot [BAT1] (battery present)
[   28.832000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   28.860000] ACPI: AC Adapter [ADP1] (off-line)
[   28.872000] No dock devices found.
[   28.884000] Using specific hotkey driver
[   32.968000] ppdev: user-space parallel port driver
[   38.588000] apm: BIOS not found.
[   40.256000] /dev/vmmon[4795]: VMCI: Driver initialized.
[   40.260000] /dev/vmmon[4795]: Module vmmon: registered with major=10 minor=165
[   40.260000] /dev/vmmon[4795]: Module vmmon: initialized
[   41.260000] Bluetooth: Core ver 2.11
[   41.260000] NET: Registered protocol family 31
[   41.260000] Bluetooth: HCI device and connection manager initialized
[   41.260000] Bluetooth: HCI socket layer initialized
[   41.280000] Bluetooth: L2CAP ver 2.8
[   41.280000] Bluetooth: L2CAP socket layer initialized
[   41.404000] Bluetooth: RFCOMM socket layer initialized
[   41.404000] Bluetooth: RFCOMM TTY layer initialized
[   41.404000] Bluetooth: RFCOMM ver 1.8
[   58.296000] NET: Registered protocol family 10
[   58.300000] lo: Disabled Privacy Extensions
[   58.300000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.584000] eth1: no IPv6 routers present
[   73.968000] ieee80211_crypt: registered algorithm 'WEP'
[   89.512000] eth1: no IPv6 routers present
[ 4293.860000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 4294.036000] usb 1-1: configuration #1 chosen from 1 choice
[ 4294.336000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04E8 pid 0x3238
[ 4294.336000] usbcore: registered new interface driver usblp
[ 4294.336000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[ 4334.952000] usb 1-1: USB disconnect, address 2
[ 4334.952000] drivers/usb/class/usblp.c: usblp0: removed
[18105.956000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[18105.960000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[18106.976000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[18123.048000] eth0: no IPv6 routers present
[18191.064000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[18243.956000] e100: eth0: e100_watchdog: link down
[18245.140000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[18260.288000] eth1: no IPv6 routers present
[21238.884000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[21240.380000] ipw2200: Firmware error detected.  Restarting.
[43487.176000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[43487.196000] ipw2200: Firmware error detected.  Restarting.
[44209.660000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[44211.180000] ipw2200: Firmware error detected.  Restarting.
[49126.788000] ipw2200: Firmware error detected.  Restarting.
[49149.520000] ipw2200: Firmware error detected.  Restarting.
[139189.956000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[139189.960000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[139190.984000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[139193.616000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[139211.048000] eth0: no IPv6 routers present
[139297.956000] e100: eth0: e100_watchdog: link down
[139299.188000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[139321.216000] eth1: no IPv6 routers present
[197583.580000] ipw2200: Firmware error detected.  Restarting.
[200523.592000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[200523.816000] ipw2200: Firmware error detected.  Restarting.
[210986.796000] ipw2200: Firmware error detected.  Restarting.


I'm relatively new to all this, so what does this all mean?  And how do I correct it? I hope I'm not screwed.  Thanks for your help.

---

### Post by scxtt on 2007-07-05
those should have been run after you insert the USB disk, plug it in - then run them :)

---

### Post by shick on 2007-07-06
Okay. Gotcha.  

Here's what it says now for fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9528    76533628+  83  Linux
/dev/sda2            9529        9716     1510110    5  Extended
/dev/sda5            9529        9716     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992      999813+   6  FAT16


And here's what it says for dmesg:

[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff60000 (usable)
[    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff6a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ff6a000 - 000000005ff6b000 (reserved)
[    0.000000]  BIOS-e820: 000000005ff6b000 - 000000005ff70000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005ff70000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 393056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393056
[    0.000000] On node 0 totalpages: 393056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1278 pages used for memmap
[    0.000000]   HighMem zone: 162402 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f8350
[    0.000000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 MASM 0x06110000) @ 0x5ff64a40
[    0.000000] ACPI: FADT (v002 TOSHIB 750      0x20030101 MASM 0x61100000) @ 0x5ff69d03
[    0.000000] ACPI: SSDT (v001 TOSHIB A0019    0x00970814 MSFT 0x0100000e) @ 0x5ff69d87
[    0.000000] ACPI: DBGP (v001 TOSHIB 750      0x00970814 MASM 0x61100000) @ 0x5ff69fa4
[    0.000000] ACPI: BOOT (v001 TOSHIB 750      0x00970814 MASM 0x06110000) @ 0x5ff69fd8
[    0.000000] ACPI: DSDT (v001 TOSHIB A0019    0x20040521 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9fb80000)
[    0.000000] Detected 1695.788 MHz processor.
[   10.198583] Built 1 zonelists.  Total pages: 389986
[   10.198587] Kernel command line: root=UUID=c5e3e4ba-d321-43f4-bd3f-2f3f804fd540 ro quiet splash
[   10.198752] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   10.198762] mapped APIC to ffffd000 (01c0f000)
[   10.198766] Enabling fast FPU save and restore... done.
[   10.198768] Enabling unmasked SIMD FPU exception support... done.
[   10.198779] Initializing CPU#0
[   10.198848] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   10.201051] Console: colour VGA+ 80x25
[   10.201656] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.202253] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.273478] Memory: 1547468k/1572224k available (1992k kernel code, 23564k reserved, 900k data, 328k init, 654720k highmem)
[   10.273490] virtual kernel memory layout:
[   10.273491]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   10.273492]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.273494]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.273495]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.273496]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   10.273498]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   10.273499]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   10.273502] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.350644] Calibrating delay using timer specific routine.. 3393.84 BogoMIPS (lpj=6787680)
[   10.350696] Security Framework v1.0.0 initialized
[   10.350710] SELinux:  Disabled at boot.
[   10.350729] Mount-cache hash table entries: 512
[   10.350918] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[   10.350932] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.350935] CPU: L2 cache: 2048K
[   10.350939] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[   10.350953] Compat vDSO mapped to ffffe000.
[   10.350960] Remapping vsyscall page to ffffe000
[   10.350974] Checking 'hlt' instruction... OK.
[   10.366795] SMP alternatives: switching to UP code
[   10.367139] Freeing SMP alternatives: 11k freed
[   10.367370] Early unpacking initramfs... done
[   10.700853] ACPI: Core revision 20060707
[   10.701078] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   10.704194] ACPI: setting ELCR to 0200 (from 0c98)
[   10.704335] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[   10.704341] SMP motherboard not detected.
[   10.704343] Local APIC not detected. Using dummy APIC emulation.
[   10.704378] Brought up 1 CPUs
[   10.704617] Booting paravirtualized kernel on bare hardware
[   10.704678] Time: 22:36:18  Date: 06/01/107
[   10.704706] NET: Registered protocol family 16
[   10.704787] EISA bus registered
[   10.704791] ACPI: bus type pci registered
[   10.704855] PCI: PCI BIOS revision 2.10 entry at 0xfd981, last bus=4
[   10.704858] PCI: Using configuration type 1
[   10.704859] Setting up standard PCI resources
[   10.707932] ACPI: Interpreter enabled
[   10.707935] ACPI: Using PIC for interrupt routing
[   10.708312] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 11)
[   10.708545] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 11)
[   10.708781] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *7 11)
[   10.709012] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *11)
[   10.709243] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 7 11)
[   10.709474] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *11)
[   10.709707] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[   10.709937] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 7 11)
[   10.710133] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.710138] PCI: Probing PCI hardware (bus 00)
[   10.710518] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   10.711070] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   10.711074] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   10.711268] Boot video device is 0000:01:00.0
[   10.711438] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   10.711566] PCI: Transparent bridge - 0000:00:1e.0
[   10.711618] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[   10.711621] Please report the result to linux-kernel to fix this permanently
[   10.711639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.712991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   10.713820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   10.715981] ACPI: Power Resource [PFAN] (off)
[   10.716058] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.716066] pnp: PnP ACPI init
[   10.717577] pnp: PnP ACPI: found 9 devices
[   10.717581] PnPBIOS: Disabled by ACPI PNP
[   10.717623] PCI: Using ACPI for IRQ routing
[   10.717626] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.725369] NET: Registered protocol family 8
[   10.725371] NET: Registered protocol family 20
[   10.725975] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
[   10.726033] PCI: Bridge: 0000:00:01.0
[   10.726034]   IO window: disabled.
[   10.726038]   MEM window: c1000000-c1ffffff
[   10.726041]   PREFETCH window: e0000000-efffffff
[   10.726050] PCI: Bus 3, cardbus bridge: 0000:02:0b.0
[   10.726052]   IO window: 00003400-000034ff
[   10.726056]   IO window: 00003800-000038ff
[   10.726061]   PREFETCH window: 70000000-73ffffff
[   10.726065]   MEM window: 78000000-7bffffff
[   10.726069] PCI: Bridge: 0000:00:1e.0
[   10.726072]   IO window: 3000-3fff
[   10.726077]   MEM window: c2000000-c20fffff
[   10.726081]   PREFETCH window: 70000000-73ffffff
[   10.726096] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.726109] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
[   10.726299] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[   10.726301] PCI: setting IRQ 3 as level-triggered
[   10.726305] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   10.726312] PCI: Setting latency timer of device 0000:02:0b.0 to 64
[   10.726332] NET: Registered protocol family 2
[   10.754146] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.754261] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.755206] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.755872] TCP: Hash tables configured (established 131072 bind 65536)
[   10.755876] TCP reno registered
[   10.766231] checking if image is initramfs... it is
[   11.417346] Freeing initrd memory: 6762k freed
[   11.417603] Simple Boot Flag at 0x36 set to 0x1
[   11.417791] audit: initializing netlink socket (disabled)
[   11.417807] audit(1183329378.404:1): initialized
[   11.417885] highmem bounce pool size: 64 pages
[   11.417954] VFS: Disk quotas dquot_6.5.1
[   11.417976] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.418029] io scheduler noop registered
[   11.418032] io scheduler anticipatory registered
[   11.418035] io scheduler deadline registered
[   11.418044] io scheduler cfq registered (default)
[   11.418340] isapnp: Scanning for PnP cards...
[   11.770693] isapnp: No Plug & Play device found
[   11.794277] Real Time Clock Driver v1.12ac
[   11.794334] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.795153] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[   11.795157] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   11.795167] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   11.795240] mice: PS/2 mouse device common for all mice
[   11.795741] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.795890] input: Macintosh mouse button emulation as /class/input/input0
[   11.795922] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.795926] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.796104] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.800026] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.800030] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.800128] EISA: Probing bus 0 at eisa.0
[   11.800134] Cannot allocate resource for EISA slot 1
[   11.800137] Cannot allocate resource for EISA slot 2
[   11.800139] Cannot allocate resource for EISA slot 3
[   11.800154] EISA: Detected 0 cards.
[   11.830212] TCP cubic registered
[   11.830221] NET: Registered protocol family 1
[   11.830242] Using IPI No-Shortcut mode
[   11.830316] ACPI: (supports S0 S3 S4 S5)
[   11.830357]   Magic number: 15:993:652
[   11.830714] Freeing unused kernel memory: 328k freed
[   11.832611] Time: tsc clocksource has been installed.
[   11.840207] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.044537] Capability LSM initialized
[   13.076007] ACPI: Transitioning device [FAN] to D3
[   13.076010] ACPI: Transitioning device [FAN] to D3
[   13.076013] ACPI: Fan [FAN] (off)
[   13.079767] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.080619] ACPI: Thermal Zone [THRM] (40 C)
[   13.412042] usbcore: registered new interface driver usbfs
[   13.412071] usbcore: registered new interface driver hub
[   13.412090] usbcore: registered new device driver usb
[   13.413011] USB Universal Host Controller Interface driver v3.0
[   13.413059] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   13.413070] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.413074] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.413217] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.413241] uhci_hcd 0000:00:1d.0: irq 3, io base 0x00001800
[   13.413342] usb usb1: configuration #1 chosen from 1 choice
[   13.413364] hub 1-0:1.0: USB hub found
[   13.413369] hub 1-0:1.0: 2 ports detected
[   13.478437] SCSI subsystem initialized
[   13.483518] libata version 2.20 loaded.
[   13.507786] ieee1394: Initialized config rom entry `ip1394'
[   13.514674] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   13.514679] PCI: setting IRQ 11 as level-triggered
[   13.514683] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.514694] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.514698] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.514721] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.514745] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[   13.514830] usb usb2: configuration #1 chosen from 1 choice
[   13.514854] hub 2-0:1.0: USB hub found
[   13.514860] hub 2-0:1.0: 2 ports detected
[   13.519236] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   13.519239] e100: Copyright(c) 1999-2006 Intel Corporation
[   13.618548] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 7
[   13.618553] PCI: setting IRQ 7 as level-triggered
[   13.618557] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[   13.618569] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.618573] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.618596] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.618622] uhci_hcd 0000:00:1d.2: irq 7, io base 0x00001840
[   13.618717] usb usb3: configuration #1 chosen from 1 choice
[   13.618744] hub 3-0:1.0: USB hub found
[   13.618750] hub 3-0:1.0: 2 ports detected
[    3.488000] Time: acpi_pm clocksource has been installed.
[    3.528000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 4
[    3.528000] PCI: setting IRQ 4 as level-triggered
[    3.528000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 4 (level, low) -> IRQ 4
[    3.528000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.528000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.528000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.528000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.528000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.528000] ehci_hcd 0000:00:1d.7: irq 4, io mem 0xc0000000
[    3.532000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.532000] usb usb4: configuration #1 chosen from 1 choice
[    3.532000] hub 4-0:1.0: USB hub found
[    3.532000] hub 4-0:1.0: 6 ports detected
[    3.636000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.636000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.636000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[    3.636000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.636000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    3.636000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    3.636000] scsi0 : ata_piix
[    3.800000] ata1.00: ata_hpa_resize 1: sectors = 156087541, hpa_sectors = 156301488
[    3.800000] ata1.00: Host Protected Area detected.
[    3.800000]      current size : 156087541 sectors (79916 MB)
[    3.800000]      native  size : 156301488 sectors (80026 MB)
[    3.808000] ata1.00: Native size increased to 156301488 sectors
[    3.808000] ata1.00: ATA-6: TOSHIBA MK8025GAS, KA024A, max UDMA/100
[    3.808000] ata1.00: 156301488 sectors, multi 16: LBA 
[    3.816000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.816000] ata1.00: configured for UDMA/100
[    3.816000] scsi1 : ata_piix
[    4.292000] ata2.00: ATAPI, max UDMA/33
[    4.456000] ata2.00: configured for UDMA/33
[    4.456000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8025GA KA02 PQ: 0 ANSI: 5
[    4.456000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-820S  1.00 PQ: 0 ANSI: 5
[    4.460000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    4.460000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[    4.512000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c2006000-c20067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.512000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 3
[    4.512000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 3 (level, low) -> IRQ 3
[    4.536000] e100: eth0: e100_probe: addr 0xc2005000, irq 3, MAC addr 00:0E:7B:91:35:02
[    4.552000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.552000] sda: Write Protect is off
[    4.552000] sda: Mode Sense: 00 3a 00 00
[    4.552000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.552000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.552000] sda: Write Protect is off
[    4.552000] sda: Mode Sense: 00 3a 00 00
[    4.552000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.552000]  sda: sda1 sda2 < sda5 >
[    4.640000] sd 0:0:0:0: Attached scsi disk sda
[    4.644000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.644000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.652000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.652000] Uniform CD-ROM driver Revision: 3.20
[    4.652000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.888000] Attempting manual resume
[    4.888000] swsusp: Resume From Partition 8:5
[    4.888000] PM: Checking swsusp image.
[    4.888000] PM: Resume from disk failed.
[    4.936000] kjournald starting.  Commit interval 5 seconds
[    4.936000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.784000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000511279]
[   20.968000] iTCO_vendor_support: vendor-support=0
[   20.968000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.968000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.968000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.016000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.020000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.040000] intel_rng: FWH not detected
[   21.508000] NET: Registered protocol family 17
[   21.664000] input: PC Speaker as /class/input/input2
[   21.712000] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[   21.784000] ieee80211_crypt: registered algorithm 'NULL'
[   21.804000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.840000] Yenta: ISA IRQ mask 0x0420, PCI irq 3
[   21.840000] Socket status: 30000007
[   21.840000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   21.840000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   21.840000] cs: IO port probe 0x3000-0x3fff: clean.
[   21.840000] pcmcia: parent PCI bridge Memory window: 0xc2000000 - 0xc20fffff
[   21.840000] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x73ffffff
[   21.884000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.884000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.976000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   21.976000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.976000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   21.976000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   22.008000] nvidia: module license 'NVIDIA' taints kernel.
[   22.496000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   22.496000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   22.496000] PCI: setting IRQ 10 as level-triggered
[   22.496000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   22.496000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   22.564000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb1, caps: 0x804713/0x0
[   22.564000] synaptics: Toshiba Satellite M35 detected, limiting rate to 40pps.
[   22.608000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[   22.612000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.612000] cs: IO port probe 0x820-0x8ff: clean.
[   22.612000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.612000] cs: IO port probe 0xa00-0xaff: clean.
[   22.636000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   22.928000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   22.928000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   23.748000] intel8x0_measure_ac97_clock: measured 55489 usecs
[   23.748000] intel8x0: clocking to 48000
[   23.944000] fuse init (API version 7.8)
[   23.996000] lp: driver loaded but no devices found
[   24.036000] Adding 1510068k swap on /dev/disk/by-uuid/138b6ac5-10f0-4c7d-b1e3-c6a81befd04c.  Priority:-1 extents:1 across:1510068k
[   24.204000] EXT3 FS on sda1, internal journal
[   28.644000] input: Power Button (FF) as /class/input/input4
[   28.648000] ACPI: Power Button (FF) [PWRF]
[   28.680000] input: Lid Switch as /class/input/input5
[   28.684000] ACPI: Lid Switch [LID]
[   28.720000] input: Power Button (CM) as /class/input/input6
[   28.720000] ACPI: Power Button (CM) [PWRB]
[   28.788000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   28.788000] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   28.792000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   28.792000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   28.812000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   28.824000] ACPI: Battery Slot [BAT1] (battery present)
[   28.832000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   28.860000] ACPI: AC Adapter [ADP1] (off-line)
[   28.872000] No dock devices found.
[   28.884000] Using specific hotkey driver
[   32.968000] ppdev: user-space parallel port driver
[   38.588000] apm: BIOS not found.
[   40.256000] /dev/vmmon[4795]: VMCI: Driver initialized.
[   40.260000] /dev/vmmon[4795]: Module vmmon: registered with major=10 minor=165
[   40.260000] /dev/vmmon[4795]: Module vmmon: initialized
[   41.260000] Bluetooth: Core ver 2.11
[   41.260000] NET: Registered protocol family 31
[   41.260000] Bluetooth: HCI device and connection manager initialized
[   41.260000] Bluetooth: HCI socket layer initialized
[   41.280000] Bluetooth: L2CAP ver 2.8
[   41.280000] Bluetooth: L2CAP socket layer initialized
[   41.404000] Bluetooth: RFCOMM socket layer initialized
[   41.404000] Bluetooth: RFCOMM TTY layer initialized
[   41.404000] Bluetooth: RFCOMM ver 1.8
[   58.296000] NET: Registered protocol family 10
[   58.300000] lo: Disabled Privacy Extensions
[   58.300000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.584000] eth1: no IPv6 routers present
[   73.968000] ieee80211_crypt: registered algorithm 'WEP'
[   89.512000] eth1: no IPv6 routers present
[ 4293.860000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 4294.036000] usb 1-1: configuration #1 chosen from 1 choice
[ 4294.336000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04E8 pid 0x3238
[ 4294.336000] usbcore: registered new interface driver usblp
[ 4294.336000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[ 4334.952000] usb 1-1: USB disconnect, address 2
[ 4334.952000] drivers/usb/class/usblp.c: usblp0: removed
[18105.956000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[18105.960000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[18106.976000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[18123.048000] eth0: no IPv6 routers present
[18191.064000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[18243.956000] e100: eth0: e100_watchdog: link down
[18245.140000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[18260.288000] eth1: no IPv6 routers present
[21238.884000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[21240.380000] ipw2200: Firmware error detected.  Restarting.
[43487.176000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[43487.196000] ipw2200: Firmware error detected.  Restarting.
[44209.660000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[44211.180000] ipw2200: Firmware error detected.  Restarting.
[49126.788000] ipw2200: Firmware error detected.  Restarting.
[49149.520000] ipw2200: Firmware error detected.  Restarting.
[139189.956000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[139189.960000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[139190.984000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[139193.616000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[139211.048000] eth0: no IPv6 routers present
[139297.956000] e100: eth0: e100_watchdog: link down
[139299.188000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[139321.216000] eth1: no IPv6 routers present
[197583.580000] ipw2200: Firmware error detected.  Restarting.
[200523.592000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[200523.816000] ipw2200: Firmware error detected.  Restarting.
[210986.796000] ipw2200: Firmware error detected.  Restarting.
[364554.796000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[364556.280000] ipw2200: Firmware error detected.  Restarting.
[374535.592000] usb 4-2: new high speed USB device using ehci_hcd and address 3
[374535.724000] usb 4-2: configuration #1 chosen from 1 choice
[374535.872000] usbcore: registered new interface driver libusual
[374535.880000] Initializing USB Mass Storage driver...
[374535.880000] scsi2 : SCSI emulation for USB Mass Storage devices
[374535.880000] usbcore: registered new interface driver usb-storage
[374535.880000] USB Mass Storage support registered.
[374535.880000] usb-storage: device found at 3
[374535.880000] usb-storage: waiting for device to settle before scanning
[374540.880000] usb-storage: device scan complete
[374540.896000] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.2  PQ: 0 ANSI: 2
[374540.896000] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[374540.896000] sdb: Write Protect is off
[374540.896000] sdb: Mode Sense: 03 00 00 00
[374540.896000] sdb: assuming drive cache: write through
[374540.900000] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[374540.900000] sdb: Write Protect is off
[374540.900000] sdb: Mode Sense: 03 00 00 00
[374540.900000] sdb: assuming drive cache: write through
[374540.900000]  sdb: sdb1
[374540.904000] sd 2:0:0:0: Attached scsi removable disk sdb
[374540.904000] sd 2:0:0:0: Attached scsi generic sg2 type 0


Do is there any way to make vm recognize the flashdrive.

Thanks.

---

### Post by scxtt on 2007-07-06
hmm ... one thing i noticed when i tried to connect my phone to my XP VM and it wasn't working (always worked fine in the past) were these lines:
```
:> cat /path/to/<virtual_machine>.vmx | grep -i usb
usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"
#usb.autoConnect.device0 = "path:1/0 autoclean:1"
#usb.autoConnect.device1 = ""
```which i had done intentionally cause (at the time) i didn't want usb enabled on my VM at boot (but didn't want to remove the device) ... once i uncommented the lines, it was working again ... i restarted the VM after uncommenting ... so see if you have lines like that ...

---

