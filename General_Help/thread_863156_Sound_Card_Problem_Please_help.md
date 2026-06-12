---
title: "Sound Card Problem Please help"
date: 2008-07-18
forum: General Help
---

### Post by Uchiha_madara on 2008-07-18
hi ,

i tried to Configure the Sound Card in My Laptop
there is no result the alsamixer is Working but the Sound still Muted , i tried hard to unMute it but there is no result :

i Typed 

> aplay


there is the Reply :

> ALSA lib pcm_dmix.c:975:(snd_pcm_dmix_open) unable to create IPC semaphore
aplay: main:546: audio open error: Permission denied


and I typed this Command , and the Shell sends the Relpy

> nightmare@nightmare-laptop:~$ sudo modprobe snd-atiixp
[sudo] password for nightmare: 
WARNING: /etc/modprobe.d/als-base.save.1 line 1: ignoring bad line starting with 'options'
FATAL: Error inserting snd_atiixp (/lib/modules/2.6.24-19-generic/updates/alsa/pci/snd-atiixp.ko): Invalid argument
nightmare@nightmare-laptop:~$ sudo modprobe snd-atiixp
WARNING: /etc/modprobe.d/als-base.save.1 line 1: ignoring bad line starting with 'options'
FATAL: Error inserting snd_atiixp (/lib/modules/2.6.24-19-generic/updates/alsa/pci/snd-atiixp.ko): Invalid argument



---

### Post by danwood76 on 2008-07-18
It sounds like you've put a bad option in the /etc/modprobe.d/alsa-base file.
That will be why the module isnt loading at least.

Can you post the contents of that file?

To dump it in the terminal do:
```

cat /etc/modprobe.d/alsa-base

```

---

### Post by Uchiha_madara on 2008-07-18
> nightmare@nightmare-laptop:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss


install sound-slot-1 /sbin/modprobe snd-card-1
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-12 snd-pcm-oss

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-atiixp index= mpu_port=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci snd_id="first" mpu_port=0x330 fm_port=0x388
nightmare@nightmare-laptop:~$ 



Thank s a lot, and please help me

---

### Post by danwood76 on 2008-07-18
Its probbaly because there is no index in your options line:
> 
options snd-atiixp index= mpu_port=-2

Setting the index to 0 should allow the module to load as your first sound card.

SO first open the alsa-base config file in gedit as the admin:
```

sudo gedit /etc/modprobe.d/alsa-base

```
then change the line I mentioned above to be:
```

options snd-atiixp index=0 mpu_port=-2

```
That should then allow you to load the module with the following command:
```

sudo modprobe snd-atiixp

```
If that command gives no output it means that the module is loaded and you then need to restart the sound deamons.
Its easier to restart your system to do this as there are quite a few sound deamons that need restarting.

What changes to the sound options did you make to try and fix your sound issue?

---

### Post by Uchiha_madara on 2008-07-18
thanks a lot , I did anything you said , but there is a small bug


when I typed the Order :
> sudo modprobe snd-atiixp


this is the Error : 
> FATAL: Error inserting snd_atiixp (/lib/modules/2.6.24-19-generic/updates/alsa/pci/snd-atiixp.ko): Unknown symbol in module, or unknown parameter (see dmesg)


---

### Post by danwood76 on 2008-07-18
The module may not like the 'mpu_port=-2'

But do as the error says and check demsg.
To dump dmesg just run this in the terminal:
```

dmesg

```
And post the results here.

---

### Post by Uchiha_madara on 2008-07-18
this is the result
:

