---
title: "usb key mounting issues"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by electroconvulsive on 2006-05-10
I Have an easy disk usb key that I use to transfer files onto my system.

After install it mounted up and a disk symbol showed up on the desktop. But like usual with ubuntu a start later when I plug it in it shows up in the browser but I cannot seem to mount it. Firstly the error message i receive says "[COLOR="Red"]error: given UDI is not a mountable volume[/COLOR]" (well it was on the last startup and nothing has changed since then(*,) ) So I started the hotplug system (using sudo) which incedentally doesnt always seem to want to start at startup, during the start up phase before login it doesnt say OK or fail when starting the hotplug system. I replug my key and whammo still doesnt work. Oh yeah my USB stick is 2.0 and is set up for no disk caching so i dont have to dismount it to pull it out of any systems I plug it into.

I have followed a few of the forums on the subject and havent found a working answer to any of my issues concerning the USB key as yet but I know that posting the output of dmesg may help.

What I would like to see happen is
1. The hotplug system start on startup like its supposed to
2. The USB key automount every time I plug it in (not just the first time after install)
 So if anyone can help with either or both of these issues it would be most appreciated.

But anyway heres the output of dmesg if it will help.

ric@techno-202:~$ dmesg
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000e000000 (usable)
[4294667.296000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 224MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 57344
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 53248 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x00 0fdf50
[4294667.296000]   >>> ERROR: Invalid checksum
[4294667.296000] Allocating PCI resources starting at 0e000000 (gap: 0e000000:f1 e00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/mapper/Ubuntu-root ro quiet spla sh
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (011c1000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 498.883 MHz processor.
[   23.127863] Using tsc for high-res timesource
[   23.129311] Console: colour VGA+ 80x25
[   23.130503] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.131256] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   23.162917] Memory: 219268k/229376k available (1415k kernel code, 9500k reser ved, 763k data, 224k init, 0k highmem)
[   23.162934] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.163147] Calibrating delay loop... 985.08 BogoMIPS (lpj=492544)
[   23.183710] Security Framework v1.0.0 initialized
[   23.183731] SELinux:  Disabled at boot.
[   23.183771] Mount-cache hash table entries: 512
[   23.184085] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 000 00000 00000000 00000000 00000000
[   23.184112] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 0000 0000 00000000 00000000 00000000
[   23.184146] CPU: L1 I cache: 16K, L1 D cache: 16K
[   23.184157] CPU: L2 cache: 512K
[   23.184167] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 0 0000000 00000000 00000000
[   23.184188] CPU: Intel Pentium III (Katmai) stepping 02
[   23.184203] Enabling fast FPU save and restore... done.
[   23.184213] Enabling unmasked SIMD FPU exception support... done.
[   23.184227] Checking 'hlt' instruction... OK.
[   23.187632] Checking for popad bug... OK.
[   23.188157] checking if image is initramfs... it is
[   24.718337] Freeing initrd memory: 4821k freed
[   24.720338] NET: Registered protocol family 16
[   24.720451] EISA bus registered
[   24.735751] PCI: PCI BIOS revision 2.10 entry at 0xfcaee, last bus=1
[   24.735773] PCI: Using configuration type 1
[   24.735786] mtrr: v2.0 (20020519)
[   24.736951] ACPI: Subsystem revision 20050729
[   24.736960] ACPI: Interpreter disabled.
[   24.736973] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.736997] pnp: PnP ACPI: disabled
[   24.737012] PnPBIOS: Scanning system for PnP BIOS support...
[   24.737100] PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
[   24.737115] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe2f4, dseg 0x40
[   24.739481] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   24.739648] PCI: Probing PCI hardware
[   24.739660] PCI: Probing PCI hardware (bus 00)
[   24.740858] Boot video device is 0000:01:00.0
[   24.742358] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   24.745855] pnp: 00:00: ioport range 0x800-0x83f has been reserved
[   24.745870] pnp: 00:00: ioport range 0x850-0x85f has been reserved
[   24.748369] audit: initializing netlink socket (disabled)
[   24.748392] audit: initialized
[   24.748770] VFS: Disk quotas dquot_6.5.1
[   24.748849] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.748963] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   24.748985] devfs: boot_options: 0x0
[   24.749088] Initializing Cryptographic API
[   24.749106] Limiting direct PCI/PCI transfers.
[   24.749405] isapnp: Scanning for PnP cards...
[   25.103295] isapnp: No Plug & Play device found
[   25.192161] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   25.193906] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.194034] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.194051] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing  enabled
[   25.194346] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.194613] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.204346] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.204785] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.205557] io scheduler noop registered
[   25.205600] io scheduler anticipatory registered
[   25.205620] io scheduler deadline registered
[   25.205660] io scheduler cfq registered
[   25.207483] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc ksize
[   25.207876] EISA: Probing bus 0 at eisa.0
[   25.207943] EISA: Detected 0 cards.
[   25.208037] NET: Registered protocol family 2
[   25.217352] IP: routing cache hash table of 2048 buckets, 16Kbytes
[   25.217930] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   25.218304] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   25.218472] TCP: Hash tables configured (established 8192 bind 8192)
[   25.218763] NET: Registered protocol family 8
[   25.218773] NET: Registered protocol family 20
[   25.219905] Freeing unused kernel memory: 224k freed
[   25.245927] input: AT Translated Set 2 keyboard on isa0060/serio0
[   25.281940] vga16fb: initializing
[   25.281954] vga16fb: mapped to 0xc00a0000
[   25.402534] Console: switching to colour frame buffer device 80x30
[   25.402554] fb0: VGA16 VGA frame buffer device
[   26.612672] Capability LSM initialized
[   26.659925] NET: Registered protocol family 1
[   26.709648] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.709682] ide: Assuming 33MHz system bus speed for PIO modes; override with  idebus=xx
[   26.732398] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   26.732439] PIIX4: chipset revision 1
[   26.732448] PIIX4: not 100% native mode: will probe irqs later
[   26.732470]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pi o
[   26.732501]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pi o
[   26.732529] Probing IDE interface ide0...
[   26.996505] hda: FUJITSU MPC3043AT, ATA DISK drive
[   27.609550] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.609713] Probing IDE interface ide1...
[   28.282101] hdc: CRD-8400B, ATAPI CD/DVD-ROM drive
[   28.894785] ide1 at 0x170-0x177,0x376 on irq 15
[   28.895136] Probing IDE interface ide2...
[   29.408368] Probing IDE interface ide3...
[   29.922006] Probing IDE interface ide4...
[   30.435643] Probing IDE interface ide5...
[   30.966156] hda: max request size: 128KiB
[   30.966171] hda: 8448300 sectors (4325 MB), CHS=8940/15/63, UDMA(33)
[   30.966189] hda: cache flushes not supported
[   30.966416]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[   31.009037] hdc: ATAPI 40X CD-ROM drive, 128kB Cache
[   31.009058] Uniform CD-ROM driver Revision: 3.20
[   32.128941] usbcore: registered new driver usbfs
[   32.129061] usbcore: registered new driver hub
[   32.134605] USB Universal Host Controller Interface driver v2.2
[   32.134800] PCI: Found IRQ 11 for device 0000:00:07.2
[   32.134832] PCI: Sharing IRQ 11 with 0000:00:11.0
[   32.134860] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[   32.197237] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus numbe r 1
[   32.197265] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000dce0
[   32.197732] hub 1-0:1.0: USB hub found
[   32.197769] hub 1-0:1.0: 2 ports detected
[   32.322202] PCI: Found IRQ 11 for device 0000:00:11.0
[   32.322227] PCI: Sharing IRQ 11 with 0000:00:07.2
[   32.322249] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.htm](www.scyld.com/network/vortex.htm) l
[   32.322267] 0000:00:11.0: 3Com PCI 3c905B Cyclone 100baseTx at 0xd880. Vers L K1.1.19
[   35.706374] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@red hat.com
[   35.939100] cdrom: open failed.
[   36.224769] Attempting manual resume
[   36.243331] swsusp: Suspend partition has wrong signature?
[   36.327515] kjournald starting.  Commit interval 5 seconds
[   36.327553] EXT3-fs: mounted filesystem with ordered data mode.
[   38.466494] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   45.484485] Adding 200696k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 ex tents:1
[   45.921260] EXT3 FS on dm-0, internal journal
[   64.468064] parport: PnPBIOS parport detected.
[   64.468199] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRI STATE,COMPAT,EPP,ECP]
[   64.570204] lp0: using parport0 (interrupt-driven).
[   64.669361] mice: PS/2 mouse device common for all mice
[   65.189521] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[   66.351291] ts: Compaq touchscreen protocol output
[   70.950987] cdrom: open failed.
[   72.411210] kjournald starting.  Commit interval 5 seconds
[   72.412428] EXT3 FS on hda1, internal journal
[   72.412446] EXT3-fs: mounted filesystem with ordered data mode.
[   74.711411] Linux agpgart interface v0.101 (c) Dave Jones
[   74.740736] agpgart: Detected an Intel 440BX Chipset.
[   74.753743] agpgart: AGP aperture is 64M @ 0xf4000000
[   75.123891] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   75.145642] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[   76.073921] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   76.073961] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   76.830940] Linux video capture interface: v1.00
[   76.919480] PCI: Found IRQ 10 for device 0000:00:0d.0
[   76.919515] PCI: Sharing IRQ 10 with 0000:01:00.0
[   79.403380] gameport: FM801 is pci0000:00:0d.1/gameport0, io 0xdcd0, speed 15 69kHz
[   81.493302] Floppy drive(s): fd0 is 1.44M
[   81.505959] FDC 0 is a National Semiconductor PC87306
[   83.134467] input: PC Speaker
[   83.966657] Real Time Clock Driver v1.12
[   85.484465] PCI: Found IRQ 11 for device 0000:00:11.0
[   85.484493] PCI: Sharing IRQ 11 with 0000:00:07.2
[  112.216142] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  116.983237] Bluetooth: Core ver 2.7
[  116.983266] NET: Registered protocol family 31
[  116.983276] Bluetooth: HCI device and connection manager initialized
[  116.983306] Bluetooth: HCI socket layer initialized
[  117.063209] Bluetooth: L2CAP ver 2.7
[  117.063226] Bluetooth: L2CAP socket layer initialized
[  117.125595] Bluetooth: RFCOMM ver 1.5
[  117.125625] Bluetooth: RFCOMM socket layer initialized
[  117.125656] Bluetooth: RFCOMM TTY layer initialized
[  228.109232] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  228.967573] SCSI subsystem initialized
[  229.015063] Initializing USB Mass Storage driver...
[  229.043533] scsi0 : SCSI emulation for USB Mass Storage devices
[  229.048710] usb-storage: device found at 2
[  229.048725] usb-storage: waiting for device to settle before scanning
[  229.049159] usbcore: registered new driver usb-storage
[  229.049172] USB Mass Storage support registered.
[  234.058681]   Vendor: USB       Model: Flash Disk        Rev: 1100
[  234.058721]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  234.074705] usb-storage: device scan complete
[  234.307900] SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
[  234.310898] sda: Write Protect is off
[  234.310946] sda: Mode Sense: 43 00 00 00
[  234.310956] sda: assuming drive cache: write through
[  234.327920] SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
[  234.330923] sda: Write Protect is off
[  234.330972] sda: Mode Sense: 43 00 00 00
[  234.330982] sda: assuming drive cache: write through
[  234.330996]  /dev/scsi/host0/bus0/target0/lun0: p1
[  234.411447] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[  296.528279] usb 1-1: USB disconnect, address 2
[ 2244.614434] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 2244.719659] scsi1 : SCSI emulation for USB Mass Storage devices
[ 2244.723991] usb-storage: device found at 3
[ 2244.724006] usb-storage: waiting for device to settle before scanning
[ 2249.733865]   Vendor: USB       Model: Flash Disk        Rev: 1100
[ 2249.733904]   Type:   Direct-Access                      ANSI SCSI revision: 00
[ 2249.747850] SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
[ 2249.751866] sda: Write Protect is off
[ 2249.751887] sda: Mode Sense: 43 00 00 00
[ 2249.751897] sda: assuming drive cache: write through
[ 2249.768849] SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
[ 2249.771843] sda: Write Protect is off
[ 2249.771857] sda: Mode Sense: 43 00 00 00
[ 2249.771867] sda: assuming drive cache: write through
[ 2249.771881]  /dev/scsi/host1/bus0/target0/lun0: p1
[ 2249.852120] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
[ 2249.857291] usb-storage: device scan complete
[ 2414.867318] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[ 2431.430562] usb 1-1: USB disconnect, address 3
[ 2432.848279] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 2432.985549] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2432.989782] usb-storage: device found at 4
[ 2432.989796] usb-storage: waiting for device to settle before scanning
[ 2437.999750]   Vendor: USB       Model: Flash Disk        Rev: 1100
[ 2437.999790]   Type:   Direct-Access                      ANSI SCSI revision: 00
[ 2438.014729] SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
[ 2438.018752] sda: Write Protect is off
[ 2438.018772] sda: Mode Sense: 43 00 00 00
[ 2438.018782] sda: assuming drive cache: write through
[ 2438.034734] SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
[ 2438.037699] sda: Write Protect is off
[ 2438.037745] sda: Mode Sense: 43 00 00 00
[ 2438.037755] sda: assuming drive cache: write through
[ 2438.037769]  /dev/scsi/host2/bus0/target0/lun0: p1
[ 2438.117934] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[ 2438.123351] usb-storage: device scan complete

