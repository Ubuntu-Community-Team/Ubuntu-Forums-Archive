---
title: "Problems with removable media - cdrom, usb stick and usb hdd"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by kthdsn on 2005-10-16
Since upgrading to breezy, I am having problems with removable media.  When i insert a cd, or connect my usb stick or my usb hdd, I get the same behaviour:

The media doesn't appear on the desktop or in the places menu.

If I browse to /media/firelite (my usb hdd) the cd rom or usb stick, it tells me that the media is empty and the freespace is equal to the freespace on my system and not on the media.

The computer does attempt to read the drives, the read light flashes for a second on the cdrom and the usb hdd.

The /mnt/ folder remains empty no matter what media is available.

I didn't have any problems with any of the media in hoary, when I plugged it in/inserted it it appeared on the desktop and in the places menu and worked fine.  I haven't had to mount anything myself before and I wouldn't know how to do it.

I would appreciate some help, as I really need to access the files on my usb hdd (the stuff I backed up before putting breezy on) and I'm pretty sure I will want to use a cd in the near future too.

Thanks in advance.

---

### Post by jdtanner on 2005-10-16
I'm having the same problem as you! Hoary used to automatically mount and place icons on my desktop for my flashdisk and my cdrom. Breezy (both upgrade and fresh install) do not exhibit the same behaviour. It is possible for me to issue *mount /media/cdrom* to mount the disk, but clicking on the icon in Computer before I issue this command returns *Unable to Mount Selected Volume (error: given UDI is not a mountable volume)* .

Unless anyone can help I'll file a bugzilla,
JohnT

---

### Post by sk545 on 2005-10-16
I have the same issue, posted this thread yesterday:

