---
title: "Ndiswrapper HELP PLEASE!"
date: 2005-12-02
forum: General Help
---

### Post by ihavenoname on 2005-12-02
Hi im runing Ubuntu Breezy Badger and i cant connect to the internet.....I have a Linksys WUSB54g v4 wireless card. I have tried ndiswrapper but im not very good at it. I know it works on ndiswrapper because i have used it on Xandros although Xandros provided a Graphical method of loading ur wireless card (u input the location of the driver and it automatically configures it for you).
 
Im not sure what im doing wrong. I can get the driver install to where when i type " ndiswrapper -l) it shows my driver and next to it states that the hardware is present. However i cannot connect to the internet...i have no clue what to do.  

If anyone could Please help i would be very greatful! Thank you For your time

---

### Post by teaker1s on 2005-12-02
ndisgtk is a GTK based frontend for ndiswrapper, allowing an easy way to
 install Windows wireless drivers.

search and install with synaptic:KS

---

### Post by ihavenoname on 2005-12-02
THANK YOU SOOO ! I WILL TRY THIS! Lets hope it works!

---

### Post by littlepr on 2005-12-02
After installing the drivers through ndiswrapper you have to enable the wifi card/adapter through networking tools.

---

### Post by ihavenoname on 2005-12-03
ok so i used another OS to get ndisgtk. i installed my drivers, now...im sorta stuck...i went to the network config tool but all it has is ethernet and dialup.....wen i type iwconfig it does not say anything about wlan0 but yet ndiswrapper says that my drivers are installed.

---

### Post by littlepr on 2005-12-03
So you brought up networking by going to System->Administration and selected networking but no wireless adapter is showing up, correct? If so open a terminal window and type these commands

dmesg

lspci

ifconfig

, copy them and post the contents here for us to analyze.

Another thing, if your AP is configured with any encryption, disable for now to see if we can get it to work in an open system.

---

### Post by ihavenoname on 2005-12-03
Yes it does not show anything that relates to a wireless connection in the networking box/gui/(w/e it maybe called hehe)

I attached the results to 

dmesg
lspci
ifconfig


i also added

lsusb
iwconfig


i dont know if i have said this before but my card is a USB wireless card not pci.

another thing is that now (after i installed the drivers) the computer when it is loading up the network interfaces blinks out of the normal Ubuntu loader and shows a bunch of commands that it has scrolled thru...it then loads up...
im not sure if that is any help at all i just that i should note that. 

(also since i have no internet on Ubuntu i am having to switch back n forth and to use a memory stick to switch files. if anyone has a quick way of allowing me to mount the windows hard drive (hda1) in Ubuntu it would be great ( I have tried using the Disks option in the system tab it does not work nor does using the mount command in the terminal.) ) this is not as important to me right now as getting the internet up and runing in Ubuntu but i was just wondering if any one had a quick fix for that as it would make this process easier for me.

 thank you very much for all of ur time.

---