---

### Post by electroconvulsive on 2006-05-13
Yeah 2 days 61 views and no answers. I dont want to sound like too much of a whinger but this problem is really getting to me. Ill see what happens after I finish updating but could anyone please leave me a message and point out the obvious to me just in case im missing it? If anyone has solved this can they please tell me so I can finally have an installation of Ubuntu without any probs because this is the last one for now I hope.

---

### Post by electroconvulsive on 2006-05-14
Weel anyway I have updated my system and now the error message has changed when I try to mount the USB key. 

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And the output is

ric@techno-202:~$        dmesg | tail
[ 1340.013092] VFS: Can't find an ext2 filesystem on dev sda.
[ 1340.128262] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[ 1340.151286] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[ 1340.307689] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[ 1340.308321] SGI XFS Quota Management subsystem
[ 1340.329530] XFS: bad magic number
[ 1340.329550] XFS: SB validate failed
[ 1340.345542] XFS: bad magic number
[ 1340.345560] XFS: SB validate failed
[ 1340.421180] JFS: nTxBlock = 1754, nTxLock = 14033

And to add to this the mountable volume like all others is owned by root.

I hope that this information will help someone help me figure it out.

---

### Post by pellgarlic on 2006-05-14
hi - i'm a bit of a linux beginner too, but i like trying to figure out these things, so i had a look for an answer for you. 