> 
[   15.209184] Freeing SMP alternatives: 11k freed
[   15.209308] Early unpacking initramfs... done
[   15.587578] ACPI: Core revision 20070126
[   15.587654] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.601489] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[   15.601518] Total of 1 processors activated (3203.83 BogoMIPS).
[   15.601705] ENABLING IO-APIC IRQs
[   15.601904] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.641582] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   15.641635] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   15.641638] ...trying to set up timer as Virtual Wire IRQ... works.
[   15.785796] Brought up 1 CPUs
[   15.785822] CPU0 attaching sched-domain:
[   15.785825]  domain 0: span 01
[   15.785827]   groups: 01
[   15.786010] net_namespace: 64 bytes
[   15.786020] Booting paravirtualized kernel on bare hardware
[   15.786528] Time: 17:51:55  Date: 07/18/08
[   15.786559] NET: Registered protocol family 16
[   15.786768] EISA bus registered
[   15.786799] ACPI: bus type pci registered
[   15.787086] PCI: PCI BIOS revision 2.10 entry at 0xfd6ac, last bus=14
[   15.787088] PCI: Using configuration type 1
[   15.787098] Setting up standard PCI resources
[   15.789610] ACPI: EC: Look up EC in DSDT
[   15.791909] ACPI: Interpreter enabled
[   15.791914] ACPI: (supports S0 S3 S4 S5)
[   15.791928] ACPI: Using IOAPIC for interrupt routing
[   15.792338] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.873292] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   15.873295] ACPI: EC: driver started in interrupt mode
[   15.873338] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.874814] PCI: Transparent bridge - 0000:00:14.4
[   15.874911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.875168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   15.875297] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   15.877194] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   15.877300] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   15.877404] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   15.877507] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   15.877615] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   15.877720] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   15.877823] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   15.877926] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   15.878051] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.878089] pnp: PnP ACPI init
[   15.878097] ACPI: bus type pnp registered
[   15.879764] pnp: PnP ACPI: found 10 devices
[   15.879767] ACPI: ACPI bus type pnp unregistered
[   15.879771] PnPBIOS: Disabled by ACPI PNP
[   15.880009] PCI: Using ACPI for IRQ routing
[   15.880012] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.917598] NET: Registered protocol family 8
[   15.917600] NET: Registered protocol family 20
[   15.917678] AppArmor: AppArmor Filesystem Enabled
[   15.921538] Time: tsc clocksource has been installed.
[   15.929564] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   15.929573] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   15.929577] system 00:08: ioport range 0x200-0x20f has been reserved
[   15.929580] system 00:08: ioport range 0x40b-0x40b has been reserved
[   15.929583] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   15.929586] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   15.929588] system 00:08: ioport range 0x530-0x537 has been reserved
[   15.929591] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   15.929594] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   15.929597] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   15.929600] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   15.929603] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   15.929606] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   15.929609] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   15.929612] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   15.929615] system 00:08: ioport range 0x8000-0x805f could not be reserved
[   15.929618] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   15.929622] system 00:08: ioport range 0x280-0x293 has been reserved
[   15.929624] system 00:08: ioport range 0x87f-0x87f has been reserved
[   15.929631] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   15.929634] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   15.929637] system 00:09: iomem range 0xc0004800-0xc00057ff has been reserved
[   15.929641] system 00:09: iomem range 0x0-0xfff could not be reserved
[   15.960036] PCI: Bridge: 0000:00:01.0
[   15.960039]   IO window: 9000-9fff
[   15.960044]   MEM window: d0100000-d01fffff
[   15.960048]   PREFETCH window: d4000000-d7ffffff
[   15.960060] PCI: Bus 10, cardbus bridge: 0000:09:01.0
[   15.960063]   IO window: 0000a400-0000a4ff
[   15.960069]   IO window: 0000a800-0000a8ff
[   15.960076]   PREFETCH window: 14000000-17ffffff
[   15.960083]   MEM window: 18000000-1bffffff
[   15.960089] PCI: Bridge: 0000:00:14.4
[   15.960093]   IO window: a000-afff
[   15.960100]   MEM window: d0200000-d02fffff
[   15.960106]   PREFETCH window: disabled.
[   15.960154] PCI: Enabling device 0000:09:01.0 (0000 -> 0003)
[   15.960164] ACPI: PCI Interrupt 0000:09:01.0[A] -> GSI 20 (level, low) -> IRQ 16
[   15.960186] NET: Registered protocol family 2
[   15.997504] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   15.997714] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   15.997784] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   15.997874] TCP: Hash tables configured (established 8192 bind 8192)
[   15.997877] TCP reno registered
[   16.009542] checking if image is initramfs... it is
[   16.460712] Switched to high resolution mode on CPU 0
[   16.766319] Freeing initrd memory: 7314k freed
[   16.767108] audit: initializing netlink socket (disabled)
[   16.767132] audit(1216403516.508:1): initialized
[   16.769488] VFS: Disk quotas dquot_6.5.1
[   16.769581] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.769761] io scheduler noop registered
[   16.769764] io scheduler anticipatory registered
[   16.769766] io scheduler deadline registered
[   16.769780] io scheduler cfq registered (default)
[   17.443154] Boot video device is 0000:01:05.0
[   17.443472] isapnp: Scanning for PnP cards...
[   17.797761] isapnp: No Plug & Play device found
[   17.828244] Real Time Clock Driver v1.12ac
[   17.828383] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.829713] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.829797] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.829909] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   17.834003] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.834009] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.834728] mice: PS/2 mouse device common for all mice
[   17.834856] EISA: Probing bus 0 at eisa.0
[   17.834866] Cannot allocate resource for EISA slot 1
[   17.834898] Cannot allocate resource for EISA slot 8
[   17.834900] EISA: Detected 0 cards.
[   17.834904] cpuidle: using governor ladder
[   17.834906] cpuidle: using governor menu
[   17.835026] NET: Registered protocol family 1
[   17.835060] Using IPI No-Shortcut mode
[   17.835108] registered taskstats version 1
[   17.835228]   Magic number: 0:501:896
[   17.835324]   hash matches device ptyy6
[   17.835419] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.835422] EDD information not available.
[   17.835835] Freeing unused kernel memory: 368k freed
[   17.874470] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.060130] fuse init (API version 7.9)
[   19.086122] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.086130] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.086147] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.088939] ACPI: Thermal Zone [THRM] (54 C)
[   19.729357] SCSI subsystem initialized
[   19.811145] usbcore: registered new interface driver usbfs
[   19.811178] usbcore: registered new interface driver hub
[   19.818860] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.818867] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.835367] libata version 3.00 loaded.
[   19.845451] usbcore: registered new device driver usb
[   19.858821] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
[   19.858851] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   19.858865] ATIIXP: not 100% native mode: will probe irqs later
[   19.858870] ATIIXP: IDE port disabled
[   19.858880]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[   19.858894] Probing IDE interface ide1...
[   19.898729] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.923263] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   20.450400] Clocksource tsc unstable (delta = -2833141515 ns)
[   20.454386] Time: acpi_pm clocksource has been installed.
[   20.744735] hdc: TSSTcorpCDW/DVD TS-L462C, ATAPI CD/DVD-ROM drive
[   20.744782] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   20.779106] hdc: UDMA/33 mode selected
[   20.815628] ide1 at 0x170-0x177,0x376 on irq 15
[   20.830119] sata_sil 0000:00:12.0: version 2.3
[   20.830177] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   20.830189] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[   20.830299] scsi0 : sata_sil
[   20.830462] scsi1 : sata_sil
[   20.830725] ata1: SATA max UDMA/100 mmio m512@0xd0004000 tf 0xd0004080 irq 18
[   20.830730] ata2: SATA max UDMA/100 mmio m512@0xd0004000 tf 0xd00040c0 irq 18
[   20.998020] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.004211] ata1.00: ATA-7: FUJITSU MHV2040BH PL, 00000029, max UDMA/100
[   21.004216] ata1.00: 78140160 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   21.005288] ata1.00: configured for UDMA/100
[   21.134260] ata2: SATA link down (SStatus 0 SControl 300)
[   21.134419] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2040B 0000 PQ: 0 ANSI: 5
[   21.137885] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   21.137902] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   21.138404] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   21.138430] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0005000
[   21.170466] usb usb1: configuration #1 chosen from 1 choice
[   21.170496] hub 1-0:1.0: USB hub found
[   21.170509] hub 1-0:1.0: 4 ports detected
[   21.274145] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   21.274166] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   21.274193] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   21.274209] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0006000
[   21.334046] usb usb2: configuration #1 chosen from 1 choice
[   21.334072] hub 2-0:1.0: USB hub found
[   21.334083] hub 2-0:1.0: 4 ports detected
[   21.438151] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   21.438168] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   21.438198] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   21.438256] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0007000
[   21.449758] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.449902] usb usb3: configuration #1 chosen from 1 choice
[   21.449931] hub 3-0:1.0: USB hub found
[   21.449939] hub 3-0:1.0: 8 ports detected
[   21.553817] 8139cp 0000:09:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   21.553825] 8139cp 0000:09:02.0: Try the "8139too" driver instead.
[   21.556963] 8139too Fast Ethernet driver 0.9.28
[   21.557041] ACPI: PCI Interrupt 0000:09:02.0[A] -> GSI 21 (level, low) -> IRQ 20
[   21.558327] eth0: RealTek RTL8139 at 0xa000, 00:16:36:59:7b:96, IRQ 20
[   21.558330] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   21.599545] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache
[   21.599555] Uniform CD-ROM driver Revision: 3.20
[   21.600133] Driver 'sd' needs updating - please use bus_type methods
[   21.600238] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   21.600253] sd 0:0:0:0: [sda] Write Protect is off
[   21.600255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.600273] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.600325] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   21.600335] sd 0:0:0:0: [sda] Write Protect is off
[   21.600338] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.600354] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.600358]  sda: sda1 sda2 < sda5 sda6 > sda3
[   22.033915] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.040778] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.358350] Attempting manual resume
[   22.358355] swsusp: Resume From Partition 8:3
[   22.358357] PM: Checking swsusp image.
[   22.358621] PM: Resume from disk failed.
[   22.396570] kjournald starting.  Commit interval 5 seconds
[   22.396586] EXT3-fs: mounted filesystem with ordered data mode.
[   32.315046] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   32.586485] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.772905] Linux agpgart interface v0.102
[   32.854098] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.996496] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   33.622943] input: Power Button (FF) as /devices/virtual/input/input3
[   33.632709] ACPI: Power Button (FF) [PWRF]
[   33.632930] input: Lid Switch as /devices/virtual/input/input4
[   33.636169] ACPI: Lid Switch [LID]
[   33.636245] input: Power Button (CM) as /devices/virtual/input/input5
[   33.648687] ACPI: Power Button (CM) [PWRB]
[   33.711986] ACPI: AC Adapter [ACAD] (on-line)
[   33.785452] sysfs: duplicate filename 'pcspkr' can not be created
[   33.785459] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   33.785465] Pid: 2786, comm: modprobe Not tainted 2.6.24-19-generic #1
[   33.785479]  [<c01d744f>] sysfs_add_one+0x9f/0xe0
[   33.785495]  [<c01d7988>] create_dir+0x48/0x90
[   33.785502]  [<c01d79f9>] sysfs_create_dir+0x29/0x50
[   33.785507]  [<c021543f>] kobject_get+0xf/0x20
[   33.785513]  [<c0215903>] kobject_add+0x93/0x1b0
[   33.785520]  [<c0215ab1>] kobject_register+0x21/0x50
[   33.785525]  [<c0281fb1>] bus_add_driver+0x71/0x1e0
[   33.785536]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   33.785557]  [<c013f260>] param_get_int+0x0/0x20
[   33.785567]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   33.785576]  =======================
[   33.785581] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
[   33.785587] Pid: 2786, comm: modprobe Not tainted 2.6.24-19-generic #1
[   33.785591]  [<c0215983>] kobject_add+0x113/0x1b0
[   33.785598]  [<c0215ab1>] kobject_register+0x21/0x50
[   33.785603]  [<c0281fb1>] bus_add_driver+0x71/0x1e0
[   33.785610]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   33.785628]  [<c013f260>] param_get_int+0x0/0x20
[   33.785636]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   33.785644]  =======================
[   33.786886] ath_hal: module license 'Proprietary' taints kernel.
[   33.794790] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   33.826966] Yenta: CardBus bridge found at 0000:09:01.0 [1179:ff31]
[   33.827005] Yenta: Using CSCINT to route CSC interrupts to PCI
[   33.827007] Yenta: Routing CardBus interrupts to PCI
[   33.827014] Yenta TI: socket 0000:09:01.0, mfunc 0x00001002, devctl 0x44
[   34.056831] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   34.056838] Socket status: 30000006
[   34.056843] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   34.056846] cs: IO port probe 0xa000-0xafff: clean.
[   34.057165] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   34.183984] ACPI: Battery Slot [BAT1] (battery present)
[   34.437353] wlan: 0.9.4
[   34.670734] ath_pci: 0.9.4
[   34.670826] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 22 (level, low) -> IRQ 18
[   35.359940] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   35.359952] synaptics: Toshiba Satellite L30                     detected, limiting rate to 40pps.
[   35.393910] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   36.154302] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   36.332529] [fglrx] Maximum main memory to use for locked dma buffers: 170 MBytes.
[   36.332576] [fglrx] ASYNCIO init succeed!
[   36.332819] [fglrx] PAT is enabled successfully!
[   36.333448] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   36.405296] snd_atiixp: `' invalid for parameter `index'
[   36.635217] ath_rate_sample: 1.2 (0.9.4)
[   36.636977] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   36.636982] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   36.636992] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   36.636996] wifi0: mac 7.8 phy 4.5 radio 5.6
[   36.637001] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   36.637004] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   36.637006] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   36.637008] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   36.637010] wifi0: Use hw queue 8 for CAB traffic
[   36.637012] wifi0: Use hw queue 9 for beacons
[   36.867832] wifi0: Atheros 5212: mem=0xd0200000, irq=18
[   36.867984] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   36.868066] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1838: chipset global capabilities = 0x4401
[   36.906800] NET: Registered protocol family 10
[   36.907078] lo: Disabled Privacy Extensions
[   36.911342] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:739: codec_mask = 0xb
[   36.913028] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[   36.913462] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3019: autoconfig: line_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   36.913466] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3023:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   36.913470] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3027:    hp_outs=1 (0xe/0x0/0x0/0x0/0x0)
[   36.913480] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3028:    mono: mono_out=0x0
[   36.913483] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:3036:    inputs: mic=0xd, fmic=0x0, line=0x0, fline=0x0, cd=0x0, aux=0x0
[   36.952321] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1108: No slave found for Master Playback Volume
[   36.952337] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1123: Cannot find slave Surround Playback Switch, skipped
[   36.952341] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1123: Cannot find slave Center Playback Switch, skipped
[   36.952345] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1123: Cannot find slave LFE Playback Switch, skipped
[   36.952349] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1123: Cannot find slave Side Playback Switch, skipped
[   36.952354] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1123: Cannot find slave Speaker Playback Switch, skipped
[   36.952358] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1123: Cannot find slave Mono Playback Switch, skipped
[   36.952362] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1123: Cannot find slave IEC958 Playback Switch, skipped
[   37.916610] cs: IO port probe 0x100-0x3af: clean.
[   37.919025] cs: IO port probe 0x3e0-0x4ff: clean.
[   37.920061] cs: IO port probe 0x820-0x8ff: clean.
[   37.920915] cs: IO port probe 0xc00-0xcf7: clean.
[   37.921827] cs: IO port probe 0xa00-0xaff: clean.
[   38.070615] lp: driver loaded but no devices found
[   38.079219] snd_atiixp: `' invalid for parameter `index'
[   38.302472] Adding 522104k swap on /dev/sda3.  Priority:-1 extents:1 across:522104k
[   38.625345] EXT3 FS on sda6, internal journal
[   39.474454] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.888699] No dock devices found.
[   40.811894] apm: BIOS not found.
[   40.990857] ppdev: user-space parallel port driver
[   41.140705] audit(1216392779.081:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4858 profile="/usr/sbin/cupsd" namespace="default"
[   41.994920] Bluetooth: Core ver 2.11
[   41.995658] NET: Registered protocol family 31
[   41.995663] Bluetooth: HCI device and connection manager initialized
[   41.995667] Bluetooth: HCI socket layer initialized
[   42.101882] Bluetooth: L2CAP ver 2.9
[   42.101888] Bluetooth: L2CAP socket layer initialized
[   42.182086] Bluetooth: RFCOMM socket layer initialized
[   42.182342] Bluetooth: RFCOMM TTY layer initialized
[   42.182346] Bluetooth: RFCOMM ver 1.8
[   42.914894] eth0: no IPv6 routers present
[   44.014711] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[   45.803617] [fglrx] GART Table is not in FRAME_BUFFER range 
[   45.803633] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   45.803636] [fglrx] Reserve Block - 1 offset =  0X1ff5000 length = 0Xb000
[   45.987178] [fglrx] interrupt source 10000000 successfully enabled
[   45.987188] [fglrx] enable ID = 0x00000004
[   45.987523] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   50.011397] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[   50.011442] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[   50.038715] hda-intel: Invalid position buffer, using LPIB read method instead.
[   50.678028] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   50.684916] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   54.303862] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x4400, format=0x11
[   54.304258] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   54.310832] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x4400, format=0x11
[   54.311069] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   54.375427] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x4400, format=0x11
[   54.375478] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x11
[   54.382744] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x4400, format=0x11
[   54.382798] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x11
[   55.588310] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   55.592550] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   55.600644] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   55.608480] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   55.612540] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   55.624461] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   56.186829] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x4400, format=0x11
[   56.186883] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   56.190071] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x4400, format=0x11
[   56.190113] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   64.915500] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   64.923268] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   64.931360] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   64.935281] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  110.842710] PPP generic driver version 2.4.2
[  110.934762] NET: Registered protocol family 17
[  111.087544] NET: Registered protocol family 24
[  602.132784] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  602.132844] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  606.055809] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  606.058532] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  617.148951] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  617.149006] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  617.243020] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  617.247341] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  618.070664] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  618.070724] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  618.140285] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  618.144430] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  619.401752] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  619.401803] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  619.552220] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  619.556827] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  631.187193] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  631.187253] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  631.256809] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  631.261191] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  631.607941] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  631.607992] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  631.678231] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  631.682680] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  631.869880] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  631.869935] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  632.023231] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  632.026426] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  678.809829] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  678.809878] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  678.963318] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  678.970431] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  740.058610] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  740.058659] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  740.128711] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  740.129824] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  740.324391] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1307: azx_pcm_prepare: bufsize=0x10000, format=0x31
[  740.324441] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x31
[  740.392849] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[  740.397292] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:725: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[ 2431.248609] snd_atiixp: `' invalid for parameter `index'
[ 2444.998863] snd_atiixp: Unknown parameter `mpu_port'
[ 2742.216549] snd_atiixp: `' invalid for parameter `index'

