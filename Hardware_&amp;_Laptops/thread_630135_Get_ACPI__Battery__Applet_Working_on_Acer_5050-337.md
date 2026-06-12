---
title: "Get ACPI / Battery / Applet Working on Acer 5050-3371 (ZR3) Gusty 7.10"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by aubreyisland on 2007-12-03
**[COLOR="Red"]Deprecated! See Post #3[/COLOR]**

Okay guys, when I heard Gusty came out I totally had to try it out. Awesome, everything works great minus wireless which I fixed using ndiswrapper. But, there was this other little problem: I tried adding the Battery Applet to the Gnome panel, and it always stayed a little plug, even if I was on battery; I knew something was wrong.

I searched my dmesg at the time and it said my battery was not present (battery absent). Well for a few days I looked at tons of stuff like upgrading my kernel, etc.

**[SIZE="4"]And then I found [_this._]("http://ubuntuforums.org/showthread.php?t=609925")[/SIZE]**

This guys instructions worked perfectly and now I have a little battery icon that changes when I unplug it, etc. Plus ACPI works and dmesg says I have a battery plugged in.

So thanks to him! I am going to attach the instructions here again, for convenience, and attach the DSTD file I used [tar.gz], in case the link stops working.

[SIZE="5"]**Here are the exact instructions I used:**[/SIZE]

The Acer Aspire 5050 line tends to come with a buggy ACPI table that causes the following symptoms in its laptops:
[LIST]
[*]Battery monitor program shows power as always plugged in
[*]Computer gets VERY HOT (fails to cool)
[*]Computer locks up occasionally
[*]dmesg says your battery is not present
[/LIST]

If you're experiencing any of the following problems, this HOWTO might be for you.

[LIST=1]
[*]Open up a terminal
[*]Install Intel's IASL compiler
```
sudo aptitude update
sudo aptitude install iasl
```
[*]Download the fixed DSDT file
```
wget -O dsdt.asl http://blakecmartin.googlepages.com/acer-aspire-5050.asl
```
[*]Compile the custom DSDT (you should receive 4 warnings and 0 errors; this is normal)
```
iasl -tc dsdt.asl
```
[*]Install the custom DSDT
```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
```
[*]Update your kernel images to use the custom DSDT
```
sudo update-initramfs -c -k all
```
[/LIST]

Restart your computer. Hopefully, the problem is fixed.[/QUOTE]

Let everyone know if this helped!

A chunk (from messages.log) of my dmesg from before I did this with the battery absent message:

```
Dec  2 17:25:27 aubrey-laptop kernel: [   38.674025] lp: driver loaded but no devices found
Dec  2 17:25:27 aubrey-laptop kernel: [   38.704885] ndiswrapper version 1.45 loaded (smp=yes)
Dec  2 17:25:27 aubrey-laptop kernel: [   38.788834] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
Dec  2 17:25:27 aubrey-laptop kernel: [   38.789003] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Dec  2 17:25:27 aubrey-laptop kernel: [   38.789009] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 18
Dec  2 17:25:27 aubrey-laptop kernel: [   38.789047] ndiswrapper (ZwClose:2247): closing handle 0xebfdf928 not implemented
Dec  2 17:25:27 aubrey-laptop kernel: [   39.201099] ndiswrapper: using IRQ 18
Dec  2 17:25:27 aubrey-laptop kernel: [   39.401507] wlan0: ethernet device 00:19:7e:29:3f:a0 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: '', 168C:001C.5.conf
Dec  2 17:25:27 aubrey-laptop kernel: [   39.412286] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Dec  2 17:25:27 aubrey-laptop kernel: [   39.415220] usbcore: registered new interface driver ndiswrapper
Dec  2 17:25:27 aubrey-laptop kernel: [   39.448157] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
Dec  2 17:25:27 aubrey-laptop kernel: [   39.722730] EXT3 FS on sda1, internal journal
Dec  2 17:25:27 aubrey-laptop kernel: [   41.153133] ACPI: Battery Slot [BAT1] (battery absent)
Dec  2 17:25:27 aubrey-laptop kernel: [   41.322072] input: Power Button (FF) as /class/input/input4
Dec  2 17:25:27 aubrey-laptop kernel: [   41.325302] ACPI: Power Button (FF) [PWRF]
Dec  2 17:25:27 aubrey-laptop kernel: [   41.354249] input: Power Button (CM) as /class/input/input5
Dec  2 17:25:27 aubrey-laptop kernel: [   41.357430] ACPI: Power Button (CM) [PWRB]
Dec  2 17:25:27 aubrey-laptop kernel: [   41.386951] input: Lid Switch as /class/input/input6
Dec  2 17:25:27 aubrey-laptop kernel: [   41.390132] ACPI: Lid Switch [LID]
Dec  2 17:25:27 aubrey-laptop kernel: [   41.419029] input: Sleep Button (CM) as /class/input/input7
Dec  2 17:25:27 aubrey-laptop kernel: [   41.422258] ACPI: Sleep Button (CM) [SLPB]
Dec  2 17:25:27 aubrey-laptop kernel: [   41.478578] No dock devices found.
```