### Post by Comrade on 2005-12-03
Check your router's settings through your browser, find the mode, channel, ssid, rate, and WEP key. The channel and rate are usually combined, the mode is something like Ad-Hoc for example, WEP key is a hex number, and ssid is a name that you most likely gave to the connection. If you can't connect to the internet, then get the files in the self-extracting exe mentioned below into your Linux partition somehow. I had the same problem - without ndiswrapper, internet was not working. I had to use the same USB card.
 
 Get ndiswrapper, make install, etc. Get the drivers, as previously stated, from [ftp://ftp.linksys.com/pub/network/WUSB54G_20040903.exe]("ftp://ftp.linksys.com/pub/network/WUSB54G_20040903.exe"). Assuming you are currently on Windows, run the self-extracting archive, and you should see a folder called &quot;Drivers&quot;. Somehow get that folder into your Linux partition (I used USB memory stick). Inside the drivers folder, open the Version 1 folder. Make sure there is a file in there that has an .inf extension. Copy the entire version 1 folder to your Linux partition, and open a terminal. Issue the following commands as root:
 
 
 &lt;home&gt;/driver-version-1-folder/SOMETHING.inf
 /usr/sbin/ndiswrapper -l
 /sbin/modprobe ndiswrapper
 dmesg
 ndiswrapper -m
 
 A detailed description follows.
 
 /usr/sbin/ndiswrapper -i ~/driver-version-1-folder/SOMETHING.inf
 
 This should work.
 
 /usr/sbin/ndiswrapper -l
 
 You should see something about active and hardware detected.
 
 /sbin/modprobe ndiswrapper
 
 This should work.
 
 dmesg
 
 Make sure you see something about ndiswrapper and wusb54g in this one.
 
 ndiswrapper -m
 
Open network-admin. Create a new wireless interface (wlan0), and choose the thing that says ndiswrapper(wlan0). After entering the information, check the automatic dhcp configuration section. For my network, I had to change it to static IP and manually enter my IP, gateway, and subnet mask. But you might not have to. 
 
 I hope this helps!

---

### Post by ihavenoname on 2005-12-03
Hmmm i tried what (Comrade) suggested and once i attemted to modprobe ndiswrapper the terminal seemed to crash, and by that i mean it just shifted down to the next and did not let me input any commands...well i could type them but it had no effect. and i dont think that dmesg ever displayed my wireless card...hmmm

---

### Post by Comrade on 2005-12-03
Could you post the output of dmesg here, please? Then we could figure out if your problem has been solved already.

---

### Post by ihavenoname on 2005-12-03
DMESG
 
viper@ubuntu:~$ dmesg
: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 00000000 0 0000000
[4294667.368000] Intel machine check architecture supported.
[4294667.368000] Intel machine check reporting enabled on CPU#0.
[4294667.368000] CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
[4294667.368000] CPU0: Thermal monitoring enabled
[4294667.368000] CPU: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[4294667.368000] Enabling fast FPU save and restore... done.
[4294667.368000] Enabling unmasked SIMD FPU exception support... done.
[4294667.368000] Checking 'hlt' instruction... OK.
[4294667.372000] checking if image is initramfs... it is
[4294668.133000] Freeing initrd memory: 5149k freed
[4294668.135000] ACPI: Looking for DSDT in initrd... not found!
[4294668.205000] not found!
[4294668.213000] ACPI: setting ELCR to 0200 (from 0820)
[4294668.216000] NET: Registered protocol family 16
[4294668.216000] ACPI: bus type pci registered
[4294668.217000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[4294668.217000] PCI: Using configuration type 1
[4294668.217000] mtrr: v2.0 (20020519)
[4294668.218000] ACPI: Subsystem revision 20050729
[4294668.227000] ACPI: Interpreter enabled
[4294668.227000] ACPI: Using PIC for interrupt routing
[4294668.228000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.228000] PCI: Probing PCI hardware (bus 00)
[4294668.228000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.232000] Uncovering SIS961 that hid as a SIS503 (compatible=1)
[4294668.232000] Enabling SiS 96x SMBus.
[4294668.233000] Boot video device is 0000:01:00.0
[4294668.234000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.240000] ACPI: Power Resource [URP1] (off)
[4294668.240000] ACPI: Power Resource [URP2] (off)
[4294668.240000] ACPI: Power Resource [FDDP] (off)
[4294668.240000] ACPI: Power Resource [LPTP] (off)
[4294668.241000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294668.241000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.242000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.242000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) * 0, disabled.
[4294668.242000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.243000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) * 0, disabled.
[4294668.243000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294668.244000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.244000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.244000] pnp: PnP ACPI init
[4294668.250000] pnp: PnP ACPI: found 12 devices
[4294668.250000] PnPBIOS: Disabled by ACPI PNP
[4294668.250000] PCI: Using ACPI for IRQ routing
[4294668.250000] PCI: If a device doesn't work, try "pci=routeirq". If it helps , post a report
[4294668.264000] audit: initializing netlink socket (disabled)
[4294668.264000] audit: initialized
[4294668.264000] VFS: Disk quotas dquot_6.5.1
[4294668.264000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.264000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.264000] devfs: boot_options: 0x0
[4294668.264000] Initializing Cryptographic API
[4294668.265000] isapnp: Scanning for PnP cards...
[4294668.618000] isapnp: No Plug & Play device found
[4294668.649000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 i rq 1,12
[4294668.655000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.656000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.656000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shari ng enabled
[4294668.656000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.657000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.660000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.660000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.660000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294668.660000] PCI: setting IRQ 11 as level-triggered
[4294668.660000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (l evel, low) -> IRQ 11
[4294668.660000] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[4294668.660000] io scheduler noop registered
[4294668.660000] io scheduler anticipatory registered
[4294668.660000] io scheduler deadline registered
[4294668.660000] io scheduler cfq registered
[4294668.661000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294668.661000] NET: Registered protocol family 2
[4294668.674000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294668.674000] TCP established hash table entries: 32768 (order: 6, 262144 byt es)
[4294668.674000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.675000] TCP: Hash tables configured (established 32768 bind 32768)
[4294668.675000] NET: Registered protocol family 8
[4294668.675000] NET: Registered protocol family 20
[4294668.678000] ACPI wakeup devices:
[4294668.678000] PCI0 PS2M PS2K UAR1 UAR2 USB1 USB2 LAN MDM AUD SLPB
[4294668.678000] ACPI: (supports S0 S1 S4 S5)
[4294668.679000] Freeing unused kernel memory: 168k freed
[4294668.714000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294668.722000] vga16fb: initializing
[4294668.722000] vga16fb: mapped to 0xc00a0000
[4294668.855000] Console: switching to colour frame buffer device 80x30
[4294668.855000] fb0: VGA16 VGA frame buffer device
[4294669.995000] Capability LSM initialized
[4294670.015000] NET: Registered protocol family 1
[4294670.039000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.039000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294670.039000] ACPI: bus type ide registered
[4294670.048000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294670.048000] SIS5513: chipset revision 208
[4294670.048000] SIS5513: not 100% native mode: will probe irqs later
[4294670.048000] SIS5513: SiS 961 MuTIOL IDE UDMA100 controller
[4294670.048000] ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb: DMA
[4294670.048000] ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd: DMA
[4294670.048000] Probing IDE interface ide0...
[4294670.312000] hda: WDC WD800EB-00DJF0, ATA DISK drive
[4294670.567000] hdb: GENERIC GENERIC, ATA DISK drive
[4294670.619000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294670.619000] Probing IDE interface ide1...
[4294671.291000] hdc: HL-DT-ST RW/DVD GCC-4480B, ATAPI CD/DVD-ROM drive
[4294672.005000] hdd: ATAPI CD-RW 52XMax, ATAPI CD/DVD-ROM drive
[4294672.056000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.056000] Probing IDE interface ide2...
[4294672.569000] Probing IDE interface ide3...
[4294673.081000] Probing IDE interface ide4...
[4294673.593000] Probing IDE interface ide5...
[4294674.111000] hda: max request size: 1024KiB
[4294674.127000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/25 5/63, UDMA(33)
[4294674.128000] hda: cache flushes supported
[4294674.129000] /dev/ide/host0/bus0/target0/lun0: p1
[4294674.134000] hdb: max request size: 128KiB
[4294674.139000] hdb: 78198750 sectors (40037 MB) w/2000KiB Cache, CHS=65535/16/ 63, UDMA(33)
[4294674.139000] hdb: cache flushes supported
[4294674.139000] /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
[4294674.170000] hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294674.170000] Uniform CD-ROM driver Revision: 3.20
[4294674.171000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294675.146000] usbcore: registered new driver usbfs
[4294675.146000] usbcore: registered new driver hub
[4294675.148000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Dri ver (PCI)
[4294675.148000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294675.148000] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKE] -> GSI 11 (l evel, low) -> IRQ 11
[4294675.148000] ohci_hcd 0000:00:02.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294675.665000] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus num ber 1
[4294675.665000] ohci_hcd 0000:00:02.2: irq 11, io mem 0xdfffe000
[4294675.718000] hub 1-0:1.0: USB hub found
[4294675.718000] hub 1-0:1.0: 3 ports detected
[4294675.721000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294675.721000] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 11 (l evel, low) -> IRQ 11
[4294675.721000] ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294676.237000] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus num ber 2
[4294676.237000] ohci_hcd 0000:00:02.3: irq 11, io mem 0xdffff000
[4294676.290000] hub 2-0:1.0: USB hub found
[4294676.290000] hub 2-0:1.0: 3 ports detected
[4294676.329000] sis900.c: v1.08.08 Jan. 22 2005
[4294676.330000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[4294676.330000] PCI: setting IRQ 5 as level-triggered
[4294676.330000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKG] -> GSI 5 (le vel, low) -> IRQ 5
[4294676.331000] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
[4294676.344000] 0000:00:03.0: Using transceiver found at address 1 as default
[4294676.345000] eth0: SiS 900 PCI Fast Ethernet at 0xdc00, IRQ 5, 00:07:95:b4:a c:40.
[4294676.418000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[4294678.406000] SCSI subsystem initialized
[4294678.409000] Initializing USB Mass Storage driver...
[4294678.411000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294678.411000] usb-storage: device found at 2
[4294678.411000] usb-storage: waiting for device to settle before scanning
[4294678.411000] usbcore: registered new driver usb-storage
[4294678.411000] USB Mass Storage support registered.
[4294679.425000] ACPI: CPU0 (power states: C1[C1])
[4294679.638000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294679.681000] cdrom: open failed.
[4294679.743000] cdrom: open failed.
[4294679.826000] Attempting manual resume
[4294679.858000] swsusp: Suspend partition has wrong signature?
[4294679.899000] kjournald starting. Commit interval 5 seconds
[4294679.899000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.555000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.416000] Vendor: OTi6828 Model: Flash Disk Rev: 1.89
[4294683.416000] Type: Direct-Access ANSI SCSI revision : 02
[4294683.463000] usb-storage: device scan complete
[4294685.764000] SCSI device sda: 64000 512-byte hdwr sectors (33 MB)
[4294685.771000] sda: Write Protect is off
[4294685.771000] sda: Mode Sense: 03 00 00 00
[4294685.771000] sda: assuming drive cache: write through
[4294685.798000] SCSI device sda: 64000 512-byte hdwr sectors (33 MB)
[4294685.805000] sda: Write Protect is off
[4294685.805000] sda: Mode Sense: 03 00 00 00
[4294685.805000] sda: assuming drive cache: write through
[4294685.805000] /dev/scsi/host0/bus0/target0/lun0: p1
[4294685.817000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294687.484000] Adding 1544184k swap on /dev/mapper/Ubuntu-swap_1. Priority:-1 extents:1
[4294687.819000] EXT3 FS on dm-0, internal journal
[4294696.415000] parport: PnPBIOS parport detected.
[4294696.415000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTA TE,COMPAT,ECP,DMA]
[4294696.507000] lp0: using parport0 (interrupt-driven).
[4294696.549000] mice: PS/2 mouse device common for all mice
[4294696.628000] Linux agpgart interface v0.101 (c) Dave Jones
[4294696.661000] nvidia: module license 'NVIDIA' taints kernel.
[4294696.680000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[4294696.680000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (le vel, low) -> IRQ 5
[4294696.681000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module 1.0-7667 Fri Jun 17 07:01:04 PDT 2005
[4294696.986000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294697.466000] ts: Compaq touchscreen protocol output
[4294701.452000] cdrom: open failed.
[4294701.454000] cdrom: open failed.
[4294702.954000] kjournald starting. Commit interval 5 seconds
[4294702.954000] EXT3 FS on hdb1, internal journal
[4294702.954000] EXT3-fs: mounted filesystem with ordered data mode.
[4294705.090000] agpgart: Detected SiS 650 chipset
[4294705.123000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294705.435000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294705.456000] shpchp: shpc_init : shpc_cap_offset == 0
[4294705.456000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294705.685000] i2c-sis96x version 1.0.0
[4294705.692000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[4294706.462000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294706.462000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKC] -> GSI 11 (l evel, low) -> IRQ 11
[4294708.963000] Real Time Clock Driver v1.12
[4294709.031000] input: PC Speaker
[4294709.451000] Floppy drive(s): fd0 is 1.44M
[4294709.466000] FDC 0 is a post-1991 82077
[4294712.201000] eth0: Media Link Off
[4294712.219000] NET: Registered protocol family 17
[4294779.497000] ACPI: Power Button (FF) [PWRF]
[4294779.497000] ACPI: Power Button (CM) [PWRB]
[4294779.497000] ACPI: Sleep Button (CM) [SLPB]
[4294779.674000] ibm_acpi: ec object not found
[4294785.996000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294785.996000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294785.996000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294787.035000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294787.035000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294787.035000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294791.981000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294791.981000] apm: overridden by ACPI.
[4294795.238000] Bluetooth: Core ver 2.7
[4294795.238000] NET: Registered protocol family 31
[4294795.238000] Bluetooth: HCI device and connection manager initialized
[4294795.238000] Bluetooth: HCI socket layer initialized
[4294795.319000] Bluetooth: L2CAP ver 2.7
[4294795.319000] Bluetooth: L2CAP socket layer initialized
[4294795.352000] Bluetooth: RFCOMM ver 1.5
[4294795.352000] Bluetooth: RFCOMM socket layer initialized
[4294795.352000] Bluetooth: RFCOMM TTY layer initialized
[4294805.247000] NET: Registered protocol family 10
[4294805.247000] Disabled Privacy Extensions on device c031eb40(lo)
[4294805.247000] IPv6 over IPv4 tunneling driver
[4294816.199000] eth0: no IPv6 routers present
[4294817.676000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4295077.977000] usb 1-1: USB disconnect, address 2
[4295081.127000] ohci_hcd 0000:00:02.2: wakeup
[4295082.241000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295083.151000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295084.061000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295084.971000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295085.148000] usb 1-1: new full speed USB device using ohci_hcd and address 7
[4295196.727000] usb 1-1: USB disconnect, address 7
[4295214.476000] ohci_hcd 0000:00:02.2: wakeup
[4295215.741000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295216.651000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295217.561000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295218.471000] hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
[4295218.648000] usb 1-1: new full speed USB device using ohci_hcd and address 1 2
viper@ubuntu:~$

---

### Post by Comrade on 2005-12-03
Yeah, modprobe ndiswrapper didn't work. If it did, there would be something in dmesg about ndiswrapper. I'm assuming you did all the steps I'd mentioned before modprobe. Can you describe what happens when you do modprobe ndiswrapper, more specifically please?

Here's what shows up in my dmesg:
> wlan0: ndiswrapper ethernet device 00:0a:66:71:54:70 using driver wusb54g, configuration file 1915:2234.0.conf
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
NET: Registered protocol family 10


---

### Post by Tsiki on 2005-12-03
Hello, try the trial version of driverloader at [www.driverloader.com](www.driverloader.com), it worked for the Broadcom 54g wireless card in my laptop. It uses win drivers to configure your wifi hardware under Ubuntu.Wish you luck...

---

### Post by Comrade on 2005-12-03
ndiswrapper should do the same. I configured the exact same wireless card on the exact same distro of Linux, so I can't see why you can't do it eventually. We just need to work out the kinks. 

I highly recommend that you avoid non-free software if there is a free alternative. You learn a lot more trying to hack together the solution.

---

### Post by ihavenoname on 2005-12-03
ok, you know how when you are at the command prompt it displays this

"viper@ubuntu:~$"

well when i type modprobe ndiswrapper

"viper@ubuntu:~$ modprobe ndiswrapper"

and hit enter

it takes me to the line under where i typed
 "viper@ubuntu:~$ modprobe ndiswrapper"
as if i had executed a command however it displays no information
and does not return me to the command prompt, which is to say 
i dont get "viper@ubuntu:~$" that back anymore and no matter what command i try to execute it just takes me to the next line.
i think some may describe it as "It crashed my terminal" although it doesnt close it...it simply renders it unusable

Im sry...I hope that made some sense... Im not sure exactly how to describe it....

do you think that perhaps my ndiswrapper is too old?

---

### Post by Comrade on 2005-12-03
What version of ndiswrapper are you trying to compile? Get [the latest version]("http://sourceforge.net/projects/ndiswrapper/"), and compile it. After you've done ./configure and make install, do the steps I listed above, then try modprobe.

---

### Post by ihavenoname on 2005-12-04
I am using the one that Came with Breezy (i installed it via Synaptic(sp?)) I think that may be ver. .8. but i cannot be sure.  also should ndisgtk automatically take care of the modprobe for me or what?


edit: my sn is heye63 on aim i have other SNs on other messengers if anyone finds that easier to use.

also should i get verison 1.6 or 1.7-rc1 for ndiswrapper

---

### Post by ihavenoname on 2005-12-04
Ok wow so it is actually ver 1.1 and I went back and this time i used ver. 2 of the drivers that u posted (ver 1 says hardware not get detected) and i tryed the modprobe again, it worked and did not crash the terminal....here is the new dmesg report.


root@ubuntu:/home/viper# modprobe ndiswrapper
root@ubuntu:/home/viper# dmesg
.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.362000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.364000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.383000] Memory: 510732k/524224k available (1622k kernel code, 12844k reserved, 731k data, 168k init, 0k highmem)
[4294667.383000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.383000] Calibrating delay loop... 3366.91 BogoMIPS (lpj=1683456)
[4294667.405000] Security Framework v1.0.0 initialized
[4294667.405000] SELinux:  Disabled at boot.
[4294667.405000] Mount-cache hash table entries: 512
[4294667.405000] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.405000] CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.405000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.405000] CPU: L2 cache: 256K
[4294667.405000] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 00000000 00000000
[4294667.405000] Intel machine check architecture supported.
[4294667.405000] Intel machine check reporting enabled on CPU#0.
[4294667.405000] CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
[4294667.405000] CPU0: Thermal monitoring enabled
[4294667.405000] CPU: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[4294667.405000] Enabling fast FPU save and restore... done.
[4294667.405000] Enabling unmasked SIMD FPU exception support... done.
[4294667.405000] Checking 'hlt' instruction... OK.
[4294667.409000] checking if image is initramfs... it is
[4294668.170000] Freeing initrd memory: 5149k freed
[4294668.173000] ACPI: Looking for DSDT in initrd... not found!
[4294668.242000]  not found!
[4294668.250000] ACPI: setting ELCR to 0200 (from 0820)
[4294668.253000] NET: Registered protocol family 16
[4294668.253000] ACPI: bus type pci registered
[4294668.255000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[4294668.255000] PCI: Using configuration type 1
[4294668.255000] mtrr: v2.0 (20020519)
[4294668.255000] ACPI: Subsystem revision 20050729
[4294668.264000] ACPI: Interpreter enabled
[4294668.264000] ACPI: Using PIC for interrupt routing
[4294668.265000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.265000] PCI: Probing PCI hardware (bus 00)
[4294668.265000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.269000] Uncovering SIS961 that hid as a SIS503 (compatible=1)
[4294668.269000] Enabling SiS 96x SMBus.
[4294668.270000] Boot video device is 0000:01:00.0
[4294668.271000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.277000] ACPI: Power Resource [URP1] (off)
[4294668.277000] ACPI: Power Resource [URP2] (off)
[4294668.277000] ACPI: Power Resource [FDDP] (off)
[4294668.277000] ACPI: Power Resource [LPTP] (off)
[4294668.278000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294668.279000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.279000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.279000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[4294668.280000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.280000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[4294668.280000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294668.281000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294668.281000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.281000] pnp: PnP ACPI init
[4294668.287000] pnp: PnP ACPI: found 12 devices
[4294668.287000] PnPBIOS: Disabled by ACPI PNP
[4294668.287000] PCI: Using ACPI for IRQ routing
[4294668.287000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.301000] audit: initializing netlink socket (disabled)
[4294668.301000] audit: initialized
[4294668.302000] VFS: Disk quotas dquot_6.5.1
[4294668.302000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.302000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.302000] devfs: boot_options: 0x0
[4294668.302000] Initializing Cryptographic API
[4294668.302000] isapnp: Scanning for PnP cards...
[4294668.656000] isapnp: No Plug & Play device found
[4294668.692000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294668.698000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.699000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.699000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294668.699000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.700000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.703000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.703000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.703000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294668.703000] PCI: setting IRQ 11 as level-triggered
[4294668.703000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294668.703000] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[4294668.703000] io scheduler noop registered
[4294668.703000] io scheduler anticipatory registered
[4294668.703000] io scheduler deadline registered
[4294668.703000] io scheduler cfq registered
[4294668.704000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.704000] NET: Registered protocol family 2
[4294668.717000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294668.717000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294668.718000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.718000] TCP: Hash tables configured (established 32768 bind 32768)
[4294668.718000] NET: Registered protocol family 8
[4294668.718000] NET: Registered protocol family 20
[4294668.720000] ACPI wakeup devices:
[4294668.720000] PCI0 PS2M PS2K UAR1 UAR2 USB1 USB2  LAN  MDM  AUD SLPB
[4294668.720000] ACPI: (supports S0 S1 S4 S5)
[4294668.720000] Freeing unused kernel memory: 168k freed
[4294668.752000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294668.764000] vga16fb: initializing
[4294668.764000] vga16fb: mapped to 0xc00a0000
[4294668.897000] Console: switching to colour frame buffer device 80x30
[4294668.897000] fb0: VGA16 VGA frame buffer device
[4294670.036000] Capability LSM initialized
[4294670.057000] NET: Registered protocol family 1
[4294670.080000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.080000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.080000] ACPI: bus type ide registered
[4294670.090000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294670.090000] SIS5513: chipset revision 208
[4294670.090000] SIS5513: not 100% native mode: will probe irqs later
[4294670.090000] SIS5513: SiS 961 MuTIOL IDE UDMA100 controller
[4294670.090000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[4294670.090000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[4294670.090000] Probing IDE interface ide0...
[4294670.354000] hda: WDC WD800EB-00DJF0, ATA DISK drive
[4294670.609000] hdb: GENERIC GENERIC, ATA DISK drive
[4294670.661000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294670.661000] Probing IDE interface ide1...
[4294671.333000] hdc: HL-DT-ST RW/DVD GCC-4480B, ATAPI CD/DVD-ROM drive
[4294672.047000] hdd: ATAPI CD-RW 52XMax, ATAPI CD/DVD-ROM drive
[4294672.098000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.098000] Probing IDE interface ide2...
[4294672.611000] Probing IDE interface ide3...
[4294673.123000] Probing IDE interface ide4...
[4294673.635000] Probing IDE interface ide5...
[4294674.153000] hda: max request size: 1024KiB
[4294674.170000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
[4294674.171000] hda: cache flushes supported
[4294674.171000]  /dev/ide/host0/bus0/target0/lun0: p1
[4294674.180000] hdb: max request size: 128KiB
[4294674.207000] hdb: 78198750 sectors (40037 MB) w/2000KiB Cache, CHS=65535/16/63, UDMA(33)
[4294674.208000] hdb: cache flushes supported
[4294674.208000]  /dev/ide/host0/bus0/target1/lun0: p1 p2
[4294674.263000] hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294674.263000] Uniform CD-ROM driver Revision: 3.20
[4294674.265000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294675.173000] Attempting manual resume
[4294675.173000] swsusp: Suspend partition has wrong signature?
[4294675.231000] usbcore: registered new driver usbfs
[4294675.231000] usbcore: registered new driver hub
[4294675.233000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294675.233000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294675.233000] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[4294675.233000] ohci_hcd 0000:00:02.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294675.750000] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[4294675.750000] ohci_hcd 0000:00:02.2: irq 11, io mem 0xdfffe000
[4294675.803000] hub 1-0:1.0: USB hub found
[4294675.803000] hub 1-0:1.0: 3 ports detected
[4294675.806000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294675.806000] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[4294675.806000] ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294676.322000] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[4294676.322000] ohci_hcd 0000:00:02.3: irq 11, io mem 0xdffff000
[4294676.375000] hub 2-0:1.0: USB hub found
[4294676.375000] hub 2-0:1.0: 3 ports detected
[4294676.414000] sis900.c: v1.08.08 Jan. 22 2005
[4294676.414000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[4294676.414000] PCI: setting IRQ 5 as level-triggered
[4294676.414000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKG] -> GSI 5 (level, low) -> IRQ 5
[4294676.416000] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
[4294676.429000] 0000:00:03.0: Using transceiver found at address 1 as default
[4294676.430000] eth0: SiS 900 PCI Fast Ethernet at 0xdc00, IRQ 5, 00:07:95:b4:ac:40.
[4294676.503000] usb 1-1: new full speed USB device using ohci_hcd and address 2[4294676.974000] usb 2-1: new full speed USB device using ohci_hcd and address 2[4294678.514000] SCSI subsystem initialized
[4294678.516000] Initializing USB Mass Storage driver...
[4294678.518000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294678.518000] usb-storage: device found at 2
[4294678.518000] usb-storage: waiting for device to settle before scanning
[4294678.518000] usbcore: registered new driver usb-storage
[4294678.518000] USB Mass Storage support registered.
[4294679.511000] ACPI: CPU0 (power states: C1[C1])
[4294679.754000] Attempting manual resume
[4294679.755000] swsusp: Suspend partition has wrong signature?
[4294679.769000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294679.769000] EXT3-fs: write access will be enabled during recovery.
[4294681.093000] kjournald starting.  Commit interval 5 seconds
[4294681.093000] EXT3-fs: recovery complete.
[4294681.102000] EXT3-fs: mounted filesystem with ordered data mode.
[4294683.144000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.524000]   Vendor: OTi6828   Model: Flash Disk        Rev: 1.89
[4294683.524000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294683.585000] usb-storage: device scan complete
[4294683.787000] SCSI device sda: 64000 512-byte hdwr sectors (33 MB)
[4294683.794000] sda: Write Protect is off
[4294683.794000] sda: Mode Sense: 03 00 00 00
[4294683.794000] sda: assuming drive cache: write through
[4294683.846000] SCSI device sda: 64000 512-byte hdwr sectors (33 MB)
[4294683.853000] sda: Write Protect is off
[4294683.853000] sda: Mode Sense: 03 00 00 00
[4294683.853000] sda: assuming drive cache: write through
[4294683.853000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4294683.886000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294688.608000] Adding 522104k swap on /dev/hdb2.  Priority:-1 extents:1
[4294688.977000] EXT3 FS on hdb1, internal journal
[4294698.414000] parport: PnPBIOS parport detected.
[4294698.414000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294698.506000] lp0: using parport0 (interrupt-driven).
[4294698.547000] mice: PS/2 mouse device common for all mice
[4294698.611000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.663000] nvidia: module license 'NVIDIA' taints kernel.
[4294698.699000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[4294698.699000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[4294698.700000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667 Fri Jun 17 07:01:04 PDT 2005
[4294698.959000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294699.526000] ts: Compaq touchscreen protocol output
[4294702.528000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294703.653000] cdrom: open failed.
[4294703.656000] cdrom: open failed.
[4294707.461000] agpgart: Detected SiS 650 chipset
[4294707.480000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294707.637000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294707.657000] shpchp: shpc_init : shpc_cap_offset == 0
[4294707.657000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294707.890000] i2c-sis96x version 1.0.0
[4294707.894000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[4294708.670000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294708.670000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294711.558000] Real Time Clock Driver v1.12
[4294711.631000] input: PC Speaker
[4294712.053000] Floppy drive(s): fd0 is 1.44M
[4294712.068000] FDC 0 is a post-1991 82077
[4294717.000000] ACPI: Power Button (FF) [PWRF]
[4294717.000000] ACPI: Power Button (CM) [PWRB]
[4294717.000000] ACPI: Sleep Button (CM) [SLPB]
[4294717.175000] ibm_acpi: ec object not found
[4294725.528000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294725.528000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294725.528000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294726.465000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294726.465000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294726.465000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294731.531000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294731.531000] apm: overridden by ACPI.
[4294734.059000] Bluetooth: Core ver 2.7
[4294734.059000] NET: Registered protocol family 31
[4294734.059000] Bluetooth: HCI device and connection manager initialized
[4294734.059000] Bluetooth: HCI socket layer initialized
[4294734.126000] Bluetooth: L2CAP ver 2.7
[4294734.126000] Bluetooth: L2CAP socket layer initialized
[4294734.162000] Bluetooth: RFCOMM ver 1.5
[4294734.162000] Bluetooth: RFCOMM socket layer initialized
[4294734.162000] Bluetooth: RFCOMM TTY layer initialized
[4294774.874000] NET: Registered protocol family 10
[4294774.874000] Disabled Privacy Extensions on device c031eb40(lo)
[4294774.874000] IPv6 over IPv4 tunneling driver
[4295059.739000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4295059.797000] usbcore: registered new driver ndiswrapper

edit: smileys again....

---

### Post by ihavenoname on 2005-12-04
also it is still not displaying in the networking area. It doesnt seem to me that it is regiester wlan0 or my drivers all its doing is putting in ndiswrapper....im confused

---

### Post by ihavenoname on 2005-12-05
umm...wow...so has ne one found anything out? i have no clue..it appers modprobe ndiswrapper is loading ndiswrapper but not my drivers. thats all i have found out so if anyone might know y please tell ne...im desprate here:confused: :(

---

### Post by hedone on 2005-12-05
look... i have some problems in history with ndiswrapper... and if u can see your driver with "ndiswrapper -l" than ndisis working... no mather what version do u have...

my problems was:
- some versions of ndiswrapper stucks at modprobe... 
- some versions of ndiswrapper does not create "ndsiwrapper" in modprobe

u can add ndiswrapper to modprobe with gedit... open modprobe and just add it as last line...

and yes... i'm usein' NetworkManager to manage ndiswrapper...  think that it could be good for u to ...

---

### Post by vivekrawal on 2005-12-05
I had same problem. tried to follow what you suggested but I do not get any ADD button in my network-admin. any clues?
Vivek


[QUOTE=Comrade]Open network-admin. Create a new wireless interface (wlan0), and choose the thing that says ndiswrapper(wlan0). After entering the information, check the automatic dhcp configuration section. For my network, I had to change it to static IP and manually enter my IP, gateway, and subnet mask. But you might not have to. 
 
 I hope this helps![/QUOTE]

---

### Post by ihavenoname on 2005-12-05
ya i dont have that button either...i wasnt aware that i had to add it...i thought it would automatically be put in the networking tab. also hedone i think your information might be helpful but do u know wut the modprobe file is called...i was able to locate modprobe.d but i dont know where to add ndiswrapper... also i was able to get it to go to modprobe and not crash when i used a diffrent driver i later found that the driver i was using was not infact a usb driver.....so now we are back to square one...i was however able to install my drivers in a diffrent distro that uses ndiswrapper in a gui (xandros) i noticed that the ndiswrapper version there was actually 1.2rc where as mine is 1.1 so im thinkin that i may need to update but i dont know how to build ndiswrapper...does anyone know if there is a deb file for ndiswrapper?

---

### Post by rsankuratri on 2005-12-05
If you follow the instructions in this link (below)... except you do not have to edit the conf file...
--------------------------------------------------------------
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile

--------------------------------------------------------------
... It should work.  
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset)

Just instead of the broadcom drivers you will be using the drivers that you need for your wireless chipset.

Hope that works.  I have done this atleast three to four times now (on my laptop and my friend's laptop at work) and it works every time... 

Let me know what happened...  We will get you surfing wirelessly... do not worry...

Raj

---

### Post by Comrade on 2005-12-05
Do ndiswrapper -l. What does it say? 

(Sorry for being late - my ndiswrapper went down today, ironically)

---

### Post by ihavenoname on 2005-12-06
Thank You to everyone that has helpped me thus far, i will try those steps and get back to you asap.

---

### Post by ihavenoname on 2005-12-07
ok so i followed the steps....it didnt work, i tried modprobeing it didnt work (im using ndiswrapper 1.1 i have no idea how to install the new version cuz i have no internet connection on ubuntu) so i tried editing the conffile and i didnt know what i was doing and the terminal messed up when i put the files in anyways thou.... when i type ndiswrapper -l it shows my driver "rt2500usb" and then after that it says that both the driver and the hardware are detected. 
also when i modprobe ndiswrapper the terminal still messes up (hence it lets me typer but does not accept commands nor does it display the current folder etc.)

---

### Post by Comrade on 2005-12-07
Make sure that either you are root or you sudo when you modprobe. Like su -c 'modprobe ndiswrapper'.

It would appear that these are the only steps you have left.
> 
 /sbin/modprobe ndiswrapper
 dmesg
 ndiswrapper -m
 Since you said that ndiswrapper -l shows the hardware detected, the hardest part of the problem has been overcome. Now, you need to get some information about your network, so that you can configure your network properly when the time comes.[LIST]
[*]ESSID (like the network name)
[*]Transfer Rate
[*]WEP key
[*]Subnet mask
[*]Gateway address
[*]Static IP Address
[*]DNS servers[/LIST]EDIT: If your terminal "messes up", try doing C-c, or whatever the Break control combination is on your system.

---

### Post by ihavenoname on 2005-12-09
umm well yes i was in root. the -c function did not  work.. how would i find out what the break control combo is?? (sry im really new to all the linux functions)

---

### Post by Comrade on 2005-12-09
Try Control-C (C-c), C-d, C-z, and, if all else fails, just go through the alphabet. Normally it's either C-c, C-d, or C-z. 

Give us the output of this command: ```
dmesg | grep ndis
```

---

### Post by ihavenoname on 2005-12-10
well...i installed fedora core 4 the other day and i got my card working with ndiswrapepr 1.7 (i had to compile it) using some of  the info that alot of people gave me on this website, so thank you to all. Hmm from that experience i learned that apparently i cant build source codes on Ubuntu...i dont have the build file in the /libs/modules/kernel folder (im not sure of the exact location but i know that when i tried to build ndiswrapper it told me it couldnt find something in that area.) Hmm....i dunno what do u guy think? is there anyway i could get that fix or should i just stick to FC4? Thank You btw to all those who have been helping me thus far you have no idea how much i apprechiate (sp?) your help!:D

---

### Post by Comrade on 2005-12-10
The process that you used on FC4 should be replicable on Ubuntu, besides the configuration of the ndiswrapper(wlan0) itself. On FC, I believe it is system-config-network, whereas on Ubuntu it is network-admin. That's the only difference.

What exactly worked in Fedora Core that did not work under Ubuntu? You can stick with FC if you want.

---

### Post by ihavenoname on 2005-12-10
[QUOTE=Comrade]The process that you used on FC4 should be replicable on Ubuntu, besides the configuration of the ndiswrapper(wlan0) itself. On FC, I believe it is system-config-network, whereas on Ubuntu it is network-admin. That's the only difference.

What exactly worked in Fedora Core that did not work under Ubuntu? You can stick with FC if you want.[/QUOTE]


the "make" and "make install" commands worked in FC Ubuntu would not let me build it said it could not find a file (something to do with the kernel and a folder called build) also the modprobe worked in FC where as it did not in Ubuntu. My problem with FC is that it takes alot more to configure (with reguards to mp3s as well as the nvidia drivers)

---

### Post by ihavenoname on 2005-12-13
WHOOOOOOOOOOO HOOOOOOOOOOOOOOOOOOOOOOOOOO MY UBUNTU WIRELESS IS IN BUSSNIESS!!! IM USING IT RIGHT NOW!!!!!!!!!!! YAH!!!!!!!!!!!!!!!!!!!!!!! THANK YOU ALL SOOOO MUCH FOR YOU HELP!!! YOUR INFORMATION WAS RIGHT ON THE MONEY!!!! 

and for those of u who have the same problem heres what i did, 

in the terminal i typed 

apt-get install debhelper build-essential fakeroot linux-headers-$(uname -r)


i then used synaptic to install gcc 3.4 and automake 1.9  

then i complied a deb file from the ndiswrapper tar with make deb 

then i typed this in to the terminal 

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper


then i used dpkg to install the both ndiswrapper utils and modulis also ndisgtk (it only worked when i used ndisgtk for some reason)

i then used ndisgtk to install my drivers

i went in to the terminal and typed modprobe ndiswrapper
i checked the networking section found wlan0 listed there so i jumped up and began to dance and then i typed ndiswrapper -m and wala! 

so aparrently i just had to build it or something...

thank you everyone who posted!! Its you people that really make the open source community worth while and you guys are why ubuntu has gotten this far! If Linux does eventually take Windoze down it will be larglely due to communties like this thank you sooo much!!! I know it must have been hard having to deal with my incompentence in linux!  and if anyone needs my help in anything or has ne questions about what i did feel free to ask i would be more then happy to help!

---