---

### Post by danwood76 on 2008-07-18
What soundcard is in your system?
There are a lot of errors and warnings relating to alsa which really shouldnt be coming up.

Can your re post your /etc/modprobe.d/alsa-base file so I can see where it is at now.
It seems to still be disliking something.

It might help to remove the mpu_port=-2 as it may not be an option for that module.

---

### Post by Uchiha_madara on 2008-07-18
> /etc/modprobe.d/alsa-base

and this is the result

>   GNU nano 2.0.7                                          File: /etc/modprobe.d/alsa-base                                                                                           

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss


install sound-slot-1 /sbin/modprobe snd-card-1
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-12 snd-pcm-oss

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-atiixp index=0 mpu_port=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci snd_id="first" mpu_port=0x330 fm_port=0x388


the Driver of the Sound Card is   "Realtek High Definition Audio"
,the Motherboard is ATI

---

### Post by danwood76 on 2008-07-18
I would hazzard a guess that the alsa driver mdoule you want is the snd-hda-intel module, not snd-atiixp.
There is a good troubleshooting guide for this in the community docs:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Try just deleting the 'options snd-atiixp index=0 mpu_port=-2' options line in the above config file as its not needed I doubt.

---

### Post by Uchiha_madara on 2008-07-18
so .. what shall i do with the Previous "False" Configuration 