as far as i can tell, the "hot-plugging" facility (being able to mount and unmount usb drives and the like) depends on something called "pmount". 

i have read here: [http://www.ubuntuforums.org/showthread.php?t=85777](http://www.ubuntuforums.org/showthread.php?t=85777) that some people have similar problems to yours, but with floppy drives rather than usb drives. (at least they seem to be getting similar output from dmesg - lots of "connects" follwed by "disconnects"). 

someone on that thread recommended updating pmount from the dapper repositories (which have to be added to your sources.list - read the comment for details) to version 0.9.6-1. i currently have version 0.9.5-0, which came by default as far as i know, and i have had no problems with my 1gb usb flash drive. you could check in synaptic to see what version of pmount you have installed, and if it is less than 0.9.5-0, update it to that. if that doesn't work, or you already have that version, try the dapper version. 

someone else in another thread i read here: [http://www.ubuntuforums.org/archive/index.php/t-80482.html](http://www.ubuntuforums.org/archive/index.php/t-80482.html) says they had the same problem, but if they boot up ubuntu with the flash drive already plugged in, it mounts properly. not an ideal solution, but better than nothing? hope you find a solution :)

p.s. just for a point of reference, here is the output of my dmesg when i plug my usb drive in - to give you a point of comparison, to see where the problem might be occurring:

[4304941.958000] usb 3-6: new high speed USB device using ehci_hcd and address 3
[4304942.129000] scsi1 : SCSI emulation for USB Mass Storage devices
[4304942.131000] usb-storage: device found at 3
[4304942.131000] usb-storage: waiting for device to settle before scanning
[4304947.131000]   Vendor: LG        Model: USB  Drive        Rev: 2.00
[4304947.131000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4304949.097000] sdc: Unit Not Ready, sense:
[4304949.097000] : Current: sense key: Unit Attention
[4304949.097000]     Additional sense: Not ready to ready change, medium may have changed
[4304949.098000] SCSI device sdc: 2033664 512-byte hdwr sectors (1041 MB)
[4304949.098000] sdc: Write Protect is off
[4304949.098000] sdc: Mode Sense: 03 00 00 00
[4304949.098000] sdc: assuming drive cache: write through
[4304949.101000] SCSI device sdc: 2033664 512-byte hdwr sectors (1041 MB)
[4304949.102000] sdc: Write Protect is off
[4304949.102000] sdc: Mode Sense: 03 00 00 00
[4304949.102000] sdc: assuming drive cache: write through
[4304949.102000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4304949.104000] Attached scsi removable disk sdc at scsi1, channel 0, id 0, lun 0
[4304949.105000] usb-storage: device scan complete
[4304949.635000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

### Post by electroconvulsive on 2006-05-15
Thanx heaps Pellgarlic I will try it as soon as I get back to my place. But just for now I have been using a workaround to get it working (not the solution though) adding it as a folder in media but now I think this might be the solution so I will give it a go and thanx for the response

BIG UPS

---

### Post by pellgarlic on 2006-05-15
cool. let us know if it works for you. fingers crossed...

---