My current dmesg:
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe90000 (usable)
[    0.000000]  BIOS-e820: 000000002fe90000 - 000000002fe9a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fe9a000 - 000000002ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 766MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8a60
[    0.000000] Entering add_active_range(0, 0, 196240) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196240
[    0.000000]   HighMem    196240 ->   196240
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196240
[    0.000000] On node 0 totalpages: 196240
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1501 pages used for memmap
[    0.000000]   Normal zone: 190643 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8A30 checksum 0
[    0.000000] ACPI: RSDP 000F8A30, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 2FE92BD2, 003C (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
[    0.000000] ACPI: FACP 2FE99C36, 0074 (r1 ATI    Bowfin    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 2FE92C0E, 7028 (r1    ATI    SB460  6040000 MSFT  2000002)
[    0.000000] ACPI: FACS 2FE9AFC0, 0040
[    0.000000] ACPI: SSDT 2FE99CAA, 0136 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 2FE99DE0, 0046 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 2FE99E26, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: BOOT 2FE99E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 2FE99E8A, 0176 (r1 ACRSYS ACRPRDCT  6040000 acer        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 194707
[    0.000000] Kernel command line: root=UUID=0555d907-25b0-42b7-a9b7-6ced08026528 ro quiet
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.191 MHz processor.
[   12.155559] Console: colour VGA+ 80x25
[   12.155830] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.156137] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.166518] Memory: 766468k/784960k available (2015k kernel code, 17872k reserved, 916k data, 364k init, 0k highmem)
[   12.166527] virtual kernel memory layout:
[   12.166528]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   12.166529]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.166531]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   12.166532]     lowmem  : 0xc0000000 - 0xefe90000   ( 766 MB)
[   12.166533]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   12.166534]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   12.166535]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   12.166538] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.166567] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.246515] Calibrating delay using timer specific routine.. 4404.57 BogoMIPS (lpj=8809157)
[   12.246534] Security Framework v1.0.0 initialized
[   12.246538] SELinux:  Disabled at boot.
[   12.246549] Mount-cache hash table entries: 512
[   12.246633] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d
[   12.246640] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.246642] CPU: L2 Cache: 512K (64 bytes/line)
[   12.246645] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001d
[   12.246653] Compat vDSO mapped to ffffe000.
[   12.246661] Checking 'hlt' instruction... OK.
[   12.262590] SMP alternatives: switching to UP code
[   12.262709] Freeing SMP alternatives: 11k freed
[   12.262921] Early unpacking initramfs... done
[   12.521664] ACPI: Core revision 20070126
[   12.521737] ACPI: Looking for DSDT in initramfs... successfully read 25216 bytes from /DSDT.aml.
[   12.521764] ACPI: Table DSDT replaced by host OS
[   12.521767] ACPI: DSDT 00000000, 6280 (r1    ATI    SB460  6040000 INTL 20061109)
[   12.994596] CPU0: AMD Turion(tm) 64 Mobile Technology MK-38 stepping 02
[   12.994614] Total of 1 processors activated (4404.57 BogoMIPS).
[   12.994777] ENABLING IO-APIC IRQs
[   12.994957] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   13.141729] Brought up 1 CPUs
[   13.141807] Booting paravirtualized kernel on bare hardware
[   13.141877] Time:  6:09:41  Date: 11/03/107
[   13.141894] NET: Registered protocol family 16
[   13.141958] EISA bus registered
[   13.141971] ACPI: bus type pci registered
[   13.157548] PCI: BIOS BUG #81[49435000] found
[   13.157589] PCI: Using configuration type 1
[   13.157591] Setting up standard PCI resources
[   13.158827] ACPI: EC: Look up EC in DSDT
[   13.159664] ACPI: EC: GPE=0x14, ports=0x66, 0x62
[   13.181204] ACPI: Interpreter enabled
[   13.181206] ACPI: (supports S0 S3 S4 S5)
[   13.181217] ACPI: Using IOAPIC for interrupt routing
[   13.184337] ACPI: EC: GPE=0x14, ports=0x66, 0x62
[   13.184371] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.184376] PCI: Probing PCI hardware (bus 00)
[   13.186013] PCI: Transparent bridge - 0000:00:14.4
[   13.186114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.186242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   13.186332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   13.186421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   13.186511] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   13.186606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.186706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   13.188691] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   13.188789] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   13.188885] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   13.188981] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   13.189077] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   13.189172] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   13.189271] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   13.189367] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   13.189463] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   13.189529] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.189537] pnp: PnP ACPI init
[   13.189543] ACPI: bus type pnp registered
[   13.191169] pnp: PnP ACPI: found 10 devices
[   13.191171] ACPI: ACPI bus type pnp unregistered
[   13.191174] PnPBIOS: Disabled by ACPI PNP
[   13.191213] PCI: Using ACPI for IRQ routing
[   13.191215] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.191222] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   13.191264] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   13.191302] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   13.191340] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   13.191378] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[   13.191416] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[   13.191546] NET: Registered protocol family 8
[   13.191548] NET: Registered protocol family 20
[   13.191593] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   13.191596] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   13.191599] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.191607] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   13.191609] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   13.191613] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   13.191616] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   13.191618] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   13.193656] Time: tsc clocksource has been installed.
[   13.221806] PCI: Bridge: 0000:00:01.0
[   13.221808]   IO window: 9000-9fff
[   13.221811]   MEM window: b0100000-b01fffff
[   13.221813]   PREFETCH window: c0000000-cfffffff
[   13.221816] PCI: Bridge: 0000:00:04.0
[   13.221817]   IO window: disabled.
[   13.221819]   MEM window: b0200000-b02fffff
[   13.221821]   PREFETCH window: disabled.
[   13.221823] PCI: Bridge: 0000:00:05.0
[   13.221825]   IO window: disabled.
[   13.221827]   MEM window: disabled.
[   13.221828]   PREFETCH window: disabled.
[   13.221831] PCI: Bridge: 0000:00:06.0
[   13.221832]   IO window: disabled.
[   13.221834]   MEM window: disabled.
[   13.221836]   PREFETCH window: disabled.
[   13.221838] PCI: Bridge: 0000:00:07.0
[   13.221839]   IO window: disabled.
[   13.221841]   MEM window: disabled.
[   13.221843]   PREFETCH window: disabled.
[   13.221854] PCI: Bus 9, cardbus bridge: 0000:08:01.0
[   13.221856]   IO window: 0000a400-0000a4ff
[   13.221861]   IO window: 0000a800-0000a8ff
[   13.221867]   PREFETCH window: 50000000-53ffffff
[   13.221872]   MEM window: 58000000-5bffffff
[   13.221878] PCI: Bridge: 0000:00:14.4
[   13.221880]   IO window: a000-afff
[   13.221886]   MEM window: b0300000-b03fffff
[   13.221891]   PREFETCH window: 50000000-53ffffff
[   13.221907] PCI: Enabling device 0000:00:04.0 (0000 -> 0002)
[   13.221910] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   13.221916] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   13.221922] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.221928] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.221950] PCI: Enabling device 0000:08:01.0 (0000 -> 0003)
[   13.221957] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 23 (level, low) -> IRQ 16
[   13.221974] NET: Registered protocol family 2
[   13.257626] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.257719] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   13.258540] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.258800] TCP: Hash tables configured (established 131072 bind 65536)
[   13.258803] TCP reno registered
[   13.269690] checking if image is initramfs... it is
[   13.725179] Switched to high resolution mode on CPU 0
[   13.778607] Freeing initrd memory: 7053k freed
[   13.778686] Simple Boot Flag at 0x36 set to 0x1
[   13.778903] audit: initializing netlink socket (disabled)
[   13.778915] audit(1196662180.956:1): initialized
[   13.780269] VFS: Disk quotas dquot_6.5.1
[   13.780307] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.780372] io scheduler noop registered
[   13.780374] io scheduler anticipatory registered
[   13.780375] io scheduler deadline registered
[   13.780387] io scheduler cfq registered (default)
[   13.780394] PCI: MSI quirk detected. MSI deactivated.
[   13.780435] Boot video device is 0000:01:05.0
[   13.780507] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   13.780526] assign_interrupt_mode Found MSI capability
[   13.780528] Allocate Port Service[0000:00:04.0:pcie00]
[   13.780554] Allocate Port Service[0000:00:04.0:pcie02]
[   13.780599] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   13.780615] assign_interrupt_mode Found MSI capability
[   13.780617] Allocate Port Service[0000:00:05.0:pcie00]
[   13.780662] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.780679] assign_interrupt_mode Found MSI capability
[   13.780681] Allocate Port Service[0000:00:06.0:pcie00]
[   13.780724] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.780741] assign_interrupt_mode Found MSI capability
[   13.780743] Allocate Port Service[0000:00:07.0:pcie00]
[   13.780833] isapnp: Scanning for PnP cards...
[   14.136965] isapnp: No Plug & Play device found
[   14.156784] Real Time Clock Driver v1.12ac
[   14.156854] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.157729] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.157892] input: Macintosh mouse button emulation as /class/input/input0
[   14.157945] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.161743] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.162736] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.162741] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.162743] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.162745] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.162748] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.162892] mice: PS/2 mouse device common for all mice
[   14.163059] EISA: Probing bus 0 at eisa.0
[   14.163070] Cannot allocate resource for EISA slot 1
[   14.163096] Cannot allocate resource for EISA slot 8
[   14.163098] EISA: Detected 0 cards.
[   14.163169] TCP cubic registered
[   14.163180] NET: Registered protocol family 1
[   14.163197] Using IPI No-Shortcut mode
[   14.163342]   Magic number: 3:511:164
[   14.163390]   hash matches device ttyq4
[   14.163676] Freeing unused kernel memory: 364k freed
[   14.284635] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.307301] AppArmor: AppArmor initialized<5>audit(1196662181.456:2):  type=1505 info="AppArmor initialized" pid=1193
[   14.313555] fuse init (API version 7.8)
[   14.316907] Failure registering capabilities with primary security module.
[   14.332332] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   14.421752] ACPI: Thermal Zone [THRM] (59 C)
[   14.840031] SCSI subsystem initialized
[   14.843497] libata version 2.21 loaded.
[   14.848740] sata_sil 0000:00:12.0: version 2.2
[   14.848782] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   14.848790] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[   14.848856] scsi0 : sata_sil
[   14.848893] scsi1 : sata_sil
[   14.849139] ata1: SATA max UDMA/100 cmd 0xf083c080 ctl 0xf083c08a bmdma 0xf083c000 irq 17
[   14.849143] ata2: SATA max UDMA/100 cmd 0xf083c0c0 ctl 0xf083c0ca bmdma 0xf083c008 irq 17
[   14.861651] usbcore: registered new interface driver usbfs
[   14.861671] usbcore: registered new interface driver hub
[   14.861688] usbcore: registered new device driver usb
[   14.864514] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.977753] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.977758] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.986693] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   15.315676] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   15.324266] ata1.00: ATA-7: SAMSUNG HM080HI, AB100-16, max UDMA/100
[   15.324268] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   15.340240] ata1.00: configured for UDMA/100
[   15.651338] ata2: SATA link down (SStatus 0 SControl 310)
[   15.651429] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080HI  AB10 PQ: 0 ANSI: 5
[   15.651772] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[   15.651784] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   15.651984] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   15.652006] ohci_hcd 0000:00:13.0: irq 18, io mem 0xb0005000
[   15.657717] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   15.657728] sd 0:0:0:0: [sda] Write Protect is off
[   15.657730] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.657742] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.657785] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   15.657792] sd 0:0:0:0: [sda] Write Protect is off
[   15.657794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.657805] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.657808]  sda: sda1 sda2 <<6>usb usb1: configuration #1 chosen from 1 choice
[   15.707413] hub 1-0:1.0: USB hub found
[   15.707425] hub 1-0:1.0: 4 ports detected
[   15.714304]  sda5 >
[   15.714674] sd 0:0:0:0: [sda] Attached SCSI disk
[   15.717853] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   15.811295] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[   15.811311] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   15.811332] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   15.811347] ohci_hcd 0000:00:13.1: irq 18, io mem 0xb0006000
[   15.867269] usb usb2: configuration #1 chosen from 1 choice
[   15.867291] hub 2-0:1.0: USB hub found
[   15.867304] hub 2-0:1.0: 4 ports detected
[   15.878850] Attempting manual resume
[   15.878853] swsusp: Resume From Partition 8:5
[   15.878854] PM: Checking swsusp image.
[   15.879103] PM: Resume from disk failed.
[   15.928355] kjournald starting.  Commit interval 5 seconds
[   15.928364] EXT3-fs: mounted filesystem with ordered data mode.
[   15.971234] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[   15.971246] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   15.971270] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   15.971314] ehci_hcd 0000:00:13.2: irq 18, io mem 0xb0007000
[   15.971326] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.971388] usb usb3: configuration #1 chosen from 1 choice
[   15.971412] hub 3-0:1.0: USB hub found
[   15.971418] hub 3-0:1.0: 8 ports detected
[   16.075129] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   16.075151] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   16.075161] ATIIXP: chipset revision 128
[   16.075163] ATIIXP: not 100% native mode: will probe irqs later
[   16.075172]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[   16.075186] ATIIXP: simplex device: DMA disabled
[   16.075187] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   16.075191] Probing IDE interface ide0...
[   16.810665] hda: HL-DT-ST DVDRAM GSA-T10N, ATAPI CD/DVD-ROM drive
[   17.145935] hda: selected mode 0x42
[   17.146800] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   17.150191] Probing IDE interface ide1...
[   17.709540] 8139cp 0000:08:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   17.709584] 8139cp 0000:08:02.0: Try the "8139too" driver instead.
[   23.809750] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.816063] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.833607] Linux agpgart interface v0.102 (c) Dave Jones
[   24.523774] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   24.722948] input: PC Speaker as /class/input/input2
[   25.038582] Yenta: CardBus bridge found at 0000:08:01.0 [1025:010f]
[   25.038612] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.038614] Yenta: Routing CardBus interrupts to PCI
[   25.038620] Yenta TI: socket 0000:08:01.0, mfunc 0x00001202, devctl 0x44
[   25.050732] 8139too Fast Ethernet driver 0.9.28
[   25.079125] sdhci: Secure Digital Host Controller Interface driver
[   25.079129] sdhci: Copyright(c) Pierre Ossman
[   25.110530] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   25.110537] Uniform CD-ROM driver Revision: 3.20
[   25.278983] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   25.278988] Socket status: 30000006
[   25.278991] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   25.278996] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   25.279000] cs: IO port probe 0xa000-0xafff: clean.
[   25.279223] pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xb03fffff
[   25.279294] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   25.286366] ACPI: PCI Interrupt 0000:08:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[   25.287040] eth0: RealTek RTL8139 at 0xf09a4c00, 00:16:36:fe:df:be, IRQ 20
[   25.287042] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   25.290929] sdhci: SDHCI controller found at 0000:08:01.2 [1524:0550] (rev 1)
[   25.290950] ACPI: PCI Interrupt 0000:08:01.2[B] -> GSI 22 (level, low) -> IRQ 17
[   25.291052] mmc0: SDHCI at 0xb0301400 irq 17 DMA
[   25.297050] sdhci: SDHCI controller found at 0000:08:01.4 [1524:0551] (rev 1)
[   25.297069] PCI: Enabling device 0000:08:01.4 (0000 -> 0002)
[   25.297073] ACPI: PCI Interrupt 0000:08:01.4[B] -> GSI 22 (level, low) -> IRQ 17
[   25.297117] mmc1: SDHCI at 0xb0301100 irq 17 PIO
[   25.305643] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   25.350032] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   25.552523] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   25.709887] cs: IO port probe 0x100-0x3af: clean.
[   25.712156] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   25.713110] cs: IO port probe 0x820-0x8ff: clean.
[   25.713913] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   25.714770] cs: IO port probe 0xa00-0xaff: clean.
[   26.717217] lp: driver loaded but no devices found
[   26.759020] ndiswrapper version 1.45 loaded (smp=yes)
[   26.854095] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   26.854261] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   26.854267] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   26.854307] ndiswrapper (ZwClose:2247): closing handle 0xebf89928 not implemented
[   26.854437] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   27.266337] ndiswrapper: using IRQ 19
[   27.467444] wlan0: ethernet device 00:19:7e:29:3f:a0 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: '', 168C:001C.5.conf
[   27.471624] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   27.476863] usbcore: registered new interface driver ndiswrapper
[   27.528714] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
[   27.821907] EXT3 FS on sda1, internal journal
[   29.349173] ACPI: Battery Slot [BAT1] (battery present)
[   29.513083] input: Power Button (FF) as /class/input/input4
[   29.516396] ACPI: Power Button (FF) [PWRF]
[   29.546744] input: Power Button (CM) as /class/input/input5
[   29.550017] ACPI: Power Button (CM) [PWRB]
[   29.580033] input: Lid Switch as /class/input/input6
[   29.583306] ACPI: Lid Switch [LID]
[   29.612932] input: Sleep Button (CM) as /class/input/input7
[   29.616267] ACPI: Sleep Button (CM) [SLPB]
[   29.681333] No dock devices found.
[   29.731886] ACPI: AC Adapter [ACAD] (off-line)
[   29.959201] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-38 processors (version 2.00.00)
[   29.959236] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xd
[   29.959238] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xf
[   29.959240] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x11
[   29.959242] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x13
[   29.959244] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[   31.054584] eth0: link down
[   31.064105] ppdev: user-space parallel port driver
[   31.347504] audit(1196662199.583:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4802 profile="/usr/sbin/cupsd"
[   31.548848] Failure registering capabilities with primary security module.
[   31.736624] Bluetooth: Core ver 2.11
[   31.736714] NET: Registered protocol family 31
[   31.736716] Bluetooth: HCI device and connection manager initialized
[   31.736719] Bluetooth: HCI socket layer initialized
[   31.750640] Bluetooth: L2CAP ver 2.8
[   31.750643] Bluetooth: L2CAP socket layer initialized
[   31.828370] Bluetooth: RFCOMM socket layer initialized
[   31.828445] Bluetooth: RFCOMM TTY layer initialized
[   31.828447] Bluetooth: RFCOMM ver 1.8
[   19.296000] Marking TSC unstable due to: cpufreq changes.
[   19.300000] Time: acpi_pm clocksource has been installed.
[   19.476000] apm: BIOS not found.
[   19.984000] Clocksource tsc unstable (delta = -136406041 ns)
[   20.728000] [fglrx] Maximum main memory to use for locked dma buffers: 678 MBytes.
[   20.728000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   20.752000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[   22.352000] [fglrx] total      GART = 130023424
[   22.352000] [fglrx] free       GART = 114032640
[   22.352000] [fglrx] max single GART = 114032640
[   22.352000] [fglrx] total      LFB  = 134217728
[   22.352000] [fglrx] free       LFB  = 119828480
[   22.352000] [fglrx] max single LFB  = 119828480
[   22.352000] [fglrx] total      Inv  = 134217728
[   22.352000] [fglrx] free       Inv  = 134217728
[   22.352000] [fglrx] max single Inv  = 134217728
[   22.352000] [fglrx] total      TIM  = 0
[   28.524000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   64.668000] NET: Registered protocol family 17
[   73.060000] NET: Registered protocol family 10
[   73.060000] lo: Disabled Privacy Extensions
[   73.060000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   83.392000] wlan0: no IPv6 routers present

```

---

### Post by aubreyisland on 2008-05-24
I must have changed something. It's like my applet is confused! It will say on battery power, then on AC; sometimes only AC. I tried re-installing the custom file again, to no avail. 

I swear, it's little things like this that get me OUT of Ubuntu in only a couple weeks. I may not need all the extra time configuring Firefox not to crash using flash (you'd think Ubuntu would have already fixed something like that), but I need to know when my battery is going down!

The second I think Ubuntu is working, it breaks! :confused:

---

### Post by aubreyisland on 2008-05-24
I [updated my bios to 3315]("http://imaginecambio.com/2008/05/24/fixing-the-acer-5050-battery-applet-on-ubuntu-fiesty/"), and my applet works without the custom DSDT! Visit the link for files.

Note: (Few hours later). I am having problems, still, with the applet. I have obviously updated my bios, but still, the applet was getting confused (after a suspend), and I ended up installing the custom DSTD, and now seems well. But, I am going to try and ef with it a little and see what is causing the error.

So I just tried a restart. Here's what I did, I installed the custom DSTD, and still, it wasn't working after the flash update. Then I pulled my battery out unplugged and it shut down, restarted, and applet working again?

Go figure. Now I am going to try a few suspends and see if it messes anything up...

Okay, just got done with the suspend tryouts, and applet still working. I put it in suspend with it plugged in and took it out with the AC out, using battery (thinking this is what confused it), nope.

I hate this about Ubuntu, that things go wrong, and it's like ghosts in the machine, because I don't know what the f went wrong. But, I want to note I did a few kernel updates for usplashes and I wonder if that is causing the problem, using *update-initramfs*. So I am going to try doing one of those and see if it f's things up...

Before reboot...

```
aubrey@aubrey-laptop:~$ sudo update-initramfs -c -k all
Password:
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
update-initramfs: Generating /boot/initrd.img--v
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/usb/core/usbcore.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/usb/host/ehci-hcd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/usb/host/ohci-hcd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/usb/host/uhci-hcd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/hid/hid.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/usb/input/usbhid.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/usb/storage/libusual.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_mod.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/mbcache.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/ext2/ext2.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/jbd/jbd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/ext3/ext3.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/isofs/isofs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/jfs/jfs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/net/sunrpc/sunrpc.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/lockd/lockd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/nfs/nfs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/reiserfs/reiserfs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/udf/udf.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/fs/xfs/xfs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/net/packet/af_packet.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/mii.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/3c59x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/8139cp.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/8139too.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/8390.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/b44.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/bnx2.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/defxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/dl2k.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/e100.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/epic100.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/eql.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/fealnx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/forcedeth.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/hp100.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/myri10ge/myri10ge.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/natsemi.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/ne2k-pci.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/netconsole.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/ns83820.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/pcnet32.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/qla3xxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/r8169.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/s2io.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/sis900.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/skge.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/slhc.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/starfire.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/sundance.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/sungem_phy.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/sungem.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/sunhme.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tg3.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tlan.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tulip/de2104x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tulip/de4x5.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tulip/dmfe.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tulip/tulip.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tulip/winbond-840.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/tulip/xircom_cb.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/via-rhine.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/lib/crc-ccitt.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/via-velocity.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/net/yellowfin.ko
Copying module directory kernel/drivers/ide
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/ide-tape.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/cdrom/cdrom.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/ide-cd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/ide-generic.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/ide-pnp.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/via82cxxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/cy82c693.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/sc1200.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/hpt34x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/cs5535.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/opti621.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/trm290.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/generic.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/piix.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/aec62xx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/cs5530.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/atiixp.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/siimage.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/ns87415.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/alim15x3.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/amd74xx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/hpt366.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/sis5513.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/cmd64x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/pdc202xx_old.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/ide-floppy.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ide/ide-disk.ko
Copying module directory kernel/drivers/scsi
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sr_mod.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_transport_spi.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/aha1740.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/aha1542.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_transport_fc.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/libata.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/advansys.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/ultrastor.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/atp870u.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/aha152x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_debug.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/aacraid/aacraid.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/u14-34f.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/pas16.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sg.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/parport/parport.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/ppa.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/ibmmca.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sym53c416.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/g_NCR5380.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/wd7000.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/seagate.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/t128.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_tgt.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/libsrp.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/tmscsim.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/qla1280.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sd_mod.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_transport_sas.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/psi240i.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/53c700.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sim710.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/nsp32.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/pcmcia/pcmcia_core.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/pcmcia/pcmcia.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/dtc.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/libiscsi.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/ips.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/NCR_D700.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/st.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/megaraid.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/qlogicfas.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/libsas/libsas.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/raid_class.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/fd_mcs.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/NCR53c406a.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/in2000.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/ide-scsi.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/NCR_Q720_mod.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/dmx3191d.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/scsi_wait_scan.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/gdth.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/ch.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/dc395x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/osst.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/message/fusion/mptspi.ko
Adding firmware /lib/firmware/2.6.20-16-generic/ql2100_fw.bin
Adding firmware /lib/firmware/2.6.20-16-generic/ql2200_fw.bin
Adding firmware /lib/firmware/2.6.20-16-generic/ql2300_fw.bin
Adding firmware /lib/firmware/2.6.20-16-generic/ql2322_fw.bin
Adding firmware /lib/firmware/2.6.20-16-generic/ql2400_fw.bin
Adding firmware /lib/firmware/2.6.20-16-generic/aic94xx-seq.fw
Copying module directory kernel/drivers/ata
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_qdi.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_serverworks.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/ata_generic.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_efar.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_mpiix.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_marvell.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/ata_piix.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_sis.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_jmicron.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_triflex.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_promise.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/ahci.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_svw.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_rz1000.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_it821x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_sis.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_sil24.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pdc_adma.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_sil.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_inic162x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_qstor.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_netcell.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_sl82c105.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_uli.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ata/pata_sil680.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ieee1394/ieee1394.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ieee1394/ohci1394.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/ieee1394/sbp2.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/xd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/pktcdvd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/aoe/aoe.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/cpqarray.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/loop.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/bpck6.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/block/cciss.ko
Adding binary /usr/share/initramfs-tools/init
Adding binary /etc/initramfs-tools/initramfs.conf
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin//busybox
Adding binary /sbin/modprobe
Adding library /lib/libc.so.6
Adding library /lib/ld-linux.so.2
Adding binary /sbin/depmod
Adding binary /sbin/rmmod
Calling hook brltty
Adding binary /usr/share/brltty/initramfs/brltty.sh
Adding binary /sbin/brltty-setup
Calling hook kernelextras
Adding module /lib/modules/2.6.20-16-generic/kernel/security/commoncap.ko
Adding module /lib/modules/2.6.20-16-generic/initrd/capability.ko
Adding module /lib/modules/2.6.20-16-generic/initrd/vesafb.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/video/vgastate.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/video/vga16fb.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/video/console/softcursor.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/video/console/bitblit.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/video/console/font.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/video/console/tileblit.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/video/console/fbcon.ko
Calling hook thermal
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/acpi/fan.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/acpi/processor.ko
Adding module /lib/modules/2.6.20-16-generic/kernel/drivers/acpi/thermal.ko
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.7.so
Adding binary /sbin/udevd
Adding library /lib/libselinux.so.1
Adding library /lib/libsepol.so.1
Adding library /lib/libdl.so.2
Adding binary /sbin/udevtrigger
Adding binary /sbin/udevsettle
Adding binary /lib/udev/dvb_device_name
Adding binary /lib/udev/usb_device_name
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/edd_id
Adding binary /lib/udev/usb_id
Adding binary /lib/udev/vol_id
Adding library /lib/libvolume_id.so.0
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Adding binary /lib/udev/firmware_helper
Adding binary /lib/udev/pnp_modules
Adding binary /lib/udev/ide_media
Adding binary /lib/udev/vio_type
Adding binary /lib/udev/watershed
Calling hook usplash
Adding binary /sbin/usplash
Adding library /lib/libusplash.so.0
Adding library /lib/libx86.so.1
Adding binary /sbin/usplash_write
Adding binary /etc/usplash.conf
Calling hook console_tools
Adding binary /usr/bin/consolechars
Adding library /lib/libconsole.so.0
Adding library /lib/libcfont.so.0
Adding library /lib/libctutils.so.0
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook dmsetup
Adding binary /sbin/devmap_name
Adding library /lib/libdevmapper.so.1.02
Calling hook console_setup
Adding binary /etc/initramfs-tools/DSDT.aml
Building cpio /boot/initrd.img--v initramfs
```

So, after the reboot - applet still working? So who knows what the f made it, in the first place, stop working, and what the f made it start working? I have the custom DSDT and a flashed bios at this point.

---

