---
title: "winmodem linux drivers for dell laptop"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by go_beep_yourself on 2008-01-28
I just ran scanModem on a Dell laptop with an internal software modem. I need help on what to do next. Here are the results.

ModemData.txt:
```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.22-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: http://www.linux.org/groups/index.html. 
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007
 scanModem update of:  2008_01_22


 There are no blacklisted modem drivers in /etc/modprobe*  files 

The Advanced Linux Sound Architecture (ALSA) packages providing audio support, 
also includes drivers for some modems. The ALSA diagnostics are written during 
bootup to /proc/asound/ folders.

 The /proc/asound/ audio+modem diagostics are being copied.
 Finished copy to Modem/ALSAroot.tgz

The ALSA verion is 1.0.14
The modem cards detected by "aplay -l"  are:


The /proc/asound/pcm file reports:
-----------------------
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at irq 7

USB modem not detected by lsusb

For candidate card in slot 00:1f.6, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1f.6	8086:24c6	14e4:4d64	Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
  7:        394    XT-PIC-XT        eth0, Intel 82801DB-ICH4
 --- Bootup diagnostics for card in PCI slot 00:1f.6 ----
[    9.308318] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    9.308329] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

 The PCI slot 00:1f.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 


 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

```


scanout.00:1f.6:
```
PCIDEV=8086:24c6
CLASS="Class 0703: 8086:24c6"
NAME="Modem: Intel Corporation 82801DB/DBL/DBM "
Vendor=8086
Device=24c6
SUBSYS=14e4:4d64
SUBNAME=" Broadcom Corporation Unknown device 4d64"
SUBven=14e4
IRQ=7
Test="./scanModem test 8086:24c6 14e4:4d64"
```