[http://ubuntuforums.org/showthread.php?t=76858](http://ubuntuforums.org/showthread.php?t=76858)

What do you guys get when you plug something in and run 'dmesg'?  I get the following:

"UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'movie_name', timestamp 2005/07/19 02:24 (1f10)"

It mounts it, but no icon on the desktop. :(

---

### Post by chapeaurouge on 2005-10-16
Same issue here. The devices get mounted (you should see them if you type 'mount' in a terminal) but no icon appear anywhere.
I am running a dist-upgraded breezy from today.

:confused:

---

### Post by kthdsn on 2005-10-16
I plugged in my 3 devices and ran dmesg, I got the following:

05120 sectors (30005 MB) w/1739KiB Cache, CHS=16383/255/63, UDMA(100)
[4294676.497000] hda: cache flushes supported
[4294676.497000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.565000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294676.565000] Uniform CD-ROM driver Revision: 3.20
[4294677.047000] Attempting manual resume
[4294677.066000] swsusp: Suspend partition has wrong signature?
[4294677.110000] usbcore: registered new driver usbfs
[4294677.110000] usbcore: registered new driver hub
[4294677.111000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Dri ver (PCI)
[4294677.111000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> I RQ 19
[4294677.111000] ohci_hcd 0000:00:13.0: ATI Technologies Inc OHCI USB Controller  #1
[4294677.370000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus num ber 1
[4294677.370000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xf4001000
[4294677.425000] hub 1-0:1.0: USB hub found
[4294677.425000] hub 1-0:1.0: 3 ports detected
[4294677.430000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> I RQ 19
[4294677.430000] ohci_hcd 0000:00:13.1: ATI Technologies Inc OHCI USB Controller  #2
[4294677.688000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus num ber 2
[4294677.688000] ohci_hcd 0000:00:13.1: irq 19, io mem 0xf4002000
[4294677.743000] hub 2-0:1.0: USB hub found
[4294677.743000] hub 2-0:1.0: 3 ports detected
[4294677.764000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> I RQ 19
[4294677.764000] ehci_hcd 0000:00:13.2: ATI Technologies Inc EHCI USB Controller
[4294677.764000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus num ber 3
[4294677.764000] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf4003000
[4294677.764000] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294677.764000] hub 3-0:1.0: USB hub found
[4294677.764000] hub 3-0:1.0: 6 ports detected
[4294677.847000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294677.847000] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 81 39C+ compatible chip
[4294677.847000] 8139cp: Try the "8139too" driver instead.
[4294677.848000] 8139too Fast Ethernet driver 0.9.27
[4294677.848000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> I RQ 19
[4294677.849000] eth0: RealTek RTL8139 at 0xa000, 00:02:3f:0c:58:56, IRQ 19
[4294677.849000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294678.357000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[4294679.877000] SCSI subsystem initialized
[4294679.879000] Initializing USB Mass Storage driver...
[4294679.880000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294679.880000] usb-storage: device found at 2
[4294679.880000] usb-storage: waiting for device to settle before scanning
[4294679.880000] usbcore: registered new driver usb-storage
[4294679.880000] USB Mass Storage support registered.
[4294680.507000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294680.795000] Attempting manual resume
[4294680.816000] swsusp: Suspend partition has wrong signature?
[4294680.890000] kjournald starting.  Commit interval 5 seconds
[4294680.890000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.633000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.884000]   Vendor:           Model:                   Rev:
[4294684.884000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294684.915000] usb-storage: device scan complete
[4294687.270000] SCSI device sda: 1019617 512-byte hdwr sectors (522 MB)
[4294687.276000] sda: Write Protect is off
[4294687.276000] sda: Mode Sense: 00 c0 00 00
[4294687.276000] sda: assuming drive cache: write through
[4294687.283000] Adding 1228932k swap on /dev/hda5.  Priority:-1 extents:1
[4294687.297000] SCSI device sda: 1019617 512-byte hdwr sectors (522 MB)
[4294687.303000] sda: Write Protect is off
[4294687.303000] sda: Mode Sense: 00 c0 00 00
[4294687.303000] sda: assuming drive cache: write through
[4294687.303000]  /dev/scsi/host0/bus0/target0/lun0: unknown partition table
[4294687.335000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun  0
[4294687.703000] EXT3 FS on hda1, internal journal
[4294696.181000] lp: driver loaded but no devices found
[4294696.209000] mice: PS/2 mouse device common for all mice
[4294696.982000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa0 4713/0x4000
[4294696.986000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[4294697.021000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[4294697.247000] ts: Compaq touchscreen protocol output
[4294700.584000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294702.015000] cdrom: open failed.
[4294704.725000] Linux agpgart interface v0.101 (c) Dave Jones
[4294704.735000] agpgart: Detected Ati IGP9100/M chipset
[4294704.760000] agpgart: AGP aperture is 32M @ 0xf6000000
[4294704.871000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294704.889000] shpchp: shpc_init : shpc_cap_offset == 0
[4294704.889000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294705.486000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> I RQ 17
[4294705.487000] atiixp: codec reset timeout
[4294706.830000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> I RQ 17
[4294707.479000] Linux Kernel Card Services
[4294707.479000]   options:  [pci] [cardbus] [pm]
[4294707.496000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> I RQ 16
[4294707.496000] Yenta: CardBus bridge found at 0000:02:04.0 [1025:0065]
[4294707.496000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294707.496000] Yenta: Routing CardBus interrupts to PCI
[4294707.497000] Yenta TI: socket 0000:02:04.0, mfunc 0x00111c12, devctl 0x44
[4294707.718000] Yenta: ISA IRQ mask 0x0080, PCI irq 16
[4294707.718000] Socket status: 30000006
[4294709.463000] Real Time Clock Driver v1.12
[4294709.551000] input: PC Speaker
[4294711.645000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294711.659000] NET: Registered protocol family 17
[4294713.908000] NET: Registered protocol family 10
[4294713.909000] Disabled Privacy Extensions on device c02eb280(lo)
[4294713.909000] IPv6 over IPv4 tunneling driver
[4294715.363000] ACPI: AC Adapter [ACAD] (on-line)
[4294715.420000]     ACPI-0362: *** Error: Looking up [Z00B] in namespace, AE_NO T_FOUND
[4294715.420000] search_node ddf566c0 start_node ddf566c0 return_node 00000000
[4294715.420000]     ACPI-0508: *** Error: Method execution failed [\_SB_.PCI0.L PC0.BAT1._BIF] (Node ddf56660), AE_NOT_FOUND
[4294715.443000] ACPI: Power Button (FF) [PWRF]
[4294715.443000] ACPI: Lid Switch [LID]
[4294715.443000] ACPI: Power Button (CM) [PWRB]
[4294715.568000] ibm_acpi: ec object not found
[4294715.710000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294723.457000] [drm] Initialized drm 1.0.0 20040925
[4294723.461000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> I RQ 16
[4294723.463000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Techno logies Inc RS300M AGP [Radeon Mobility 9100IGP]
[4294723.464000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294723.464000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4294723.464000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4294723.464000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294723.464000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4294723.470000] [drm] Loading R200 Microcode
[4294724.818000] eth0: no IPv6 routers present
[4294727.722000] apm: BIOS not found.
[4294729.747000] cs: IO port probe 0x100-0x4ff: clean.
[4294729.749000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc1 7 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcd7
[4294729.750000] cs: IO port probe 0xa00-0xaff: clean.
[4294731.550000] Bluetooth: Core ver 2.7
[4294731.550000] NET: Registered protocol family 31
[4294731.550000] Bluetooth: HCI device and connection manager initialized
[4294731.550000] Bluetooth: HCI socket layer initialized
[4294731.832000] Bluetooth: L2CAP ver 2.7
[4294731.832000] Bluetooth: L2CAP socket layer initialized
[4294731.862000] Bluetooth: RFCOMM ver 1.5
[4294731.862000] Bluetooth: RFCOMM socket layer initialized
[4294731.862000] Bluetooth: RFCOMM TTY layer initialized
[4294767.427000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched .
[4295695.462000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295695.462000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4295695.462000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4295695.462000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295695.462000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4295695.530000] [drm] Loading R200 Microcode
[4295976.422000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295976.422000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4295976.422000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4295976.422000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295976.422000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4295976.605000] [drm] Loading R200 Microcode
[4324255.129000] ibm_acpi: ec object not found
[4343168.180000] usb 1-2: USB disconnect, address 2
[4343794.712000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4343794.712000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4343794.712000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4343794.712000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4343794.712000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4343794.739000] [drm] Loading R200 Microcode
[4347626.741000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4347626.741000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4347626.741000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4347626.741000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4347626.741000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4347626.748000] [drm] Loading R200 Microcode
[4353522.785000] hub 3-0:1.0: over-current change on port 1
[4353522.806000] hub 3-0:1.0: over-current change on port 4
[4353526.951000] usb 3-1: new high speed USB device using ehci_hcd and address 3
[4353527.029000] scsi1 : SCSI emulation for USB Mass Storage devices
[4353527.032000] usb-storage: device found at 3
[4353527.032000] usb-storage: waiting for device to settle before scanning
[4353532.032000]   Vendor: SAMSUNG   Model: MP0804H           Rev: UE10
[4353532.032000]   Type:   Direct-Access                      ANSI SCSI revision : 02
[4353532.036000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[4353532.036000] sda: assuming drive cache: write through
[4353532.039000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[4353532.039000] sda: assuming drive cache: write through
[4353532.039000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4353532.458000] Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
[4353532.461000] usb-storage: device scan complete
[4353544.535000] usb 3-1: USB disconnect, address 3
[4360973.010000] cdrom: open failed.
[4360973.097000] cdrom: open failed.
[4361233.752000] cdrom: open failed.
[4361404.220000] cdrom: open failed.
[4361461.085000] cdrom: open failed.
[4361547.338000] cdrom: open failed.
[4361622.375000] cdrom: open failed.
[4361695.176000] cdrom: open failed.
[4361710.886000] cdrom: open failed.
[4361735.374000] cdrom: open failed.
[4361742.327000] cdrom: open failed.
[4361884.890000] cdrom: open failed.
[4361884.901000] cdrom: open failed.
[4362028.122000] cdrom: open failed.
[4362065.035000] hub 3-0:1.0: over-current change on port 1
[4362065.056000] hub 3-0:1.0: over-current change on port 4
[4362069.453000] usb 3-1: new high speed USB device using ehci_hcd and address 4
[4362069.531000] scsi2 : SCSI emulation for USB Mass Storage devices
[4362069.533000] usb-storage: device found at 4
[4362069.533000] usb-storage: waiting for device to settle before scanning
[4362074.533000]   Vendor: SAMSUNG   Model: MP0804H           Rev: UE10
[4362074.533000]   Type:   Direct-Access                      ANSI SCSI revision : 02
[4362074.536000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[4362074.536000] sda: assuming drive cache: write through
[4362074.540000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[4362074.540000] sda: assuming drive cache: write through
[4362074.540000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4362074.977000] Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
[4362074.979000] usb-storage: device scan complete
[4362150.860000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[4362150.979000] scsi3 : SCSI emulation for USB Mass Storage devices
[4362150.980000] usb-storage: device found at 3
[4362150.981000] usb-storage: waiting for device to settle before scanning
[4362155.986000]   Vendor:           Model:                   Rev:
[4362155.986000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4362155.996000] SCSI device sdb: 1019617 512-byte hdwr sectors (522 MB)
[4362156.002000] sdb: Write Protect is off
[4362156.002000] sdb: Mode Sense: 00 c0 00 00
[4362156.002000] sdb: assuming drive cache: write through
[4362156.020000] SCSI device sdb: 1019617 512-byte hdwr sectors (522 MB)
[4362156.026000] sdb: Write Protect is off
[4362156.026000] sdb: Mode Sense: 00 c0 00 00
[4362156.026000] sdb: assuming drive cache: write through
[4362156.026000]  /dev/scsi/host3/bus0/target0/lun0: unknown partition table
[4362156.058000] Attached scsi removable disk sdb at scsi3, channel 0, id 0, lun  0
[4362156.060000] usb-storage: device scan complete
[4362641.840000] attempt to access beyond end of device
[4362641.840000] hda2: rw=0, want=4, limit=2
[4362641.840000] EXT3-fs: unable to read superblock
[4362988.643000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4362988.764000] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary b oot sector is invalid.
[4362988.764000] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount opt ion errors=recover not used. Aborting without trying to recover.
[4362988.764000] NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS vol ume.
[4363347.498000] cdrom: open failed.
[4363347.509000] cdrom: open failed.
[4364246.790000] Warning: /proc/ide/hd?/settings interface is obsolete, and will  be removed soon!
[4365160.758000] cdrom: open failed.
[4365160.770000] cdrom: open failed.
[4365362.490000] cdrom: open failed.
[4365362.502000] cdrom: open failed.
[4367596.003000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4367596.003000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4367596.003000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4367596.003000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4367596.003000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4367596.011000] [drm] Loading R200 Microcode
[4368044.992000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4368044.992000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4368044.992000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4368044.992000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4368044.992000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4368045.000000] [drm] Loading R200 Microcode


I don't understand a word of it but i'm assuming something is wrong!

---

### Post by chapeaurouge on 2005-10-16
A better way to look at this is to open up a terminal and type:

```
tail -f /var/log/messages
```

Then plug in your stuff.

chap.

---

### Post by jdtanner on 2005-10-16
Well, I my cdrom doesn't mount at all. Running a dmesg doesn't indicate anything at all. If I manually mount  (*mount /media/cdrom*) then I get 

[4294814.343000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294814.503000] ISO 9660 Extensions: RRIP_1991A

which is what I'd expect, and the icon appears on the desktop. However, if I just put the disk in the cd drive nothing happens (i.e. I have to manually mount).

Cheers,
JohnT

---

### Post by chapeaurouge on 2005-10-16
[QUOTE=jdtanner]Well, I my cdrom doesn't mount at all. Running a dmesg doesn't indicate anything at all. If I manually mount  (*mount /media/cdrom*) then I get 

[4294814.343000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294814.503000] ISO 9660 Extensions: RRIP_1991A

which is what I'd expect, and the icon appears on the desktop. However, if I just put the disk in the cd drive nothing happens (i.e. I have to manually mount).

Cheers,
JohnT[/QUOTE]
Mine always seem to mount, but never show on the desktop, even if manually mounted.

---

### Post by kthdsn on 2005-10-16
OK I have manually mounted my cdrom and it is working fine, but my usb devices still aren't.  The output from the tail -f things is this:

Oct 16 19:59:30 localhost kernel: [4368915.701000] usb 3-1: new high speed USB device using ehci_hcd and address 6
Oct 16 19:59:31 localhost kernel: [4368915.779000] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 16 19:59:31 localhost usb.agent[30500]:      usb-storage: already loaded
Oct 16 19:59:36 localhost kernel: [4368920.781000]   Vendor: SAMSUNG   Model: MP0804H           Rev: UE10
Oct 16 19:59:36 localhost kernel: [4368920.781000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Oct 16 19:59:36 localhost kernel: [4368920.784000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
Oct 16 19:59:36 localhost kernel: [4368920.788000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
Oct 16 19:59:36 localhost kernel: [4368920.788000]  /dev/scsi/host4/bus0/target0/lun0: p1
Oct 16 19:59:36 localhost kernel: [4368921.210000] Attached scsi disk sda at scsi4, channel 0, id 0, lun 0
Oct 16 19:59:36 localhost scsi.agent[30547]:      sd_mod: loaded sucessfully (for disk)
Oct 16 20:00:30 localhost kernel: [4368975.608000] usb 1-2: new full speed USB device using ohci_hcd and address 4
Oct 16 20:00:31 localhost kernel: [4368975.712000] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 16 20:00:31 localhost usb.agent[30669]:      usb-storage: already loaded
Oct 16 20:00:35 localhost kernel: [4368980.717000]   Vendor:           Model:                   Rev:
Oct 16 20:00:35 localhost kernel: [4368980.717000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Oct 16 20:00:35 localhost kernel: [4368980.727000] SCSI device sdb: 1019617 512-byte hdwr sectors (522 MB)
Oct 16 20:00:35 localhost kernel: [4368980.733000] sdb: Write Protect is off
Oct 16 20:00:36 localhost kernel: [4368980.751000] SCSI device sdb: 1019617 512-byte hdwr sectors (522 MB)
Oct 16 20:00:36 localhost kernel: [4368980.757000] sdb: Write Protect is off
Oct 16 20:00:36 localhost kernel: [4368980.757000]  /dev/scsi/host5/bus0/target0/lun0: unknown partition table
Oct 16 20:00:36 localhost kernel: [4368980.789000] Attached scsi removable disk sdb at scsi5, channel 0, id 0, lun 0
Oct 16 20:00:36 localhost scsi.agent[30717]:      sd_mod: loaded sucessfully (for disk)

The first device i plugged in was the usb hdd, the second the usb stick

---

### Post by sk545 on 2005-10-16
> tail -f /var/log/messages
with a usb pendrive, i get this:

```
Oct 16 14:58:28 localhost kernel: usb 2-2: new full speed USB device using ohci_hcd and address 4
Oct 16 14:58:28 localhost kernel: Initializing USB Mass Storage driver...
Oct 16 14:58:28 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Oct 16 14:58:28 localhost kernel: usbcore: registered new driver usb-storage
Oct 16 14:58:28 localhost kernel: USB Mass Storage support registered.
Oct 16 14:58:28 localhost usb.agent[6083]:      usb-storage: loaded successfully
Oct 16 14:58:33 localhost kernel:   Vendor: KINGSTON  Model: USB DRIVE         Rev: 1.12
Oct 16 14:58:33 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
Oct 16 14:58:33 localhost kernel: SCSI device sda: 125952 512-byte hdwr sectors (64 MB)
Oct 16 14:58:33 localhost kernel: sda: Write Protect is off
Oct 16 14:58:33 localhost kernel: SCSI device sda: 125952 512-byte hdwr sectors (64 MB)
Oct 16 14:58:33 localhost kernel: sda: Write Protect is off
Oct 16 14:58:33 localhost kernel:  sda:<7>usb-storage: queuecommand called
Oct 16 14:58:33 localhost kernel:  sda1
Oct 16 14:58:33 localhost kernel: Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Oct 16 14:58:33 localhost scsi.agent[6145]:      sd_mod: loaded sucessfully (for disk)
```

With a cd/dvd in the drive, i get this:

```
Oct 16 15:01:01 localhost kernel: UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'MOVIE_NAME', timestamp 2004/10/21 22:02 (1f10)
```

My problem is that its not showing a icon on the desktop...you guys are even worse...it doesn't even mount it.  I mean, i can browse the mounted area, and it has the files in it.  One thing i did try was ' sudo apt-get remove --purge hal'  (which removes gnome-volume-manager hal hal-device-manager hwdb-client ubuntu-desktop update-notifier), then i reinstalled them all with 'sudo apt-get install gnome-volume-manager hal hal-device-manager hwdb-client ubuntu-desktop update-notifier'.  Maybe that fixed the mounting part for me??  Someone else give it a try and see what happens.

Also, anyone notice that when a application hangs now, the 'force quite' dialog message doesn't come up?  You have to manually kill it using ps -aux.  Man, i am really missing hoary right now..

---

### Post by kayas80 on 2005-10-16
I get the same problem if I insert my USB memory stick i.e. there is no icon on the desktop. I can, however, access it via Computer, but cannot write to the disk ](*,)

---

### Post by sk545 on 2005-10-16
bug has been filed:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17607](http://bugzilla.ubuntu.com/show_bug.cgi?id=17607)

reply to it, everyone. Heehee.

---

### Post by kayas80 on 2005-10-16
[quote=sk545]bug has been filed:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17607]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17607")

reply to it, everyone. Heehee.[/quote]

I've never submitted a bug before so excuse my ignorance. That bug reports title is "Breezy can't automount DVD-ROM". Does it also include the mounting error for USB disk drives?

---

### Post by jdtanner on 2005-10-16
You could amend the bug to include usb media, or create a new bug and then refer to bug number 17607 as exhibiting similar behaviour. Create a bugzilla account...it is great fun ;-)

Cheers,
JohnT

---

### Post by kayas80 on 2005-10-16
[quote=jdtanner]You could amend the bug to include usb media, or create a new bug and then refer to bug number 17607 as exhibiting similar behaviour. Create a bugzilla account...it is great fun ;-)

Cheers,
JohnT[/quote]

I had a look, but don't have the nerve as I don't really understand what it's all about

---

### Post by Jmanyeah on 2005-10-16
I too am also having issues hotplugging and accessing my IEEE1394 hd. First things first, I'm running Kubuntu on top of Breazy. Also, on bootup I'm not getting an "ok" on the hotplug stage. This is probably why I'm experiencing this problem. So here are the details. My hd is recognized (it's listed in the Disks gui and is logged as being attached in "tail -f /var/log/messages."  Here'ss the log:

[I]> ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00050003e0000f71]
[4298896.378000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4298896.379000] scsi3 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4298897.485000] ieee1394: sbp2: Logged into SBP-2 device
[4298897.485000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048][4298897.494000]   Vendor: ST320082  Model: 2A                Rev:
[4298897.494000]   Type:   Direct-Access                      ANSI SCSI revision: 06
[4298897.509000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[4298897.509000] sda: asking for cache data failed
[4298897.509000] sda: assuming drive cache: write through
[4298897.515000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[4298897.515000] sda: asking for cache data failed
[4298897.515000] sda: assuming drive cache: write through
[4298897.515000]  /dev/scsi/host3/bus0/target0/lun0: p1
[4298897.520000] Attached scsi disk sda at scsi3, channel 0, id 0, lun 0[/I]


But it fails to mount, no icon and i can't access it. I am able to mount it manually after adding the device to "fstab" and mounting /dev/sda1 to /mnt/tmp. I can access the files on the drive this way, but there are several inconsitencies. The System Disk GUI is showing that it's empty when it's got over 40 gb of data in it that I can access. It's also not registering as an IEEE1394 device in InfoCenter, only as a Storage device. This just doesn't seem to be a stable way to be running it. 

Any help on how to troubleshoot hotplug, or how to get it to automount on connection would be great. Thanks.

---

### Post by HanZo on 2005-10-18
I had the same problem. Yesterday I fresh installed Breezy and no icons would appear on the desktop neither for cds nor for my benq joybee mp3 player, although these were mounted (i could access them under /media/nameofthe device, and unmount them manually through the console).

Today, I opened synaptic and installed everything that looked like automount or hotplug or usb... basically: autofs, gnome-volume-manager, pmount, usbmount (sorry I can't remember axactly all the stuff I installed)
although I did not hope to see any great change after this, I did not really know what I was installing, now everything works fine, just had to reboot and [b]ubuntu now finally does all the icons on dektop things it used to!
[/b] hope this helps somebody to solve the problem

---

### Post by sk545 on 2005-10-18
i din't think we had to install autofs?  I thought hal took care of this...

---

### Post by kthdsn on 2005-10-18
Well I eventually decided to go back to Hoary until this problem was sorted, so I did a fresh Hoary install and set up all my old settings.  Thismorning I noticed somebody had added a solution to the bug report so I decided to upgrade again and give it a try.  I upgraded through synaptic and had a few problems with broken packages and incompatibilities on the way, but I eventually got sorted.  Just on the offchance, I plugged in the USB drive and it worked!

I don't know what was causing it not to work before or what caused it to work now, but I thought I would just let everyone know that I am no longer having problems, and Breezy is behaving perfectly.

I am really amazed at how fast solutions were found for this problem, in my previous experience (all with windows) if there was a bug then tough.  Nobody really seemed to care let alone try and fix it.  Thumbs up massively to ubuntu and open source!

---

### Post by HanZo on 2005-10-18
Actually don't think autofs solved the problem... I just listed everything I installed... because afterwards it worked (and still does).
Ehm... where can I find the solution to the bug? just curious... on ubuntu bugzilla ([http://bugzilla.ubuntu.com/show_bug.cgi?id=17607](http://bugzilla.ubuntu.com/show_bug.cgi?id=17607)) I cannot see it...

---

### Post by aeroRunner on 2005-10-18
Sounds like I am having the same problem as many others.  When I boot, the "starting hotplug subsystem" does not show OK.  And then when I plug in my USB drive, it does not show up on the desktop like it did with 5.04.  I installed the things that HanZo suggested but it still doesn't work.  

I have discovered though, that if I boot with the USB drive plugged in, it works.  Unfortunately, it also hangs for quite a while on "starting modules" if I do this.  The hotplug subsystem even starts properly when the drive is plugged in at bootup.  But when I unplug the drive and reinsert it, it no longer shows up on the desktop.

I am a newbie, but I have tried several other distros and have never been able to stick with linux.  I really liked 5.04 because it just worked.  Hopefully someone can help get this bug worked out so it just works for me too.

-David

---

### Post by HanZo on 2005-10-18
well... my approach was not really scientifical... who knows what really made the thing work... anyway just to be shure I'd check if hotplug is installed.
Can you mount cds? can you access them under /media/cdrom ?
Another thing I did (but I don't think this has something to do with things working) is use the diskmounter applet to mount the cd... one of those you can add to the panel

---

### Post by sk545 on 2005-10-18
Alright, try what someone said in the bug report guys:

> 
$ sudo /etc/init.d/dbus restart

-restart gnome-volume-manager (you probably won't have to do this, since gvm only runs when something is connected or inserted, i.e: cd/dvd, usb drive)

$ sudo killall gnome-panel
$ sudo killall nautilus


I did the above, then inserted a dvd, and the icon shows up on the desktop.  However, the application (totem) that is supposed to launch automatically, doesn't happen.  Plus, i have to reboot and see if the above works afterwards.

/edit: Nope, it didn't survive a reboot.  In other words, you have to run the above commands everytime you reboot.  Not good at all.  Its still a unfixed bug.

---

### Post by sk545 on 2005-10-26
Can you guys please comment a bit more on this bug?  I have been trying hard for days, and so far there hasn't been a solution.  The bug's status got changed to "Resolved", however, the resolution is not correct.  The problem still persists.  

Thanks.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17607](http://bugzilla.ubuntu.com/show_bug.cgi?id=17607)

---

### Post by sadiini on 2005-10-27
I pluged in my camera and got similar results as you guys. No mounting, no icon etc. 
So finally I discovered something called Storage Device Manager under System -  Admin.
I played with it and managed to mount my camera with it (manually of cource) :(
It is very annoying bug there I must admit...

Since it is fixed, go and check this manager out...

---

### Post by jdtanner on 2005-10-27
SK545 is correct. This bug isn't resolved. There are separate issues here and the later bug report does not address them.

JohnT

---

### Post by sk545 on 2005-10-27
how do you change a bug's status?  It looks like someone locked it, and the only option there is "Leave as RESOLVED DUPLICATE".

---

### Post by WayneSchuller on 2005-10-28
I had a problem with usb sticks and other devices not mounting.

It turns out I had to do this:
Go to System Menu->Administration->Users and Groups
Click on your main user.
Click on Properties.
Click on the "User Privileges" tab.

Check all the boxes for things you want: e.g.: "external storage devices" "scanner" etc. All this will do is add you to the right groups to get permissions to do these things.

Reboot the computer. 

Everything will work good.

The reason it didn't work for me was I deleted my default ubuntu user (which comes with all these options on) and created a new user without these options added.

---

### Post by sk545 on 2005-10-28
That didn't work for me.  My "boxes" are all checked off in the users/groups.
Any way you could share your /etc/group file with us?  I would like to compare and see how it differs from mine.

Thanks.

---

### Post by kayas80 on 2005-11-07
Any idea when this is going to get fixed? It's been broken for weeks. I still can't get my USB drive working. It's really annoying! I may have to change OS as I can't transfer data between work and home!!!

---

### Post by Marcussen on 2005-11-17
Same problem kubuntu 5.10
no automount of usb hard drive or usb flash drive
tried pmount no luck, 

I believe I am going to uninstall ubuntu and try something different nothing but problem after problem.

---

### Post by kthdsn on 2005-11-18
My problems were fixed by reinstalling, perhaps you could try that rather than giving up on ubuntu altogether.  I appreciate how frustrating it is when its not working, but when it is working its fantastic and totally worth trying again for IMHO.  Good luck!

---

### Post by bfonseca on 2005-11-19
[QUOTE=sk545]Alright, try what someone said in the bug report guys:



I did the above, then inserted a dvd, and the icon shows up on the desktop.  However, the application (totem) that is supposed to launch automatically, doesn't happen.  Plus, i have to reboot and see if the above works afterwards.

/edit: Nope, it didn't survive a reboot.  In other words, you have to run the above commands everytime you reboot.  Not good at all.  Its still a unfixed bug.[/QUOTE]
sks545 thank you for your recommendation on how to fix the cdrom drive. I did exactly what you said in your post and it worked.  Once again thanks for your post.
Brian

---

### Post by topic58 on 2005-11-20
Just like me then. I have problems with my USB-harddrive AND my USB-stick. Problems writing to them and sometimes reading from them. In Hoary there was no problems at all. A couple of weeks ago everything worked okay. Maybe some updates that makes them unsteady/ nonworking properly? Perhaps a question for the good people from Ubuntu? :rolleyes:

---

### Post by kayas80 on 2005-11-22
I just get a system update called Pmount. Things seem to copying to my USB drive now - something I couldn't do before. I'll test it on a Windows machine ASAP because that's also where I had a problem.

Has this problem been fixed for anyone else since updating?

---

### Post by tman_ubuntu on 2005-11-22
Ok, I've just recently upgraded from hoary to breezy as well.  Initially usb memory stick did not work.  Here's what I did to fix it.  Actually it is technically not a fix.  Nevertheless here's what I did.

Whatever usb drive is in question (memory stick, external drive and/or both), had them plugged in and rebooted.  Once rebooted and when the desktop re-appeared, my device icons were back on the desktop.  

I Right-clicked on the usb drive icon and unmounted it/them.  
I Removed the usb cable from usb plug.
I Re-insert usb plug and it detected my usb devices automatically mounted it and opened a file browser.

Seems simple enough but it works now.  Don't have a clue as to why.  Probably has something to do with the modules being initially registered with the kernel  and installed or something.

NOTE:  If you are considering upgrading to Breezy from Hoary, DON'T.  There is still waaaaay too many issues that still needs to be worked out in Breezy.  My upgrade was a nightmare between my video and usb stuff.  But that's just my experience. :(

---

### Post by kayas80 on 2005-11-24
[quote=tman_ubuntu]
NOTE: If you are considering upgrading to Breezy from Hoary, DON'T. There is still waaaaay too many issues that still needs to be worked out in Breezy. My upgrade was a nightmare between my video and usb stuff. But that's just my experience. :([/quote]

I agree my systems stability has taken a step back since upgrading to Breezy. Amarok, Firefox, USB drive and Lame are all less stable than under Hoary. Hopefully Dapper will sort this out!

---

### Post by oofnik on 2005-11-26
Yep, same problem. I have several external USB devices that would automount fine with Hoary, like my CF card reader, iRiver MP3 player, USB2 external HDD, etc.. but with Breezy it only works if the device is plugged in at boot. I have to pmount it manually when I plug it in. That shouldn't happen.. I hope someone figures this out!!
Maybe my dmesg output may help:
```

[4297344.196000] usb 5-2: new high speed USB device using ehci_hcd and address 7[4297344.338000] scsi5 : SCSI emulation for USB Mass Storage devices
[4297344.341000] usb-storage: device found at 7
[4297344.341000] usb-storage: waiting for device to settle before scanning
[4297349.356000]   Vendor: USB 2.0   Model: Storage Device    Rev: 0100
[4297349.356000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4297349.377000] SCSI device sdg: 80418240 512-byte hdwr sectors (41174 MB)
[4297349.377000] sdg: assuming drive cache: write through
[4297349.384000] SCSI device sdg: 80418240 512-byte hdwr sectors (41174 MB)
[4297349.384000] sdg: assuming drive cache: write through
[4297349.384000]  /dev/scsi/host5/bus0/target0/lun0: p1 p2
[4297349.401000] Attached scsi disk sdg at scsi5, channel 0, id 0, lun 0
[4297349.402000] Attached scsi generic sg6 at scsi5, channel 0, id 0, lun 0,  type 0
[4297349.404000] usb-storage: device scan complete

```

---

### Post by Mustard on 2005-11-26
Reading over the earlier mentioned bugzilla report, it would seem there will be no 'official' fix until dapper comes out.

---

### Post by lila on 2005-11-27
[QUOTE=HanZo]I had the same problem. Yesterday I fresh installed Breezy and no icons would appear on the desktop neither for cds nor for my benq joybee mp3 player, although these were mounted (i could access them under /media/nameofthe device, and unmount them manually through the console).

Today, I opened synaptic and installed everything that looked like automount or hotplug or usb... basically: autofs, gnome-volume-manager, pmount, usbmount (sorry I can't remember axactly all the stuff I installed)
although I did not hope to see any great change after this, I did not really know what I was installing, now everything works fine, just had to reboot and [b]ubuntu now finally does all the icons on dektop things it used to!
[/b] hope this helps somebody to solve the problem[/QUOTE]

This looks like something I should do, too - I'm new to Linux (just installed Breezy Badger) and don't know how it should behave, so not good at spotting a bug, just "don't know how this works"... But I got a few "can't mount this or that" messages to do with CDs. 
 Just one possibly rather stupid question: what is synaptic, and how can I get into it, where can I find it? Does it involve being connected to the internet, because that is my other problem, I am not, posted on the newbie forum about that, the computer doesn't recognise its modem).
Lila

---

### Post by kayas80 on 2005-11-28
[quote=Mustard]Reading over the earlier mentioned bugzilla report, it would seem there will be no 'official' fix until dapper comes out.[/quote]

:???:

---

### Post by UphillSkier on 2005-11-28
[QUOTE=lila]<snip>
Just one possibly rather stupid question: what is synaptic, and how can I get into it, where can I find it? Does it involve being connected to the internet, because that is my other problem, I am not, posted on the newbie forum about that, the computer doesn't recognise its modem).
Lila[/QUOTE]

Synaptic is the debian/ubuntu package manager - it is easy to use.  Check out the Ubuntu 5.10 Starter guide (available from the lifebuoy on the panel) under "Installing Applications" 
:smile:

---

### Post by lila on 2005-11-28
[QUOTE=UphillSkier]Synaptic is the debian/ubuntu package manager - it is easy to use.  Check out the Ubuntu 5.10 Starter guide (available from the lifebuoy on the panel) under "Installing Applications" 
:smile:[/QUOTE]
 Thanks!  I had meanwhile done some diggging both in the forums and on the desktop and had found it.  But I have just discovered, thanks to you, that the lifebuoy actually works without internet access, or at least some of it does.  I had just seen all the blue underlined things and not bothered clicking because I thought it would just get me another "unable to find page".  So, hopefully I'll ask fewer questions with easy and obvious answers from now on.  Thanks again...
Lila

---

### Post by budx on 2005-11-29
[QUOTE=HanZo]I had the same problem. Yesterday I fresh installed Breezy and no icons would appear on the desktop neither for cds nor for my benq joybee mp3 player, although these were mounted (i could access them under /media/nameofthe device, and unmount them manually through the console).

Today, I opened synaptic and installed everything that looked like automount or hotplug or usb... basically: autofs, gnome-volume-manager, pmount, usbmount (sorry I can't remember axactly all the stuff I installed)
although I did not hope to see any great change after this, I did not really know what I was installing, now everything works fine, just had to reboot and [b]ubuntu now finally does all the icons on dektop things it used to!
[/b] hope this helps somebody to solve the problem[/QUOTE]

Hello Hanzo, i just tried the same thing that you do. I open Synptic and installed all the stuff wiht mount, automount, gnome-volume-manager, pmount, usbmount and i additional install the hal new. And, what should i say, it really works. Now all Icons are there and i can mount my usb-stick and all my foto media cards.
Thank you for that good workaround.
budx

---

### Post by kirmonkey on 2005-12-06
Hi,

I have been following this thread for a while and have similar problems with USB sticks and CD/DVDs. I have posted a bugzilla that people may want to look at, comment on, answer etc.

There seems to be a number of people having HAL/pmount problems recently and no definitive solution as yet.

Here you go:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=20237]("http://bugzilla.ubuntu.com/show_bug.cgi?id=20237")

---

### Post by hollie on 2005-12-14
Hello,

following the information in [this post]("http://www.ubuntuforums.org/showthread.php?t=49939"), I simply added the user 'hal' to the following groups: 'cdrom floppy tape audio plugdev scanner'. Now my USB disks, CDROMs and scanner are automagically detected and mounted (in case of the disks) on Breezy.

Just edit the /etc/group file (add 'hal' after all the mentioned group lines), reboot or issue 'sudo /etc/init.d/dbus restart' and you're done.

HTH,
 Hollie.

---

### Post by skirkpatrick on 2005-12-14
Here's the problem I get by inserting a flash drive:
> 
dmesg:
[4551387.870000] usb 5-8: new high speed USB device using ehci_hcd and address 5[4551387.932000] usb 5-8: device descriptor read/64, error -71
[4551388.095000] usb 5-8: device descriptor read/64, error -71
[4551388.258000] usb 5-8: new high speed USB device using ehci_hcd and address 6[4551388.320000] usb 5-8: device descriptor read/64, error -71
[4551388.483000] usb 5-8: device descriptor read/64, error -71
[4551388.646000] usb 5-8: new high speed USB device using ehci_hcd and address 7[4551389.048000] usb 5-8: device not accepting address 7, error -71
[4551389.110000] usb 5-8: new high speed USB device using ehci_hcd and address 8[4551389.512000] usb 5-8: device not accepting address 8, error -71


The same drive works fine on my Breezy laptop.

---

### Post by ispmarin on 2005-12-15
I have a different problem: My user is logged by nis, so when I try to do the permission things, it does not work. Any workaround?

Thanks

---

### Post by kayas80 on 2006-01-13
Has this bug been fixed yet? If not, does anyone know when it is likely to be fixed?

---

### Post by jfryman on 2006-01-13
[QUOTE=kayas80]Has this bug been fixed yet? If not, does anyone know when it is likely to be fixed?[/QUOTE]

It's my understanding that this is due to the nature of pmount/dbus/hal versions on breezy and the update to the linux kernel (2.6.13 and greater). If you manually update a kernel, then you run into this issue. The updates to pmount/dbus/hal are avaliable in Dapper... but the only way that I see this being 'fixed' for breezy is with a backport or a manual build of each package to newer versions. 

The versions needed to make this work properly: (as I understand it)

pmount: >= 0.9.7
dbus: >= 0.60
hal: >= 0.5.5

I know on my other boxen (Fedora, Slack, Debian)... this is a moot point. I could be way off, but this is what I've observed. The only solutions I see are such:

1) Request a backport
2) Compile your own
3) Try and inject dapper .deb's

Of the three, I would think a backport would be the best, since that would be the path that is furthest away from leaving the main ubuntu tree. Otherwise, you're going into uncharted territoriy (as far as the debian/ubuntu folks are concerned). 

Personally, if you want and need a good kernel and preformance, I would run a 2.6.12 with the nitro patches to keep the above compatability.

I may be way off base... so any comments/thoughts are appreciated. Thanks!

-James

---

### Post by wagdog on 2006-01-13
Have you tried the fix suggested by hollie above?  I had the exact same problem where my cd-rom and usb devices weren't mounting and I was getting cryptic errors. But by granting hal the rights it needed everything now works like it's supposed to.

---

### Post by phyzome on 2006-04-18
I get the same AE_NOT_FOUND error in dmesg.  The sequence of events is:

[LIST]
[*]insert card
[*]beep
[*]beep
[*]drive briefly appears on desktop, then disappears
[*]import photos prompt appears
[/LIST]

The following is the exact transcript in dmesg as I put my card reader in:

```

[4412187.252000] Probing IDE interface ide2...
[4412187.516000] hde: SanDisk SDCFB-256, CFA DISK drive
[4412187.884000]     ACPI-0362: *** Error: Looking up [Z004] in namespace, AE_NOT_FOUND
[4412187.884000] search_node dbdd7fe0 start_node dbdd7fe0 return_node 00000000
[4412187.884000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dbdd7ee0), AE_NOT_FOUND
[4412188.434000] ide2 at 0x100-0x107,0x10e on irq 3
[4412188.435000] hde: max request size: 128KiB
[4412188.435000] hde: 501760 sectors (256 MB) w/1KiB Cache, CHS=980/16/32
[4412188.435000] hde: cache flushes not supported
[4412188.436000]  /dev/ide/host2/bus0/target0/lun0: p1
[4412188.441000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0
[4412188.676000]  /dev/ide/host2/bus0/target0/lun0: p1
[4412188.683000]  /dev/ide/host2/bus0/target0/lun0: p1
[4412189.003000]  /dev/ide/host2/bus0/target0/lun0: p1
[4412189.131000]  /dev/ide/host2/bus0/target0/lun0: p1
[4412189.136000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4412217.890000]     ACPI-0362: *** Error: Looking up [Z004] in namespace, AE_NOT_FOUND
[4412217.890000] search_node dbdd7fe0 start_node dbdd7fe0 return_node 00000000
[4412217.890000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dbdd7ee0), AE_NOT_FOUND

```

This is sometimes followed by a longer string of search_node and AE_NOT_FOUND messages, grouped in triplets.

I used to be able to use this thing, but I think the Breezy upgrade did it in.  I know it screwed with my ability to import over USB directly from my camera. (Specifically the Canon Powershot S1 IS.)

---

### Post by z_diver on 2006-04-21
[QUOTE=jfryman]
The versions needed to make this work properly: (as I understand it)

pmount: >= 0.9.7
dbus: >= 0.60
hal: >= 0.5.5[/QUOTE]

None of my versions are that new so I almost gave up hope but then checked another breezy install and the USB drive automatically popped right up.  I checked versions of the above mentioned packages and they were the same on both machines.  Even the kernel was the same.  Hmmm...

Next I checked in Places > Computer and saw that the disk was listed.  If I clicked on it in the breezy machine that didn't work I got an error message saying something to the effect that [COLOR="Blue"]the mount point or directory didn't exist[/COLOR].  And sure enough /media was missing.

So -- all I did was run '[COLOR="Red"]sudo mkdir /media[/COLOR]' and everything went back to normal and now my drive pops right up.  

Just though I'd let people know it can be as simple as that.

---

### Post by HolyMurderer on 2006-05-18
In my case, my usb devices are mounted, but no icon is shown in desktop... I use Kubuntu Breezy... any help is welcome. Thanks

---

