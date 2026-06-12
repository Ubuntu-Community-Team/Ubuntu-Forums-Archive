---
title: "installing an ISA 3com etherlink III Nic"
date: 2005-02-23
forum: Hardware &amp; Laptops
---

### Post by nook on 2005-02-23
I've searched the forums and couldn't find anything about installing a ISA NIC. My motherboard doesnt support my new bought Realtek PCI NIC (old motherboard), so I've to try the 3com etherlink III again.

I'm very new to linux/ubuntu, maybe thats why I don't know how to do it.

Would be great is someone could help me out here :)

---

### Post by Fugee on 2005-06-20
[QUOTE=nook]I've searched the forums and couldn't find anything about installing a ISA NIC. My motherboard doesnt support my new bought Realtek PCI NIC (old motherboard), so I've to try the 3com etherlink III again.

I'm very new to linux/ubuntu, maybe thats why I don't know how to do it.

Would be great is someone could help me out here :)[/QUOTE]
[http://ubuntuforums.org/showpost.php?p=167404&postcount=3](http://ubuntuforums.org/showpost.php?p=167404&postcount=3)

---

### Post by az on 2005-06-20
I have the same card.  The correct module is not loaded by hotplug.

In a terminal try:
sudo modprobe 3c509

If you can then use your ethernet card, add the word "3c509" at the end of the list in /etc/modules.  That loads the module on boot...

sudo gedit /etc/modules


There is a bug report about this and I cannot remember the reason why it cannot be fixed....

---

### Post by john280z on 2005-08-10
Wahoo, the modprobe above works for me also.

Thanks.
johnm

---

### Post by az on 2005-08-10
Wohoo!

---

### Post by greenthumb on 2006-01-04
i have the same card but after the modprobe they cant work.
i can see it only whit ifconfig -a but i cant setting up the interface.
when i do the error was " device or resurce occupy" ( my translation :cool: ) 
sorry for the post and thanks
whit ethtool i cant change the modo from aui to tc but this don't make changes.

---

### Post by az on 2006-01-04
[QUOTE=greenthumb]the error was " device or resurce occupy" ( my translation :cool: ) 
sorry for the post and thanks
.[/QUOTE]

Don't be sorry.  This is why we are here.


What I think is happeneing is that you have a hardware conflict with your card.  Linux does not allocate port addresses and irq's for isa hardware the same way windows does with PnP.  You will need to go into your bios and tell your bios to take those paramenters into control by hand.  It varies with your bios, but perhaps it is just a case of assigning the isa bus proority on the card's irq.  Look in 
lspci
for the irq and port address and try fiddling in your bios for things that look like that.

---

### Post by sup on 2006-01-07
Hi, I also have got problems with this ethernet card that I have been unable to solve so far.
The situation is as follows: I know I have entworking set up correctlz since when I plugin a borrowed ethernet card, I connect out of the scratch. I know the card itself is working properly as it worked on another PCs (and is detected during the bootup bz BIOs - I guess - since it prints out on the screen just before   linux starts coming up).
Dmesg goes as follows:
```
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5
20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 00000000097f0000 (usable)
[4294667.296000]  BIOS-e820: 00000000097f0000 - 00000000097f3000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000097f3000 - 0000000009800000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 151MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 38896

[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 34800 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: RSDP (v000 AWARD                                 ) @ 0x0
0f6b70
[4294667.296000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x30302e31 AWRD 0x00000000) @
0x097f3000
[4294667.296000] ACPI: FADT (v001 AWARD  AWRDACPI 0x30302e31 AWRD 0x00000000) @
0x097f3040
[4294667.296000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000a) @
0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x5008
[4294667.296000] Allocating PCI resources starting at 09800000 (gap: 09800000:f
7f0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01131000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] PM-Timer running at invalid rate: 105% of normal - aborting.
[    0.000000] Detected 333.413 MHz processor.
[   25.107212] Using tsc for high-res timesource
[   25.109524] Console: colour VGA+ 80x25
[   25.113078] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.116450] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   25.179840] Memory: 146052k/155584k available (1415k kernel code, 8888k rese
ved, 763k data, 224k init, 0k highmem)
[   25.179872] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[   25.180314] Calibrating delay loop... 655.36 BogoMIPS (lpj=327680)
[   25.202950] Security Framework v1.0.0 initialized
[   25.203007] SELinux:  Disabled at boot.
[   25.203080] Mount-cache hash table entries: 512
[   25.203962] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00
00000 00000000 00000000 00000000
[   25.204016] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 000
0000 00000000 00000000 00000000
[   25.204079] CPU: L1 I cache: 16K, L1 D cache: 16K

 [   25.204096] CPU: L2 cache: 128K
[   25.204118] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 
0000000 00000000 00000000
[   25.204149] CPU: Intel Celeron (Mendocino) stepping 05
[   25.204176] Enabling fast FPU save and restore... done.
[   25.204212] Checking 'hlt' instruction... OK.
[   25.207783] Checking for popad bug... OK.
[   25.209071] checking if image is initramfs... it is
[   27.874437] Freeing initrd memory: 4791k freed
[   27.886359] ACPI: Looking for DSDT in initrd... not found!
[   28.293860]  not found!
[   28.313509] ACPI: setting ELCR to 0200 (from 0e00)
[   28.510694] NET: Registered protocol family 16
[   28.511125] EISA bus registered
[   28.511162] ACPI: bus type pci registered
[   28.528883] PCI: PCI BIOS revision 2.10 entry at 0xfb370, last bus=1
[   28.528944] PCI: Using configuration type 1
[   28.528969] mtrr: v2.0 (20020519)
[   28.532072] ACPI: Subsystem revision 20050729
[   28.563544] ACPI: Interpreter enabled
[   28.563610] ACPI: Using PIC for interrupt routing
[   28.568149] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.568178] PCI: Probing PCI hardware (bus 00)
[   28.568761] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[   28.568837] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   28.584950] PCI: Ignoring BAR0-3 of IDE controller 0000:00:00.1
[   28.586366] Boot video device is 0000:01:00.0
[   28.593580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.600256] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   28.603462] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   28.605783] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) 
0, disabled.
[   28.608582] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) 
0, disabled.
[   28.611463] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) 
9
[   28.639883] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.640046] pnp: PnP ACPI init
[   28.675460] pnp: PnP ACPI: found 12 devices
[   28.675494] PnPBIOS: Disabled by ACPI PNP
[   28.675850] PCI: Using ACPI for IRQ routing

[   28.675872] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[   28.686341] audit: initializing netlink socket (disabled)
[   28.686458] audit: initialized
[   28.687558] VFS: Disk quotas dquot_6.5.1
[   28.687774] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.688141] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   28.688178] devfs: boot_options: 0x0
[   28.688527] Initializing Cryptographic API
[   28.689878] isapnp: Scanning for PnP cards...
[   28.785054] isapnp: Card '3Com 3C509B EtherLink III'
[   28.785080] isapnp: 1 Plug & Play card detected total
[   29.096048] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 ir
 1,12
[   29.097655] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.097711] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.097744] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharin
 enabled
[   29.098564] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.100097] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.131349] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.132955] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.133788] io scheduler noop registered
[   29.133868] io scheduler anticipatory registered
[   29.133895] io scheduler deadline registered
[   29.133959] io scheduler cfq registered
[   29.137666] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blo
ksize
[   29.139402] EISA: Probing bus 0 at eisa.0
[   29.139490] Cannot allocate resource for EISA slot 4
[   29.139506] Cannot allocate resource for EISA slot 5
[   29.139617] EISA: Detected 0 cards.
[   29.139971] NET: Registered protocol family 2
[   29.148868] IP: routing cache hash table of 1024 buckets, 8Kbytes
[   29.150319] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   29.151767] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   29.152501] TCP: Hash tables configured (established 8192 bind 8192)
[   29.153443] NET: Registered protocol family 8
[   29.153471] NET: Registered protocol family 20
[   29.155454] ACPI wakeup devices: 
[   29.155530] PWRB 
[   29.155616] ACPI: (supports S0 S1 S4bios S5)
[   29.161979] Freeing unused kernel memory: 224k freed
[   29.258564] input: AT Translated Set 2 keyboard on isa0060/serio0
[   29.498827] Capability LSM initialized
[   29.648836] NET: Registered protocol family 1
[   29.756272] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.756484] ide: Assuming 33MHz system bus speed for PIO modes; override wit
 idebus=xx
[   29.756509] ACPI: bus type ide registered
[   29.858138] SIS5513: IDE controller at PCI slot 0000:00:00.1
[   29.858230] ACPI: PCI Interrupt 0000:00:00.1[A]: no GSI - using IRQ 14
[   29.858257] PCI: setting IRQ 14 as level-triggered
[   29.858311] SIS5513: chipset revision 208
[   29.858325] SIS5513: not 100% native mode: will probe irqs later
[   29.858358] SIS5513: SiS620 ATA 66 controller
[   29.858516]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:p
o
[   29.858601]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:D
A
[   29.858675] Probing IDE interface ide0...
[   30.122873] hda: ST32132A, ATA DISK drive
[   30.736040] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.736404] Probing IDE interface ide1...
[   31.408472] hdc: TEAC CD-W552E, ATAPI CD/DVD-ROM drive
[   32.123347] hdd: 40X CD-ROM, ATAPI CD/DVD-ROM drive
[   32.174402] ide1 at 0x170-0x177,0x376 on irq 15
[   32.175764] Probing IDE interface ide2...
[   32.688864] Probing IDE interface ide3...
[   33.202482] Probing IDE interface ide4...
[   33.716108] Probing IDE interface ide5...
[   34.277144] hda: max request size: 128KiB
[   34.277188] hda: 4127760 sectors (2113 MB) w/120KiB Cache, CHS=4095/16/63, D
A
[   34.277224] hda: cache flushes not supported
[   34.277919]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[   35.805968] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[   35.806028] Uniform CD-ROM driver Revision: 3.20
[   35.809018] hdd: ATAPI 40X CD-ROM drive, 128kB Cache

[   42.169728] Attempting manual resume
[   42.176701] swsusp: Suspend partition has wrong signature?
[   42.493585] usbcore: registered new driver usbfs
[   42.494005] usbcore: registered new driver hub
[   42.504280] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driv
r (PCI)
[   42.507915] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   42.507954] PCI: setting IRQ 11 as level-triggered
[   42.507977] ACPI: PCI Interrupt 0000:00:01.2[A] -> Link [LNKE] -> GSI 11 (le
el, low) -> IRQ 11
[   42.508100] ohci_hcd 0000:00:01.2: Silicon Integrated Systems [SiS] USB 1.0 
ontroller
[   42.510080] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus numb
r 1
[   42.510167] ohci_hcd 0000:00:01.2: irq 11, io mem 0xe4900000
[   42.563964] hub 1-0:1.0: USB hub found
[   42.564092] hub 1-0:1.0: 2 ports detected
[   42.698661] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   42.698852] 8139cp: pci dev 0000:00:09.0 (id 10ec:8139 rev 10) is not an 813
C+ compatible chip
[   42.698871] 8139cp: Try the "8139too" driver instead.
[   42.714347] 8139too Fast Ethernet driver 0.9.27
[   42.717890] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   42.717930] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (le
el, low) -> IRQ 11
[   42.719325] eth0: RealTek RTL8139 at 0xd000, 00:0e:2e:31:38:f9, IRQ 11
[   42.719359] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   51.325905] ACPI: CPU0 (power states: C1[C1])
[   51.957302] Attempting manual resume
[   51.991533] swsusp: Suspend partition has wrong signature?
[   52.104196] EXT3-fs: INFO: recovery required on readonly filesystem.
[   52.104245] EXT3-fs: write access will be enabled during recovery.
[   60.028024] kjournald starting.  Commit interval 5 seconds
[   60.028130] EXT3-fs: recovery complete.
[   60.059527] EXT3-fs: mounted filesystem with ordered data mode.
[   64.955629] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   87.051287] Adding 120448k swap on /dev/hda5.  Priority:-1 extents:1
[   88.145481] EXT3 FS on hda1, internal journal
[  122.889116] pnp: Device 01:01.00 activated.
[  122.948486] eth1: 3c5x9 found at 0x220, BNC port, address  00 20 af c0 73 fbIRQ 5.
[  122.948546] 3c509.c:1.19b 08Nov2002 becker@scyld.com
[  122.948556] http://www.scyld.com/network/3c509.html
[  123.312753] parport: PnPBIOS parport detected.
[  123.312902] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  123.506133] lp0: using parport0 (interrupt-driven).
[  123.965775] mice: PS/2 mouse device common for all mice
[  124.928510] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[  127.166444] ts: Compaq touchscreen protocol output
[  132.525410] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@re
hat.com
[  135.823092] cdrom: open failed.
[  135.826354] cdrom: open failed.
[  142.570098] Linux agpgart interface v0.101 (c) Dave Jones
[  142.691800] agpgart: Detected SiS 620 chipset
[  142.825397] agpgart: AGP aperture is 64M @ 0xe0000000
[  145.501199] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module
not inserted.
[  148.136470] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  148.209406] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[  148.209443] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[  152.644642] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[  152.644686] PCI: setting IRQ 10 as level-triggered
[  152.644705] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKB] -> GSI 10 (le
el, low) -> IRQ 10
[  152.686874] gameport: ES1938 is pci0000:00:0c.0/gameport0, io 0xe400, speed 
104kHz
[  162.945630] Real Time Clock Driver v1.12
[  163.714068] input: PC Speaker
[  165.080346] Floppy drive(s): fd0 is 1.44M
[  165.096328] FDC 0 is a post-1991 82077
[  170.365798] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  177.884171] NET: Registered protocol family 10
[  177.885412] Disabled Privacy Extensions on device c02eb280(lo)
[  177.886967] IPv6 over IPv4 tunneling driver
[  183.357686] ACPI: Power Button (FF) [PWRF]
[  183.357831] ACPI: Power Button (CM) [PWRB]
[  184.472182] ibm_acpi: ec object not found
[  188.731952] eth0: no IPv6 routers present
[  213.013072] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  213.013127] apm: overridden by ACPI.

``` this being the relevant part (there miht be somthing else as well so I included the whole of it)
```
[   28.689878] isapnp: Scanning for PnP cards...
[   28.785054] isapnp: Card '3Com 3C509B EtherLink III'
[   28.785080] isapnp: 1 Plug & Play card detected total

```
lspci does not mention this card (onlz the borrowed one via which I am connecting right now)
```
pcilib: Cannot open /sys/bus/pci/devices
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 620 Host (rev 02)
0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b3)
0000:00:01.1 ff00: Silicon Integrated Systems [SiS] ACPI
0000:00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 11)
0000:00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev 2a)

```
Interesting thing happens when I issue sudo modprobe 3c509 (it suppose the other network card is not plugged in)
before it, ifconfig gives this
```
lo        Zapouzd&#345;ení:Místní smy&#269;ka  
          inet adr:127.0.0.1  Maska:255.0.0.0
          inet6-adr: ::1/128 Rozsah:Po&#269;íta&#269;
          AKTIVOVÁNO SMY&#268;KA B&#282;ŽÍ  MTU:16436  Metrika:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```
after, it gives this
```
eth0      Zapouzd&#345;ení:Ethernet  HWadr 00:0E:2E:31:38:F9  
          inet adr:192.168.1.250  Všesm&#283;r:192.168.1.255  Maska:255.255.255.0
          inet6-adr: fe80::20e:2eff:fe31:38f9/64 Rozsah:Linka
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;ŽÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:1829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1819 errors:0 dropped:0 overruns:1 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          RX bytes:1117279 (1.0 MiB)  TX bytes:249800 (243.9 KiB)
          P&#345;erušení:11 Vstupn&#283;/Výstupní port:0xd000 

lo        Zapouzd&#345;ení:Místní smy&#269;ka  
          inet adr:127.0.0.1  Maska:255.0.0.0
          inet6-adr: ::1/128 Rozsah:Po&#269;íta&#269;
          AKTIVOVÁNO SMY&#268;KA B&#282;ŽÍ  MTU:16436  Metrika:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```
however I cannot ping anzthing even then.

---

### Post by sup on 2006-01-07
I actually thing the problem is in BIOS set up but I am kind of awkward there.

I have choices of "PNP OS Installed" no/yes
and "Resources Controlled By" Manual/Auto
if I set it up on manual, 
many entries like "IRQ-3 assigned to" [PCI/ISA PnP]/Legacy ISA"- they differ in IRQ number (ergo there are IRQ-4,IRG-5 etc)
when all is set up to PCI/ISA PnP, the card gets IRQ-5, when I set IRQ-5 to Legacy ISA, the card hets 10 and so on, when I set up all IRQ to Legacy ISA, the system wont boot. actually, I have no idea if I should change anything here:-(

---

### Post by hulk on 2006-01-25
[QUOTE=sup]I actually thing the problem is in BIOS set up but I am kind of awkward there.

I have choices of "PNP OS Installed" no/yes
and "Resources Controlled By" Manual/Auto
if I set it up on manual, 
many entries like "IRQ-3 assigned to" [PCI/ISA PnP]/Legacy ISA"- they differ in IRQ number (ergo there are IRQ-4,IRG-5 etc)
when all is set up to PCI/ISA PnP, the card gets IRQ-5, when I set IRQ-5 to Legacy ISA, the card hets 10 and so on, when I set up all IRQ to Legacy ISA, the system wont boot. actually, I have no idea if I should change anything here:-([/QUOTE]

Try setting IRQ 10 to Legacy ISA.  That's what worked for me.

---

### Post by sup on 2006-01-27
Nothing better, at least it seems so. Which IRQ your card takes by default? 5 as well as mine?

---

### Post by hulk on 2006-01-31
my card takes 10 by default but in bios, I have 5 set to ISA/PNP & 10 set to Legacy ISA.  Maybe try that.  Otherwise, I can't think of anything else.

---

### Post by cvmostert on 2006-02-02
I must say... the modprobe 3c509 helped me allot when i had a 3com modem aswell... wierd that it does not detect it by now... luckaly there is a wonderfull forum like this one to help with all the little hickups!

:-)

---

### Post by misiu_mp on 2008-03-04
Here is what i did on feisty:
- set all IRQ settings to auto in bios
- #modprobe 3c509
- #ifconfig -a           (this should print the info of the device and its name, e. g. eth0)
- #ifconfig eth0 up   (to bring it up)
- #dhclient eth0       (to assign the  ip number and dns)
And it worked! 

Network manager didn't recognize the card, so it couldn't control it, but I still could enjoy full benfits of a 10Mbps link. 

After seting all the IRQs to ISA/PNP, even network manager did pick it up at some point.

---

### Post by oldsoundguy on 2008-03-04
The universal card is the 3com 3C905 series.  It is a 10/100 PCI and every operating system on the planet has the drivers built into it for the card (including Windows 95 OEM).  I have two of them and a D-Link in my 3 Linux boxes just in case the wireless craps out.  I keep one on the bench to add to repair units (regardless of the OS) so I can go onto my broadband and download to fix the units. They install out of the box.
They can be had on eBay for under 10 bucks a lot of the time.

---

### Post by jrusso2 on 2008-03-04
> **oldsoundguy said:**
> The universal card is the 3com 3C905 series.  It is a 10/100 PCI and every operating system on the planet has the drivers built into it for the card (including Windows 95 OEM).  I have two of them and a D-Link in my 3 Linux boxes just in case the wireless craps out.  I keep one on the bench to add to repair units (regardless of the OS) so I can go onto my broadband and download to fix the units. They install out of the box.
They can be had on eBay for under 10 bucks a lot of the time.

The 3C905 series is one of the all time greats,  I used them all the time until the onboard ones started being standard.

Also the old Intel's 5227,8.9's were the same way. Worked with everything even Netware and DOS

---

