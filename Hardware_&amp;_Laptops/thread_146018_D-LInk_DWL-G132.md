---
title: "D-LInk DWL-G132"
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by eaterb on 2006-03-17
I am new to Linux and Ubuntu...I installed the operating system last night and purchased the new D-Link DWL-G132.  

The software cd that came with the USB card states that the software should be installed first before the card is plugged in.  I did find information in a few other threads relating to what needs to be done to have the system recognize the software, etc, but wanted to check here first before I just plug it in without first installing Windows Software.

Any thoughts?

SOrry if this is confusing.

---

### Post by sailor2001 on 2006-03-18
I understand you don't need to attempt to install from disk.... BUT you do have to find the chip set for that card at lists.ndiswrapper and install that to your desktop.........
code:
cd Desktop
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i NET8180.INF
sudo ndiswrapper -l
sudo dhclient

during that process the comments are #can't locate driver.or something like that...but it works

---

### Post by eaterb on 2006-04-08
I still have not been able to get my D-Link Card working.  It is a bit frustrating.  Can someone look over the Kernel Messages below and let me know if there are any issues that need to be addressed?  Thanks,

Brett


00 - 0000000017ee06c0 (usable)
[4294667.296000]  BIOS-e820: 0000000017ee06c0 - 0000000017ee66c0 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000017ee66c0 - 0000000017eee700 (ACPI NVS)
[4294667.296000]  BIOS-e820: 0000000017eee700 - 0000000018000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 382MB LOWMEM available.
[4294667.296000] found SMP MP-table at 0009fe00
[4294667.296000] On node 0 totalpages: 98016
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 93920 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 IBM                                   ) @ 0x000fdfe0
[4294667.296000] ACPI: RSDT (v001 IBM    CDTPWSPI 0x00001010 IBM  0x00000000) @ 0x17ee6640
[4294667.296000] ACPI: FADT (v001 IBM    CDTPWSPI 0x00001010 IBM  0x00000000) @ 0x17ee65c0
[4294667.296000] ACPI: MADT (v001 IBM    CDTPWSPI 0x00001010 IBM  0x00000000) @ 0x17ee6540
[4294667.296000] ACPI: DSDT (v001 IBM    CDTPWSPI 0x00001000 MSFT 0x01000007) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0xf808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:8 APIC version 17
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 18000000 (gap: 18000000:e6c00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/mapper/Ubuntu-root ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 930.391 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294671.192000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.193000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.230000] Memory: 380164k/392064k available (1416k kernel code, 11328k reserved, 762k data, 224k init, 0k highmem)
[4294671.230000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294671.230000] Calibrating delay loop... 1847.29 BogoMIPS (lpj=923648)
[4294671.252000] Security Framework v1.0.0 initialized
[4294671.252000] SELinux:  Disabled at boot.
[4294671.252000] Mount-cache hash table entries: 512
[4294671.252000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294671.252000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294671.252000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294671.252000] CPU: L2 cache: 256K
[4294671.252000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[4294671.252000] CPU: Intel Pentium III (Coppermine) stepping 06
[4294671.252000] Enabling fast FPU save and restore... done.
[4294671.252000] Enabling unmasked SIMD FPU exception support... done.
[4294671.252000] Checking 'hlt' instruction... OK.
[4294671.256000] Checking for popad bug... OK.
[4294671.256000] checking if image is initramfs... it is
[4294672.144000] Freeing initrd memory: 5172k freed
[4294672.146000] ACPI: Looking for DSDT in initrd... not found!
[4294672.282000]  not found!
[4294672.429000] ENABLING IO-APIC IRQs
[4294672.429000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294672.541000] NET: Registered protocol family 16
[4294672.541000] EISA bus registered
[4294672.541000] ACPI: bus type pci registered
[4294672.543000] PCI: PCI BIOS revision 2.10 entry at 0xfd55c, last bus=1
[4294672.543000] PCI: Using configuration type 1
[4294672.543000] mtrr: v2.0 (20020519)
[4294672.544000] ACPI: Subsystem revision 20050729
[4294672.557000] ACPI: Interpreter enabled
[4294672.557000] ACPI: Using IOAPIC for interrupt routing
[4294672.558000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294672.558000] PCI: Probing PCI hardware (bus 00)
[4294672.558000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294672.558000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294672.561000] Boot video device is 0000:00:02.0
[4294672.562000] PCI: Transparent bridge - 0000:00:1e.0
[4294672.574000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294672.575000] ACPI: PCI Interrupt Link [PIN1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.576000] ACPI: PCI Interrupt Link [PIN2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.576000] ACPI: PCI Interrupt Link [PIN3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.577000] ACPI: PCI Interrupt Link [PIN4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.577000] ACPI: PCI Interrupt Link [PIN5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.578000] ACPI: PCI Interrupt Link [PIN6] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.579000] ACPI: PCI Interrupt Link [PIN7] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.579000] ACPI: PCI Interrupt Link [PIN8] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294672.585000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[4294672.586000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294672.586000] pnp: PnP ACPI init
[4294672.592000] pnp: PnP ACPI: found 15 devices
[4294672.592000] PnPBIOS: Disabled by ACPI PNP
[4294672.593000] PCI: Using ACPI for IRQ routing
[4294672.593000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294672.599000] pnp: 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[4294672.599000] pnp: 00:0b: ioport range 0x800-0x87f has been reserved
[4294672.599000] pnp: 00:0b: ioport range 0xf800-0xf87f could not be reserved
[4294672.599000] pnp: 00:0b: ioport range 0xfc00-0xfc3f has been reserved
[4294672.600000] audit: initializing netlink socket (disabled)
[4294672.600000] audit: initialized
[4294672.600000] VFS: Disk quotas dquot_6.5.1
[4294672.600000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.600000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294672.600000] devfs: boot_options: 0x0
[4294672.600000] Initializing Cryptographic API
[4294672.600000] isapnp: Scanning for PnP cards...
[4294672.954000] isapnp: No Plug & Play device found
[4294672.987000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294672.988000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.988000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.988000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.988000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.988000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.992000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.992000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.993000] io scheduler noop registered
[4294672.993000] io scheduler anticipatory registered
[4294672.993000] io scheduler deadline registered
[4294672.993000] io scheduler cfq registered
[4294672.993000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.994000] EISA: Probing bus 0 at eisa.0
[4294672.994000] Cannot allocate resource for EISA slot 7
[4294672.994000] EISA: Detected 0 cards.
[4294672.994000] NET: Registered protocol family 2
[4294673.003000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294673.003000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294673.004000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294673.004000] TCP: Hash tables configured (established 16384 bind 16384)
[4294673.004000] NET: Registered protocol family 8
[4294673.004000] NET: Registered protocol family 20
[4294673.004000] ACPI wakeup devices: 
[4294673.004000] PS2K UAR1 UAR2 USB0 PCI2 
[4294673.004000] ACPI: (supports S0 S1 S3 S4 S5)
[4294673.005000] Freeing unused kernel memory: 224k freed
[4294673.037000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.041000] vga16fb: initializing
[4294673.041000] vga16fb: mapped to 0xc00a0000
[4294673.149000] Console: switching to colour frame buffer device 80x30
[4294673.149000] fb0: VGA16 VGA frame buffer device
[4294674.284000] Capability LSM initialized
[4294674.309000] NET: Registered protocol family 1
[4294674.336000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.336000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294674.336000] ACPI: bus type ide registered
[4294674.348000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294674.348000] ICH2: chipset revision 2
[4294674.348000] ICH2: not 100% native mode: will probe irqs later
[4294674.348000]     ide0: BM-DMA at 0xfff0-0xfff7, BIOS settings: hda:DMA, hdb:pio
[4294674.348000]     ide1: BM-DMA at 0xfff8-0xffff, BIOS settings: hdc:DMA, hdd:pio
[4294674.348000] Probing IDE interface ide0...
[4294674.612000] hda: Maxtor 2F020L0, ATA DISK drive
[4294675.224000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.224000] Probing IDE interface ide1...
[4294675.590000] hdc: LTN486S, ATAPI CD/DVD-ROM drive
[4294675.896000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.896000] Probing IDE interface ide2...
[4294676.409000] Probing IDE interface ide3...
[4294676.921000] Probing IDE interface ide4...
[4294677.433000] Probing IDE interface ide5...
[4294677.953000] hda: max request size: 128KiB
[4294679.566000] hda: 40718160 sectors (20847 MB) w/2048KiB Cache, CHS=40395/16/63, UDMA(100)
[4294679.566000] hda: cache flushes supported
[4294679.566000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294679.596000] hdc: ATAPI 48X CD-ROM drive, 120kB Cache
[4294679.596000] Uniform CD-ROM driver Revision: 3.20
[4294680.234000] usbcore: registered new driver usbfs
[4294680.234000] usbcore: registered new driver hub
[4294680.237000] USB Universal Host Controller Interface driver v2.2
[4294680.237000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 19
[4294680.237000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294680.237000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801BA/BAM USB (Hub #1)
[4294680.299000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294680.299000] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000fb00
[4294680.299000] hub 1-0:1.0: USB hub found
[4294680.299000] hub 1-0:1.0: 2 ports detected
[4294680.353000] ACPI: PCI Interrupt 0000:01:0d.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294680.353000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294680.353000] 0000:01:0d.0: 3Com PCI 3c905C Tornado at 0x7800. Vers LK1.1.19
[4294680.374000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294680.374000] 0000:01:0e.0: 3Com PCI 3c905C Tornado at 0x7880. Vers LK1.1.19
[4294680.488000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[4294683.078000] ACPI: CPU0 (power states: C1[C1])
[4294683.078000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294683.224000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294687.666000] cdrom: open failed.
[4294687.823000] Attempting manual resume
[4294687.854000] swsusp: Suspend partition has wrong signature?
[4294687.872000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294687.872000] EXT3-fs: write access will be enabled during recovery.
[4294694.943000] kjournald starting.  Commit interval 5 seconds
[4294694.943000] EXT3-fs: recovery complete.
[4294694.978000] EXT3-fs: mounted filesystem with ordered data mode.
[4294696.331000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294701.412000] Adding 851960k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1
[4294701.714000] EXT3 FS on dm-0, internal journal
[4294709.604000] parport: PnPBIOS parport detected.
[4294709.604000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294709.708000] lp0: using parport0 (interrupt-driven).
[4294709.789000] mice: PS/2 mouse device common for all mice
[4294710.120000] input: PS/2 Generic Mouse on isa0060/serio1
[4294710.709000] ts: Compaq touchscreen protocol output
[4294718.582000] cdrom: open failed.
[4294719.647000] kjournald starting.  Commit interval 5 seconds
[4294719.647000] EXT3 FS on hda1, internal journal
[4294719.647000] EXT3-fs: mounted filesystem with ordered data mode.
[4294721.672000] Linux agpgart interface v0.101 (c) Dave Jones
[4294721.694000] agpgart: Detected an Intel i815 Chipset.
[4294721.720000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294722.217000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294722.231000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294722.231000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294722.407000] hw_random hardware driver 1.0.0 loaded
[4294723.543000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294723.543000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294723.851000] intel8x0_measure_ac97_clock: measured 49743 usecs
[4294723.851000] intel8x0: clocking to 41137
[4294726.216000] Floppy drive(s): fd0 is 1.44M
[4294726.231000] FDC 0 is a post-1991 82077
[4294726.837000] Real Time Clock Driver v1.12
[4294726.949000] input: PC Speaker
[4294728.495000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294728.520000] NET: Registered protocol family 17
[4294795.066000] ACPI: Power Button (FF) [PWRF]
[4294795.066000] ACPI: Power Button (CM) [PWRB]
[4294795.328000] ibm_acpi: ec object not found
[4294809.816000] IBM machine detected. Enabling interrupts during APM calls.
[4294809.816000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294809.816000] apm: overridden by ACPI.
[4294812.775000] Bluetooth: Core ver 2.7
[4294812.775000] NET: Registered protocol family 31
[4294812.775000] Bluetooth: HCI device and connection manager initialized
[4294812.775000] Bluetooth: HCI socket layer initialized
[4294812.810000] Bluetooth: L2CAP ver 2.7
[4294812.811000] Bluetooth: L2CAP socket layer initialized
[4294812.865000] Bluetooth: RFCOMM ver 1.5
[4294812.865000] Bluetooth: RFCOMM socket layer initialized
[4294812.865000] Bluetooth: RFCOMM TTY layer initialized
[4294814.527000] NET: Registered protocol family 10
[4294814.527000] Disabled Privacy Extensions on device c02eb280(lo)
[4294814.528000] IPv6 over IPv4 tunneling driver
[4294824.743000] eth1: no IPv6 routers present
[4294909.302000] usb 1-2: USB disconnect, address 2
[4294915.468000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[4294990.347000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> GSI 22 (level, low) -> IRQ 22
[4295000.735000] eth1: no IPv6 routers present
[4295117.487000] ibm_acpi: ec object not found

---

### Post by Ferrat on 2006-04-10
Im glad to tell you, I just got my DWL-G132 USB WiFi working.. 

[You don't need a internet connection when in Ubuntu for this.]

First of you need to drop breezy and go straight for Dapper Flight6 cause you need the lastest ndiswrapper and other stuff that is just a bother fixing in Brezzy when it's all done for you in Dapper ;) Also you can't update Breezy without internet and Dapper is pretty stable anyway =)
[http://cdimage.ubuntu.com/releases/dapper/flight-6/](http://cdimage.ubuntu.com/releases/dapper/flight-6/)


then you need a few files before we get started 

first you need the latest drivers from d-link.com 
[http://www.dlink.com/products/support.asp?pid=358&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=358&sec=0#drivers)

second of you need ndisgtk_0.6-0ubuntu1_all.deb
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main)

Put both the drivers and the ndisgtk in a folder called wlan under /

Install Dapper straight off no biggy there, now logging in you will notice that the grafics are messed up but that's easy to fix later. 

Now lets get started, go in to synaptic and install ndiswrapper-utils
then open a terminal 

run this
```


$ cd /wlan
$ ndiswrapper -i athfmwdl.inf
$ ndiswrapper -i NetA5AGU.inf


```

This is no trubble you can check that the install is ok, just take the USB out and put it back in then do

```

$ ndiswrapper -l
Installed ndis drivers:
athfmwdl                driver present, hardware present
neta5agu                driver present, hardware present

```

This shows that everything is working. 

the run 

```
 
$ sudo dpkg -i ndisgtk_0.6-0ubuntu1_all.deb 
$ sudo depmod -a
$ sudo modprobe ndiswrapper  

```

Now check System>>Administration>>Networking and you will see wlan0 

if you do, then just activate it and go, for this to load every time you start just runt 

```

$ sudo ndiswrapper -m

```

Happy surfing =)

Still can't see the signal strenght ect. but it works

---

### Post by mrios on 2006-04-11
Is there anything you can do if you don't have an x86 machine? (ndiswrapper will not work on ppc platforms, AFAIK.

Thanks.

---

### Post by eaterb on 2006-04-11
Ferrat,

So I will need to remove the Breezy version that I installed and start over with Dapper?

Thanks,

Brett

---

### Post by Ferrat on 2006-04-12
eaterb, 

Thats what I did, saved me alot of trubble =) 


mrios you could try the generic drivers for linux for the chipset that MadWiFi uses but not 100% sure about the setup there

---

### Post by pek on 2006-05-11
i tried this procedure, but as soon i typed  " # modprobe ndiswrapper " my pc freezed and the next reboot nothing worked (no audio, no mouse, no eth, no X....nothing).

so i had to remove ndiswrapper-utils, delete the alias "ndiswrapper" in /etc/modprobe.d/ and run depmod -a in order to make everything go back to usual.

i'm using an updated dapper, motherboard with an nforce2, usb mouse, radeon 9600xt.

---

### Post by AkuX on 2006-07-24
Gah, when I try this, this happens.

/wlan$ sudo ndiswrapper -i athfmwdl.inf
Installing athfmwdl
$ sudo ndiswrapper -i neta5agu.inf
Installing neta5agu
couldn't copy neta5agu.inf at /usr/sbin/ndiswrapper line 135.
Installed ndis drivers:
athfmwdl        invalid driver!
neta5agu        invalid driver!

Even after I replug in the USB...it says invalid...Help T-T

---

### Post by purplepencil on 2006-09-09
Hi there,

I am just about at my wits end with this thing! I also have the same problem as the poster above, I try to install the .inf files with ndiswrapper, and it says they are already installed, so I run ndiswrapper -l and it lists the two drivers, saying they are BOTH invalid. To add insult to injury I cannot uninstall them either!

This is seriously putting me off linux, since I can't do anything without an internet connection.

Will someone please help?

Thanks,

Dave

---

### Post by mcgarry83 on 2006-09-12
Im having the EXACT same problem all the drivers are installed and all say invalid driver. I followed all the instructions on this and other posts, none of them seem to work. I do have a question though, do you think it makes a difference whether it is plugged into a usb 1.1 or 2.0 port, because my laptop is a 1.1 but the DWL-G132 is a 2.0 device. This works in windows (at the slower speed) but does it also work in Linux the same way.

---

### Post by Ferrat on 2006-09-16
After Dapper 6.06 I've had no trouble installing and using my DWL-132 usb device using ndiswrapper, I just follow the ndisWiki. 

Just don't forget after installing the drivers do the following

```
 
$ ndiswrapper -l 

Installed ndis drivers:
athfmwdl                driver present, hardware present
neta5agu                driver present, hardware present

$ lsusb
Bus 005 Device 005: ID **[COLOR="Red"]2001:3a02[/COLOR]** D-Link Corp. [hex]
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0a5c:3535 Broadcom Corp.
Bus 001 Device 004: ID 0a5c:200a Broadcom Corp.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000

$ ndiswrapper -d 2001:3a02 athfmwdl 
$ ndiswrapper -d 2001:3a02 neta5agu
$ ndiswrapper -m 
$ sudo depmod -a
$ sudo modprobe ndiswrapper 

```
[B][COLOR="Red"]
!!! Even if it says driver present, hardware present, do the following steps anyway !!![/COLOR][/B]

That should kickstart it, if not wait a few min, the restart the computer, one other thing tho, remove the USB device when restarting the first time or it will lock at Configurating Network Devs. 
the just put the DWL-132 in when you see the login screen, and if you doalboot windows or something else you might have to remove the USB every time you boot Ubuntu for the first time after another boot and put it in at the login screen, other than that it works flawless :)

---

### Post by sunexplodes on 2006-10-22
> **Ferrat said:**
> 
run this
```


$ cd /wlan
$ ndiswrapper -i athfmwdl.inf
$ ndiswrapper -i NetA5AGU.inf


```

This is no trubble you can check that the install is ok, just take the USB out and put it back in then do

```

$ ndiswrapper -l
Installed ndis drivers:
athfmwdl                driver present, hardware present
neta5agu                driver present, hardware present

```

This shows that everything is working. 

the run 

```
 
$ sudo dpkg -i ndisgtk_0.6-0ubuntu1_all.deb 
$ sudo depmod -a
$ sudo modprobe ndiswrapper  

```

Now check System>>Administration>>Networking and you will see wlan0 

if you do, then just activate it and go, for this to load every time you start just runt 

```

$ sudo ndiswrapper -m

```

Happy surfing =)

Still can't see the signal strenght ect. but it works

Hey, thanks, this works almost perfectly. 

The only problem I have is with the last step, when I use

sudo ndiswrapper -m, 

it gives me the message: 

modprobe config already contains alias directive


and then when i reboot, the wireless card is missing from the network list. 

any suggestions?

---

### Post by sunexplodes on 2006-10-23
sorry, dumb question. i figured it out.

---

### Post by kallywag on 2007-01-08
could you say how you figured out the bit about it not loading on boot, cuz ive had the same problem. thanks.

---

### Post by sunexplodes on 2007-01-10
Sorry, that was a couple months ago, I'm not really sure what solved that problem. The "modprobe ndiswrapper" and "ndiswrapper -m" lines seem to have done the trick in my most recent installs though.

---

### Post by pavkb on 2007-06-07
When i attempted to install these drivers, i see errors in the system log saying, its a 32bit driver on 64bit kernel.

I am using edubuntu 7.04 AMD64 version & downloaded the *.inf from DLink website.
Any suggestions as to how i can get around this problem.
Thanks

---

### Post by grenaaade on 2007-12-09
Hi,

after following your guide i get:

$ ndiswrapper -l
athfmwdl : driver installed
neta5agu : driver installed
$ sudo dpkg -i ndisgtk_0.6-0ubuntu_all.deb
dpkg: error processing ndisgtk_0.6-0ubuntu_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndisgtk_0.6-0ubuntu_all.deb

help please.

---