dmesg.txt:
```
           CPU0       
  0:     117088    XT-PIC-XT        timer
  1:        366    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  7:        394    XT-PIC-XT        eth0, Intel 82801DB-ICH4
  8:          3    XT-PIC-XT        rtc
  9:          1    XT-PIC-XT        acpi
 11:     128415    XT-PIC-XT        uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, yenta, i915@pci:0000:00:02.0
 12:     142666    XT-PIC-XT        i8042
 14:      10388    XT-PIC-XT        libata
 15:       9733    XT-PIC-XT        libata
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fec9000 (usable)
[    0.000000]  BIOS-e820: 000000001fec9000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130761) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130761
[    0.000000]   HighMem    130761 ->   130761
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130761
[    0.000000] On node 0 totalpages: 130761
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125676 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
[    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 1FEF0000, 0028 (r1 DELL    CPi R   27D40814 ASL        61)
[    0.000000] ACPI: FACP 1FEF0400, 0074 (r1 DELL    CPi R   27D40814 ASL        61)
[    0.000000] ACPI: DSDT 1FEF0C00, 2586 (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 1FEFF800, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] Built 1 zonelists.  Total pages: 129740
[    0.000000] Kernel command line: root=UUID=745c93e4-5055-40ab-a438-0ba8063ade80 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2597.816 MHz processor.
[    7.497686] Console: colour VGA+ 80x25
[    7.498021] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.498563] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.509254] Memory: 506764k/523044k available (2015k kernel code, 15720k reserved, 916k data, 364k init, 0k highmem)
[    7.509265] virtual kernel memory layout:
[    7.509266]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.509267]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.509268]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    7.509269]     lowmem  : 0xc0000000 - 0xdfec9000   ( 510 MB)
[    7.509270]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.509271]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    7.509273]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    7.509276] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.509317] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.589308] Calibrating delay using timer specific routine.. 5200.10 BogoMIPS (lpj=10400204)
[    7.589342] Security Framework v1.0.0 initialized
[    7.589351] SELinux:  Disabled at boot.
[    7.589366] Mount-cache hash table entries: 512
[    7.589558] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[    7.589574] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    7.589579] CPU: L2 cache: 128K
[    7.589582] CPU: Hyper-Threading is disabled
[    7.589586] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000
[    7.589603] Compat vDSO mapped to ffffe000.
[    7.589622] Checking 'hlt' instruction... OK.
[    7.605440] SMP alternatives: switching to UP code
[    7.605812] Freeing SMP alternatives: 11k freed
[    7.606184] Early unpacking initramfs... done
[    7.956992] ACPI: Core revision 20070126
[    7.957062] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.958197] ACPI: setting ELCR to 0200 (from 0800)
[    7.959694] CPU0: Intel(R) Celeron(R) CPU 2.60GHz stepping 09
[    7.959702] SMP motherboard not detected.
[    7.959704] Local APIC not detected. Using dummy APIC emulation.
[    7.959762] Brought up 1 CPUs
[    7.959962] Booting paravirtualized kernel on bare hardware
[    7.960048] Time: 20:49:47  Date: 00/28/108
[    7.960090] NET: Registered protocol family 16
[    7.960278] EISA bus registered
[    7.960300] ACPI: bus type pci registered
[    8.009610] PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2
[    8.009613] PCI: Using configuration type 1
[    8.009615] Setting up standard PCI resources
[    8.012136] ACPI: EC: Look up EC in DSDT
[    8.015259] ACPI: Interpreter enabled
[    8.015267] ACPI: (supports S0 S1 S3 S4 S5)
[    8.015294] ACPI: Using PIC for interrupt routing
[    8.027043] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.027067] PCI: Probing PCI hardware (bus 00)
[    8.027714] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    8.027719] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[    8.028140] PCI: Transparent bridge - 0000:00:1e.0
[    8.028296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.028643] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    8.040435] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    8.040574] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    8.040704] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    8.040831] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    8.040946] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.041079] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    8.041399] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.041426] pnp: PnP ACPI init
[    8.041449] ACPI: bus type pnp registered
[    8.053325] pnp: PnP ACPI: found 12 devices
[    8.053331] ACPI: ACPI bus type pnp unregistered
[    8.053338] PnPBIOS: Disabled by ACPI PNP
[    8.053459] PCI: Using ACPI for IRQ routing
[    8.053464] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.062229] NET: Registered protocol family 8
[    8.062233] NET: Registered protocol family 20
[    8.062419] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
[    8.062424] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    8.062426] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    8.062429] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    8.062439] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    8.062442] pnp: 00:02: ioport range 0x800-0x805 has been reserved
[    8.062444] pnp: 00:02: ioport range 0x808-0x80f has been reserved
[    8.062453] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    8.062456] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[    8.062459] pnp: 00:03: ioport range 0x810-0x85f has been reserved
[    8.062461] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[    8.062464] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[    8.062467] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[    8.062477] pnp: 00:08: ioport range 0x900-0x97f has been reserved
[    8.062486] pnp: 00:0b: ioport range 0x7b0-0x7bb has been reserved
[    8.062488] pnp: 00:0b: ioport range 0x7c0-0x7df has been reserved
[    8.062491] pnp: 00:0b: ioport range 0xbb0-0xbbb has been reserved
[    8.062493] pnp: 00:0b: ioport range 0xbc0-0xbdf has been reserved
[    8.062496] pnp: 00:0b: ioport range 0xfb0-0xfbb has been reserved
[    8.062498] pnp: 00:0b: ioport range 0xfc0-0xfdf has been reserved
[    8.062501] pnp: 00:0b: ioport range 0x13b0-0x13bb has been reserved
[    8.062509] pnp: 00:0b: ioport range 0x13c0-0x13df has been reserved
[    8.065124] Time: tsc clocksource has been installed.
[    8.093546] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    8.093550]   IO window: 0000d000-0000d0ff
[    8.093554]   IO window: 0000d400-0000d4ff
[    8.093559]   PREFETCH window: 30000000-33ffffff
[    8.093563]   MEM window: f8000000-fbffffff
[    8.093568] PCI: Bridge: 0000:00:1e.0
[    8.093571]   IO window: d000-efff
[    8.093576]   MEM window: f8000000-fdffffff
[    8.093582]   PREFETCH window: 30000000-35ffffff
[    8.093597] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.093614] PCI: Enabling device 0000:02:04.0 (0000 -> 0003)
[    8.093823] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    8.093828] PCI: setting IRQ 11 as level-triggered
[    8.093832] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    8.093860] NET: Registered protocol family 2
[    8.133159] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.133247] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.133459] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.133646] TCP: Hash tables configured (established 16384 bind 16384)
[    8.133654] TCP reno registered
[    8.145284] checking if image is initramfs... it is
[    8.596947] Switched to high resolution mode on CPU 0
[    8.814146] Freeing initrd memory: 7343k freed
[    8.814800] audit: initializing netlink socket (disabled)
[    8.814821] audit(1201553387.060:1): initialized
[    8.820505] VFS: Disk quotas dquot_6.5.1
[    8.820660] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.820946] io scheduler noop registered
[    8.820950] io scheduler anticipatory registered
[    8.820952] io scheduler deadline registered
[    8.820998] io scheduler cfq registered (default)
[    8.821018] Boot video device is 0000:00:02.0
[    8.821488] isapnp: Scanning for PnP cards...
[    9.175084] isapnp: No Plug & Play device found
[    9.305825] Real Time Clock Driver v1.12ac
[    9.306064] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.308307] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    9.308314] PCI: setting IRQ 7 as level-triggered
[    9.308318] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    9.308329] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    9.310118] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.310472] input: Macintosh mouse button emulation as /class/input/input0
[    9.310710] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.310917] i8042.c: Warning: Keylock active.
[    9.313527] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.313536] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.314075] mice: PS/2 mouse device common for all mice
[    9.314471] EISA: Probing bus 0 at eisa.0
[    9.314504] EISA: Detected 0 cards.
[    9.314652] TCP cubic registered
[    9.314682] NET: Registered protocol family 1
[    9.314719] Using IPI No-Shortcut mode
[    9.315059]   Magic number: 8:981:852
[    9.315195]   hash matches device ptyv4
[    9.315768] Freeing unused kernel memory: 364k freed
[    9.316624] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.679699] AppArmor: AppArmor initialized<5>audit(1201553389.060:2):  type=1505 info="AppArmor initialized" pid=1193
[   10.693578] fuse init (API version 7.8)
[   10.702630] Failure registering capabilities with primary security module.
[   10.722881] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   10.722889] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.726697] ACPI: Thermal Zone [THM] (40 C)
[   11.800621] usbcore: registered new interface driver usbfs
[   11.800673] usbcore: registered new interface driver hub
[   11.800739] usbcore: registered new device driver usb
[   11.801946] USB Universal Host Controller Interface driver v3.0
[   11.802054] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.802072] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.802076] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.802325] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.802360] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[   11.802590] usb usb1: configuration #1 chosen from 1 choice
[   11.802641] hub 1-0:1.0: USB hub found
[   11.802656] hub 1-0:1.0: 2 ports detected
[   11.903627] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   11.903634] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   11.903651] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.903655] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.903713] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.903742] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[   11.903925] usb usb2: configuration #1 chosen from 1 choice
[   11.903976] hub 2-0:1.0: USB hub found
[   11.903991] hub 2-0:1.0: 2 ports detected
[   11.920406] SCSI subsystem initialized
[   11.968858] libata version 2.21 loaded.
[   12.007592] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   12.007599] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.007616] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.007621] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.007690] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.007720] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[   12.007887] usb usb3: configuration #1 chosen from 1 choice
[   12.007935] hub 3-0:1.0: USB hub found
[   12.007953] hub 3-0:1.0: 2 ports detected
[   12.116388] ata_piix 0000:00:1f.1: version 2.11
[   12.116408] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   12.116421] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.116476] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.116635] scsi0 : ata_piix
[   12.116738] scsi1 : ata_piix
[   12.116938] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[   12.116943] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.872000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.876000] Time: acpi_pm clocksource has been installed.
[    4.932000] ata1.00: ATAPI: QSI CD-RW/DVD-ROM SBW242U, UD25, max UDMA/33
[    5.104000] ata1.00: configured for UDMA/33
[    5.268000] ata2.00: ATA-6: IC25N030ATMR04-0, MOAOAD0A, max UDMA/100
[    5.268000] ata2.00: 58605120 sectors, multi 8: LBA48 
[    5.284000] ata2.00: configured for UDMA/100
[    5.288000] scsi 0:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242U UD25 PQ: 0 ANSI: 5
[    5.288000] scsi 1:0:0:0: Direct-Access     ATA      IC25N030ATMR04-0 MOAO PQ: 0 ANSI: 5
[    5.288000] b44.c:v1.01 (Jun 16, 2006)
[    5.288000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    5.292000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0f:1f:26:00:5a
[    5.292000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    5.292000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    5.292000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.292000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.296000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    5.296000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.296000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    5.296000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf6effc00
[    5.300000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.300000] usb usb4: configuration #1 chosen from 1 choice
[    5.300000] hub 4-0:1.0: USB hub found
[    5.300000] hub 4-0:1.0: 6 ports detected
[    5.332000] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    5.332000] Uniform CD-ROM driver Revision: 3.20
[    5.332000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.340000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.340000] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    5.360000] sd 1:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    5.360000] sd 1:0:0:0: [sda] Write Protect is off
[    5.360000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.360000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.360000] sd 1:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    5.360000] sd 1:0:0:0: [sda] Write Protect is off
[    5.360000] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.360000] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.360000]  sda: sda1 sda2
[    5.408000] sd 1:0:0:0: [sda] Attached SCSI disk
[    5.732000] Attempting manual resume
[    5.732000] swsusp: Resume From Partition 8:1
[    5.732000] PM: Checking swsusp image.
[    5.736000] PM: Resume from disk failed.
[    5.760000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.760000] EXT3-fs: write access will be enabled during recovery.
[    7.848000] kjournald starting.  Commit interval 5 seconds
[    7.848000] EXT3-fs: recovery complete.
[    7.848000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.484000] NET: Registered protocol family 17
[   20.056000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.084000] agpgart: Detected an Intel 855GM Chipset.
[   20.084000] agpgart: Detected 892K stolen memory.
[   20.096000] agpgart: AGP aperture is 128M @ 0xe8000000
[   20.116000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.164000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.200000] intel_rng: FWH not detected
[   20.252000] iTCO_vendor_support: vendor-support=0
[   20.252000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   20.252000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
[   20.252000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.732000] ieee80211_crypt: registered algorithm 'NULL'
[   20.780000] Yenta: CardBus bridge found at 0000:02:04.0 [1028:017f]
[   20.780000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.780000] Yenta: Routing CardBus interrupts to PCI
[   20.780000] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
[   21.012000] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   21.012000] Socket status: 30000007
[   21.012000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   21.012000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   21.012000] cs: IO port probe 0xd000-0xefff: clean.
[   21.012000] pcmcia: parent PCI bridge Memory window: 0xf8000000 - 0xfdffffff
[   21.012000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   21.360000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.360000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.420000] input: PC Speaker as /class/input/input2
[   21.532000] bcm43xx driver
[   21.532000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.832000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   21.832000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.888000] cs: IO port probe 0x100-0x3af: clean.
[   21.892000] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.892000] cs: IO port probe 0x820-0x8ff: clean.
[   21.892000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.892000] cs: IO port probe 0xa00-0xaff: clean.
[   22.052000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x256eb1, caps: 0x804713/0x0
[   22.092000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   22.660000] intel8x0_measure_ac97_clock: measured 55326 usecs
[   22.660000] intel8x0: clocking to 48000
[   23.484000] lp: driver loaded but no devices found
[   23.564000] Adding 996020k swap on /dev/sda1.  Priority:-1 extents:1 across:996020k
[   24.000000] EXT3 FS on sda2, internal journal
[   25.548000] ACPI: AC Adapter [AC] (off-line)
[   25.596000] No dock devices found.
[   25.908000] ACPI: Battery Slot [BAT0] (battery present)
[   25.932000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.932000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   26.000000] input: Lid Switch as /class/input/input4
[   26.004000] ACPI: Lid Switch [LID]
[   26.048000] input: Power Button (CM) as /class/input/input5
[   26.052000] ACPI: Power Button (CM) [PBTN]
[   26.096000] input: Sleep Button (CM) as /class/input/input6
[   26.100000] ACPI: Sleep Button (CM) [SBTN]
[   26.496000] ACPI: Invalid _PSS data: freq is zero
[   27.832000] ppdev: user-space parallel port driver
[   28.136000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   28.292000] audit(1201553414.627:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4581 profile="/usr/sbin/cupsd"
[   28.436000] apm: BIOS not found.
[   28.816000] Failure registering capabilities with primary security module.
[   29.300000] Bluetooth: Core ver 2.11
[   29.300000] NET: Registered protocol family 31
[   29.300000] Bluetooth: HCI device and connection manager initialized
[   29.300000] Bluetooth: HCI socket layer initialized
[   29.348000] Bluetooth: L2CAP ver 2.8
[   29.348000] Bluetooth: L2CAP socket layer initialized
[   29.436000] Bluetooth: RFCOMM socket layer initialized
[   29.436000] Bluetooth: RFCOMM TTY layer initialized
[   29.436000] Bluetooth: RFCOMM ver 1.8
[   30.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   32.512000] [drm] Initialized drm 1.1.0 20060810
[   32.516000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   32.520000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   32.524000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   52.336000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   62.972000] NET: Registered protocol family 10
[   62.972000] lo: Disabled Privacy Extensions
[   62.972000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.452000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   96.516000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  118.572000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  140.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  162.704000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  284.820000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  406.880000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  528.940000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  622.324000] end_request: I/O error, dev sr0, sector 52392
[  622.324000] Buffer I/O error on device sr0, logical block 6549
[  622.480000] end_request: I/O error, dev sr0, sector 52392
[  622.480000] Buffer I/O error on device sr0, logical block 6549
[  622.628000] end_request: I/O error, dev sr0, sector 52408
[  622.628000] Buffer I/O error on device sr0, logical block 6551
[  622.784000] end_request: I/O error, dev sr0, sector 52408
[  622.784000] Buffer I/O error on device sr0, logical block 6551
[  622.972000] end_request: I/O error, dev sr0, sector 52408
[  622.972000] Buffer I/O error on device sr0, logical block 6551
[  623.128000] end_request: I/O error, dev sr0, sector 52408
[  623.128000] Buffer I/O error on device sr0, logical block 6551
[  623.284000] end_request: I/O error, dev sr0, sector 52408
[  623.284000] Buffer I/O error on device sr0, logical block 6551
[  623.476000] end_request: I/O error, dev sr0, sector 52408
[  623.476000] Buffer I/O error on device sr0, logical block 6551
[  623.628000] end_request: I/O error, dev sr0, sector 52408
[  623.628000] Buffer I/O error on device sr0, logical block 6551
[  623.784000] end_request: I/O error, dev sr0, sector 52408
[  623.784000] Buffer I/O error on device sr0, logical block 6551
[  624.272000] UDF-fs: No VRS found
[  624.300000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  624.312000] ISOFS: changing to secondary root
[  651.000000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  773.084000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  895.232000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1017.312000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1139.380000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1261.436000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1383.508000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1505.640000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1627.700000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1749.776000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```