how can I delete it ....

By Reinstalling Ubuntu Hardy or there are anther Skills

or re-configure it without removing the Last Configuration ??


--this is the Last Question ??

---

### Post by danwood76 on 2008-07-18
It depends what steps you have taken in configuration.

With regards to modules options (the thing that usually decideds weather or not you get audio) its just a case of removing the lines you added to the alsa-base config file.

To start with I would remove:
> 
options snd-atiixp index=0 mpu_port=-2

And any others you have added.
I would then try compiling the latest alsa as it says in that guide I linked to and then adding module options as also described.

---

### Post by Uchiha_madara on 2008-07-24
I tried hard with Intel 

I don't Know what is THe Correct Module

snd-hda-intel
or
snd-hda-intel8x0

---

### Post by danwood76 on 2008-07-24
To verify which card you have post the output of the following command:
```

sudo lspci | grep -i 'Audio'

```

---

### Post by jocko on 2008-07-24
[quote=Uchiha_madara]nightmare@nightmare-laptop:~$ sudo modprobe snd-atiixp
[sudo] password for nightmare: 
WARNING: /etc/modprobe.d/[COLOR=Red]als-base.save.1[/COLOR] line 1: ignoring bad line starting with 'options'
FATAL: Error inserting snd_atiixp (/lib/modules/2.6.24-19-generic/updates/alsa/pci/snd-atiixp.ko): Invalid argument
nightmare@nightmare-laptop:~$ sudo modprobe snd-atiixp
WARNING: /etc/modprobe.d/[COLOR=Red]als-base.save.1[/COLOR] line 1: ignoring bad line starting with 'options'
FATAL: Error inserting snd_atiixp (/lib/modules/2.6.24-19-generic/updates/alsa/pci/snd-atiixp.ko): Invalid argument[/quote]

It looks like you have a file called "als-base.save.1" which contains some invalid options. **Delete that file**, it shouldn't be there. You probably made a typo once when you tried to edit the file "als[COLOR=Red]a[/COLOR]-base", so you created a new file, and then you pasted some bad options into it...

So:
```
sudo rm -f /etc/modprobe.d/als-base.save.1
```
Check if you have any more "als-base" files:
```
ls etc/modprobe.d/als-bas*
```and if they exist, remove them also (but do NOT remove als[COLOR=Red]a[/COLOR]-base. It is very important).

---

### Post by Uchiha_madara on 2008-07-24
> 00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


this is The Result of :

> sudo lspci | grep -i 'Audio'


---

