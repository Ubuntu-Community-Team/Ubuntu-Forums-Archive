---
title: "Can't import photos from digital camera"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by Gradus on 2005-08-25
Hi there!
I have been unsuccessfull in trying to import photos from my Panasonic Lumix DMC-FZ1 camera. It uses the USB Mass Storage protocol. #dmesg shows that the camera has been recognized: I'll put here the results of #dmesg

dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Aug 18 22:23:56 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000fffc000 (usable)
 BIOS-e820: 000000000fffc000 - 000000000ffff000 (ACPI data)
 BIOS-e820: 000000000ffff000 - 0000000010000000 (ACPI NVS)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
255MB LOWMEM available.
On node 0 totalpages: 65532
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 61436 pages, LIFO batch:14
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 ASUS                                  ) @ 0x000f61b0
ACPI: RSDT (v001 ASUS   MED_2001 0x30303031 MSFT 0x31313031) @ 0x0fffc000
ACPI: FADT (v001 ASUS   MED_2001 0x30303031 MSFT 0x31313031) @ 0x0fffc080
ACPI: BOOT (v001 ASUS   MED_2001 0x30303031 MSFT 0x31313031) @ 0x0fffc040
ACPI: DSDT (v001   ASUS MED_2001 0x00001000 MSFT 0x0100000b) @ 0x00000000
ACPI: PM-Timer IO Port: 0xe408
Built 1 zonelists
Kernel command line: root=/dev/hda9 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01204000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 998.145 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 252060k/262128k available (1436k kernel code, 9408k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1974.27 BogoMIPS (lpj=987136)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000
CPU: Intel Pentium III (Coppermine) stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0c20)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf0900, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
pnp: 00:02: ioport range 0xe800-0xe80f has been reserved
Simple Boot Flag at 0x3a set to 0x1
audit: initializing netlink socket (disabled)
audit(1124979284.469:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
PCI: Disabling Via external APIC routing
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 PCI1 UAR1 UAR2 USB0 USB1
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 16 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:04.1
VP_IDE: chipset revision 16
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:04.1
    ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: ST340823A, ATA DISK drive
hdb: LITEON DVD-ROM LTD122, ATAPI CD/DVD-ROM drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78165360 sectors (40020 MB) w/1024KiB Cache, CHS=65535/16/63, UDMA(66)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 p8 p9 p10 >
Probing IDE interface ide1...
hdc: _NEC DVD+RW ND-1100A, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (454 pages freed)
Restarting tasks... done
VFS: Can't find ext3 filesystem on dev hda9.
VFS: Can't find an ext2 filesystem on dev hda9.
ReiserFS: hda9: found reiserfs format "3.6" with standard journal
ReiserFS: hda9: using ordered data mode
ReiserFS: hda9: journal params: device hda9, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: hda9: checking transaction log (hda9)
ReiserFS: hda9: Using r5 hash to sort names
Adding 562232k swap on /dev/hda5.  Priority:-1 extents:1
hdb: ATAPI 40X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdc: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache
parport_pc: VIA 686A/8231 detected
parport_pc: probing current configuration
parport_pc: Current parallel port base: 0x378
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
parport_pc: VIA parallel port: io=0x378, irq=7
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
psmouse.c: Failed to reset mouse on isa0060/serio1
input: PS/2 Generic Mouse on isa0060/serio1
psmouse.c: Failed to enable mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
NTFS volume version 3.1.
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA Apollo Pro 133 chipset
agpgart: Maximum main memory to use for agp memory: 203M
agpgart: AGP aperture is 32M @ 0xfc000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:04.2[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:04.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:04.2: irq 10, io base 0xd400
uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:04.3[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:04.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:04.3: irq 10, io base 0xd000
uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-1: new low speed USB device using uhci_hcd and address 2
usb 1-2: new full speed USB device using uhci_hcd and address 3
usb 2-1: new full speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
drivers/usb/class/usblp.c: Disabling reads from problem bidirectional printer on usblp0
SCSI subsystem initialized
drivers/usb/class/usblp.c: usblp0: USB Unidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0604
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Initializing USB Mass Storage driver...
input: USB HID v1.10 Mouse [Wireless Mouse Wireless Mouse] on usb-0000:00:04.2-1usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:05.0[A] -> GSI 5 (level, low) -> IRQ 5
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
8139cp: pci dev 0000:00:0a.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 10 (level, low) -> IRQ 10
eth0: RealTek RTL8139 at 0xb000, 00:10:a7:29:15:6d, IRQ 10
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
NET: Registered protocol family 17
  Vendor: MATSHITA  Model: DMC-FZ1           Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 02
usb-storage: device scan complete
SCSI device sda: 121856 512-byte hdwr sectors (62 MB)
sda: Write Protect is off
sda: Mode Sense: 04 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 121856 512-byte hdwr sectors (62 MB)
sda: Write Protect is off
sda: Mode Sense: 04 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
UDF-fs: No VRS found
 
#mount shows:
/dev/hda9 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda1 on /media/windows type ntfs (rw,umask=0222)
/dev/hda7 on /media/windows type ntfs (rw,umask=0222)
/dev/hda8 on /media/windows type ntfs (rw,umask=0222)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

When I tried to mount /dev/sda it replied:cannot find /dev/sda in /etc/fstab or etc/mtab.
Trying to edit fstab as sudo did not succeed: access denied!
/proc/scsi/scsi    ...access denied!

I'm getting nowhere here!!  ](*,) 

Please help!

---

### Post by s_p_a_r_k_y on 2005-08-25
mount /dev/sda /mountpnt 
is your command. Otherwise it has no idea where to mount it unless its specified in /etc/fstab

I would do mount /dev/sda /media/camera
or something, of course /media/camera has to exist. Also sometimes they put a partition on the drive so you may actually want /dev/sda1 or sda2...

---

### Post by Gradus on 2005-08-25
Thanks Sparky, but alas, didn't work. No media found. The directories had been made though.

 ;-) but there is some light here; listen: I found that with gedit I could edit /etc/fstab
I added  line 13 (Bold)  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda9       /               reiserfs notail          0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
/dev/hda7       /media/windows  ntfs    umask=0222      0       0
/dev/hda8       /media/windows  ntfs    umask=0222      0       0
**/dev/sda       /media/camera  auto  noauto,user ,noauto  0     0**

And now the Matshita DMC-FZ1 is in " Computer".

But I still cannot import my pictures.
Remounting fstab with "sudo mount -a" tells me that "line 13 in fstab is bad"
 :???: 

Any suggestions?

---

### Post by s_p_a_r_k_y on 2005-08-25
could you copy and paste the output of
 sudo sfdisk -l /dev/sda

---

### Post by David Haas on 2005-08-25
Gradus--What method(s) did you use to try to import your photos? Most folks, including myself, use gThumb Image Viewer in Applications. One connects the camera via USB, turns on the camera, and then opens gThumb. When this is first done, one needs to select his camera from the listing. Thereafter, gThumb recognizes the camera. Once recognized, gThumb automatically displays thumbnails of all photos in the camera's memory. Then, selecting "File>import photos" downloads all pictues into one's home directory. 
David

---

### Post by Gradus on 2005-08-26
[QUOTE=s_p_a_r_k_y]could you copy and paste the output of
 sudo sfdisk -l /dev/sda[/QUOTE]
 Hi guys, thanks for helping again.

The " sudo sfdisk -l /dev/sda" gave this result:

/dev/sda: no media found

sfdisk: cannot open /dev/sda to read

what does this mean? Should I add some goup or user?

By the way: connecting via USB and opening gThumb and just select your camera from a list, as suggested by David, is not a solution. As it happens my camera is not on the list and not autodetected.

---

### Post by new2hoary on 2005-08-26
Try;

mount /dev/sda1 -t vfat  /mountpnt

Edit:

Remember the mount point has to exist before trying to mount it.

Edit2: Just noticed S_P_A_R_K_Y coverd this.

---

### Post by s_p_a_r_k_y on 2005-08-26
Gradus, did you issue that command with the camera plugged in, on play mode and turned on?

---

### Post by Gradus on 2005-08-26
[QUOTE=s_p_a_r_k_y]Gradus, did you issue that command with the camera plugged in, on play mode and turned on?[/QUOTE]

Yes Sparky I just did it again with same result

---

### Post by jonrkc on 2007-03-09
One of my many cameras is a Panasonic Lumix DCM-LZ2, so very similar to yours.  Here's what I got just now when I plugged it into the USB interface and turned the camera on: quoting from dmesg...

```

[17234451.792000] usb 2-1: new full speed USB device using uhci_hcd and address 
3
[17234451.940000] scsi5 : SCSI emulation for USB Mass Storage devices
[17234451.940000] usb-storage: device found at 3
[17234451.940000] usb-storage: waiting for device to settle before scanning
[17234456.944000]   Vendor: MATSHITA  Model: DMC-LZ2           Rev: 0100
[17234456.944000]   Type:   Direct-Access                      ANSI SCSI revisio
n: 02
[17234456.956000] SCSI device sdf: 1994752 512-byte hdwr sectors (1021 MB)
[17234456.956000] sdf: Write Protect is off
[17234456.956000] sdf: Mode Sense: 04 00 00 00
[17234456.956000] sdf: assuming drive cache: write through
[17234456.964000] SCSI device sdf: 1994752 512-byte hdwr sectors (1021 MB)
[17234456.968000] sdf: Write Protect is off
[17234456.968000] sdf: Mode Sense: 04 00 00 00
[17234456.968000] sdf: assuming drive cache: write through
[17234456.968000]  sdf: sdf1
[17234456.980000] sd 5:0:0:0: Attached scsi removable disk sdf
[17234456.980000] sd 5:0:0:0: Attached scsi generic sg5 type 0
[17234456.980000] usb-storage: device scan complete
[17234548.840000] usb 2-1: USB disconnect, address 3


```

I don't know if this will help you or not.  But I thought it might somehow give a clue.

I was having to spend a lot of time manually mounting my card reader and/or cameras before I gave in and switched completely to the KDE environment, which now does it for me.  Result: I can work with my pictures instead of the *&$!! USB interface which has got to be one of the (many) Achilles' heels of the OS.  (End of that particular rant.)

Before KDE, I would go to a console and see what had been going on after supposedly hooking up the device in question.  I would get clues here and there and finally after trial-and-error get the right sda(x) mounted using

```

sudo mount -t vfat /dev/sda1 /camera

```

in which example I would have found that it looked pretty much like sda1 would satisfy the system, and I'd already made a directory /camera.  Under KDE's automounting system, for which I thank the developers a million times, the reader or camera always gets mounted under /media, which is fine with me as long as I can finally see my photos.  

Which I can, now.

I sincerely hope this helps, and another thing--if it helps, I have some idea of what you're going through.  Why things have to be this difficult, I'll never know.

---

### Post by geck07 on 2007-03-09
Gradus,
In case everything fails,install kde-hal-device-manager using synaptic and see if it is able to see your camera when plugged in.
You can also use gtKam for importing pics.Its got a nice GUI with it.
Good Luck!

Geck07

---

