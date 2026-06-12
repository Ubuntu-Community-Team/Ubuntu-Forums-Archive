---
title: "amarok&amp;ipod /dev/sda/ issue!?!"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by orev on 2005-07-02
I am attempting to be able to have full access to my ipod via amarok using the info @ [http://amarok.kde.org/files/articles/ipod_amarok_tux_june05.pdf](http://amarok.kde.org/files/articles/ipod_amarok_tux_june05.pdf).

When I run dsmeg @ terminal I get this:

root@HPDESKTOP:/home/jason # dmesg
terface ide5...
Stopping tasks: ==|
Freeing memory... done (464 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1322960k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hdc: ATAPI 40X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-686
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA KM400/KM400A chipset
agpgart: Maximum main memory to use for agp memory: 380M
agpgart: AGP aperture is 64M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[ea001000-ea0017ff]  Max Packet=[2048]
libata version 1.10 loaded.
sata_via version 1.1
ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via(0000:00:0f.0): routed to hard irq line 4
ata1: SATA max UDMA/133 cmd 0xAC00 ctl 0xB002 bmdma 0xBC00 irq 20
ata2: SATA max UDMA/133 cmd 0xB400 ctl 0xB802 bmdma 0xBC08 irq 20
ata1: no device found (phy stat 00000000)
scsi0 : sata_via
ata2: no device found (phy stat 00000000)
scsi1 : sata_via
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0xc800
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0xcc00
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0xd000
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000060e49d]
uhci_hcd 0000:00:10.3: irq 21, io base 0xd400
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xea002000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
via82xx: Assuming DXS channels with 48k fixed sample rate.
         Please try dxs_support=1 or dxs_support=4 option
         and report if it works on your machine.
ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
usb 3-1: new full speed USB device using uhci_hcd and address 2
usb 4-1: new full speed USB device using uhci_hcd and address 2
via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
eth0: VIA Rhine II at 0xe000, 00:0e:a6:6c:5d:6c, IRQ 23.
eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x107F
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
  Vendor: Generic   Model: USB SD Reader     Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: USB CF Reader     Rev: 1.01
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: USB SM Reader     Rev: 1.02
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: USB MS Reader     Rev: 1.03
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 1
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 2
Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 3
eth0: no IPv6 routers present
usb 3-1: USB disconnect, address 2
drivers/usb/class/usblp.c: usblp0: removed
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
usb 3-1: new full speed USB device using uhci_hcd and address 3
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x107F
usb 3-1: USB disconnect, address 3
drivers/usb/class/usblp.c: usblp0: removed
usb 5-5: new high speed USB device using ehci_hcd and address 5
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sde: 58605120 512-byte hdwr sectors (30006 MB)
sde: Write Protect is off
sde: Mode Sense: 64 00 00 08
sde: assuming drive cache: write through
SCSI device sde: 58605120 512-byte hdwr sectors (30006 MB)
sde: Write Protect is off
sde: Mode Sense: 64 00 00 08
sde: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1 p2
Attached scsi removable disk sde at scsi3, channel 0, id 0, lun 0
usb-storage: device scan complete
UDF-fs: No VRS found
UDF-fs: No VRS found
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: invalid media value (0x2f)
VFS: Can't find a valid FAT filesystem on dev sde1.
FAT: invalid media value (0x2f)
VFS: Can't find a valid FAT filesystem on dev sde1.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS-fs warning (device sde1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde1): ntfs_fill_super(): Not an NTFS volume.
HFS+-fs: unable to find HFS+ superblock
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sde1.
VFS: Can't find a HFS filesystem on dev sde1.
VFS: Can't find ext3 filesystem on dev sde1.
VFS: Can't find ext3 filesystem on dev sde1.
VFS: Can't find an ext2 filesystem on dev sde1.
VFS: Can't find an ext2 filesystem on dev sde1.
ReiserFS: sde1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sde1
ReiserFS: sde1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sde1
SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
SGI XFS Quota Management subsystem
Unable to handle kernel NULL pointer dereference at virtual address 00000000
 printing eip:
c0114266
*pde = 00000000
Oops: 0000 [#1]
PREEMPT
Modules linked in: xfs reiserfs ext2 hfs hfsplus nls_cp437 ntfs vfat fat isofs nls_utf8 udf proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave video sd_mod sony_acpi pcc_acpi button battery container ac ipv6 af_packet usb_storage via_rhine mii usblp snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc gameport snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_viapro i2c_core ehci_hcd uhci_hcd usbcore sata_via libata ohci1394 pci_hotplug via_agp agpgart floppy pcspkr rtc md dm_mod evdev capability tsdev commoncap sr_mod sbp2 scsi_mod ieee1394 psmouse mousedev parport_pc lp parport ide_cd cdrom ext3 jbd mbcache ide_generic via82cxxx ide_disk ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
CPU:    0
EIP:    0060:[<c0114266>]    Not tainted VLI
EFLAGS: 00010002   (2.6.10-5-686)
EIP is at try_to_wake_up+0x2a/0xb3
eax: c03723e0   ebx: 00000000   ecx: cd3e2824   edx: 00000000
esi: c03723e0   edi: db5f5ee0   ebp: db5f5ef0   esp: db5f5ed0
ds: 007b   es: 007b   ss: 0068
Process kswapd0 (pid: 148, threadinfo=db5f4000 task=db5b8060)
Stack: 00000000 db5f5ee0 00000001 00000000 00000282 00000000 00000000 00000000
       db5f5f04 c011430d 00000000 0000000f 00000000 cd3e2820 dcefa44c c01408eb
       00000000 000000d0 00019914 00000000 00000000 00000040 00000000 00000002
Call Trace:
 [<c011430d>] wake_up_process+0x1e/0x22
 [<dcefa44c>] pagebuf_daemon_wakeup+0x14/0x17 [xfs]
 [<c01408eb>] shrink_slab+0x89/0x18b
 [<c0141db8>] balance_pgdat+0x272/0x2f6
 [<c0141f03>] kswapd+0xc7/0xd7
 [<c012b61d>] autoremove_wake_function+0x0/0x57
 [<c0102dbe>] ret_from_fork+0x6/0x14
 [<c012b61d>] autoremove_wake_function+0x0/0x57
 [<c0141e3c>] kswapd+0x0/0xd7
 [<c010127d>] kernel_thread_helper+0x5/0xb
Code: c3 55 89 e5 83 ec 20 89 5d f4 89 7d fc 89 75 f8 8b 5d 08 8d 7d f0 c7 45 ec 00 00 00 00 89 7c 24 04 89 1c 24 e8 98 fc ff ff 89 c6 <8b> 13 8b 45 0c 85 d0 74 47 8b 43 28 85 c0 75 3a 83 fa 02 74 67
 <6>note: kswapd0[148] exited with preempt_count 1
XFS: bad magic number
XFS: SB validate failed
XFS: bad magic number
XFS: SB validate failed
UDF-fs: No VRS found
UDF-fs: No VRS found
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
usb 5-5: USB disconnect, address 5
usb 5-5: new high speed USB device using ehci_hcd and address 6
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sde: 58605120 512-byte hdwr sectors (30006 MB)
sde: Write Protect is off
sde: Mode Sense: 64 00 00 08
sde: assuming drive cache: write through
SCSI device sde: 58605120 512-byte hdwr sectors (30006 MB)
sde: Write Protect is off
sde: Mode Sense: 64 00 00 08
sde: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0: p1 p2
Attached scsi removable disk sde at scsi4, channel 0, id 0, lun 0
usb-storage: device scan complete
UDF-fs: No VRS found
UDF-fs: No VRS found
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
UDF-fs: No VRS found
UDF-fs: No VRS found
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: invalid media value (0x2f)
VFS: Can't find a valid FAT filesystem on dev sde1.
FAT: invalid media value (0x2f)
VFS: Can't find a valid FAT filesystem on dev sde1.
NTFS-fs warning (device sde1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde1): ntfs_fill_super(): Not an NTFS volume.
HFS+-fs: unable to find HFS+ superblock
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sde1.
VFS: Can't find a HFS filesystem on dev sde1.
VFS: Can't find ext3 filesystem on dev sde1.
VFS: Can't find ext3 filesystem on dev sde1.
VFS: Can't find an ext2 filesystem on dev sde1.
VFS: Can't find an ext2 filesystem on dev sde1.
ReiserFS: sde1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sde1
ReiserFS: sde1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sde1
XFS: bad magic number
XFS: SB validate failed
XFS: bad magic number
XFS: SB validate failed

So, i believe I have some sort of mounting issue (?) and need to make some changes in order to get to /dev/sda/ so that I can get this to read a fat32 formatted ipod?

However, I have no idea where in the hell to start.

Can anyone point me to a url or give me some advice here?

10000 thanks. :) 

(above - 8 ) has been changed to 8) )

---