Bootup.txt:
```

 A modem device/card may be disabled at bootup, due to a variety of causes.
 Look at the bootup diagnostics record dmesg.txt  written out through:
 $ dmesg > dmesg.txt
 and try to garner some understanding from it.  Possibilities therein are too
 diverse to be automagically processed by scanModem. A line including the PCI
 bus slot 00:1f.6 of your modem, and "disable" or "disabling" predicts problems,
 though sometimes corrected later in the bootup.  Similarly a line with "@"
 in the interrupt (IRQ) for your 00:1f.6 slot is predictive of problems. 

 Possible corrections are:
 0) Get unloading.gz from http://phep2.technion.ac.il/linmodems/packages/
 This script unloads excess drivers which may be competing for resources. 
 Before trying to set up the modem, do:
 $ gunzip unloading.gz
 $ chmod +x unloading
 $ su - root 
 # ./unloading
 Or for Ubuntu related Distros
 $ sudo ./unloading
 
 1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
 Instructions for accessing BIOS are at:
 http://linmodems.technion.ac.il/resources.html within:  Additional Resourcces.
 2a) Add an option "pci=routeirq" to the kernel boot up line.
 Here is an example paragraph from  /boot/grub/menu.lst :
       title           Ubuntu, kernel 2.6.15-26-686
       root            (hd0,6)
       kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
       initrd          /boot/initrd.img-2.6.15-26-686
       savedefault
 2b) Same as above, but use "pollirq" instead of "pci=routeirq".
 3) Within some BIOS setups, IRQ assignments can be changed.
 4) On non-laptop systems, moving the modem card to another slot has helped.
 5) Sometimes upgrading the kernel solves the problem.
 6) Sometimes downgrading the kernel solves the problem.
 7) Sometimes changing the Linux distribution solves the problem.

```

---

