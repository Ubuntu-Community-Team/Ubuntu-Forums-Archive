---
title: "PCMCIA  Hard drive only detected after reconnect"
date: 2010-07-30
forum: Hardware
---

### Post by lplo on 2010-07-30
I have an pcmcia sata card, which is detected and seems to work just fine. But it only detects the attached hard drive after i disconnect it and plug it back in. just switching the drive on and off will not help. Is there a way i can get the hard drive detected (and subsequently mounted) at boot time?


"hal-device" says after a boot for the PCMCIA card:

2: udi = '/org/freedesktop/Hal/devices/pci_1095_3112'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  pci.subsys_vendor = 'Silicon Image, Inc.'  (string)
  storage.hotpluggable = true  (bool)
  storage.automount_enabled_hint = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/pci_1095_3112'  (string)
  storage.removable = true  (bool)
  storage.policy.should_mount = true  (bool)
  info.subsystem = 'pci'  (string)
  info.product = 'SiI 3112 [SATALink/SATARaid] Serial ATA Controller'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_104c_ac44'  (string)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0'  (string)
  info.linux.driver = 'sata_sil'  (string)
  pci.product_id = 12562  (0x3112)  (int)
  pci.vendor_id = 4245  (0x1095)  (int)
  pci.subsys_product_id = 12562  (0x3112)  (int)
  pci.subsys_vendor_id = 4245  (0x1095)  (int)
  pci.device_class = 1  (0x1)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.vendor = 'Silicon Image, Inc.'  (string)
  info.vendor = 'Silicon Image, Inc.'  (string)
  pci.product = 'SiI 3112 [SATALink/SATARaid] Serial ATA Controller'  (string)
  storage.media_check_enabled = true  (bool)



only after i reconnect the hard drive  it also has this entry:

0: udi = '/org/freedesktop/Hal/devices/volume_uuid_0ce6a07f_899c_4b8f_8330_5636025a9d20'
  info.category = 'volume'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' } (string list)
  info.product = 'Volume (ext4)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_0ce6a07f_899c_4b8f_8330_5636025a9d20'  (string)
  block.device = '/dev/sdb1'  (string)
  block.major = 8  (0x8)  (int)
  block.minor = 17  (0x11)  (int)
  block.is_volume = true  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Hitachi_HDS721010CLA332_JP2911HQ0DWL6A'  (string)
  volume.fstype = 'ext4'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.uuid = '0ce6a07f-899c-4b8f-8330-5636025a9d20'  (string)
  volume.label = ''  (string)
  volume.mount_point = ''  (string)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.linux.is_device_mapper = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_partition = true  (bool)
  volume.partition.number = 1  (0x1)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.num_blocks = 1953520002  (0x74705982)  (uint64)
  volume.size = 1000202241024  (0xe8e0b30400)  (uint64)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.partition.media_size = 1000204886016  (0xe8e0db6000)  (uint64)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0/host5/target5:0:0/5:0:0:0/block/sdb/sdb1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_Hitachi_HDS721010CLA332_JP2911HQ0DWL6A'  (string)
  volume.ignore = false  (bool)
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' } (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' } (string list)
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' } (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' } (string list)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec' } (string list)
  volume.unmount.valid_options = { 'lazy' } (string list)


1: udi = '/org/freedesktop/Hal/devices/storage_serial_Hitachi_HDS721010CLA332_JP2911HQ0DWL6A'
  info.vendor = 'ATA'  (string)
  info.category = 'storage'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  storage.removable.media_size = 1000204886016  (0xe8e0db6000)  (uint64)
  storage.partitioning_scheme = 'mbr'  (string)
  info.capabilities = { 'storage', 'block' } (string list)
  info.product = 'Hitachi HDS72101'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_Hitachi_HDS721010CLA332_JP2911HQ0DWL6A'  (string)
  block.device = '/dev/sdb'  (string)
  block.major = 8  (0x8)  (int)
  block.minor = 16  (0x10)  (int)
  block.is_volume = false  (bool)
  storage.bus = 'pci'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.drive_type = 'disk'  (string)
  storage.model = 'Hitachi HDS72101'  (string)
  storage.vendor = 'ATA'  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Hitachi_HDS721010CLA332_JP2911HQ0DWL6A'  (string)
  storage.lun = 0  (0x0)  (int)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.removable.media_available = true  (bool)
  storage.size = 1000204886016  (0xe8e0db6000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'Hitachi_HDS721010CLA332_JP2911HQ0DWL6A'  (string)
  storage.firmware_version = 'JP4OA3AE'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0000:03:00.0/host5/target5:0:0/5:0:0:0/block/sdb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1095_3112_scsi_host_1_scsi_device_lun0'  (string)
  storage.removable = false  (bool)
  storage.media_check_enabled = false  (bool)
  storage.hotpluggable = false  (bool)
  storage.automount_enabled_hint = true  (bool)

---

### Post by lplo on 2010-07-30
... also the outputs of dmesg 1) after boot, 2) after  i unplug the sata drive and 3) after i plug in the drive back in. then it works fine.

1) boot with drive plugged in 
[   17.076086] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   17.076135] pci 0000:03:00.0: reg 10 io port: [0x00-0x07]
[   17.076144] pci 0000:03:00.0: reg 14 io port: [0x00-0x03]
[   17.076152] pci 0000:03:00.0: reg 18 io port: [0x00-0x07]
[   17.076161] pci 0000:03:00.0: reg 1c io port: [0x00-0x03]
[   17.076170] pci 0000:03:00.0: reg 20 io port: [0x00-0x0f]
[   17.076179] pci 0000:03:00.0: reg 24 32bit mmio: [0x000000-0x0001ff]
[   17.076188] pci 0000:03:00.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[   17.076216] pci 0000:03:00.0: supports D1 D2
[   17.121406] sata_sil 0000:03:00.0: version 2.4
[   17.121465] sata_sil 0000:03:00.0: enabling device (0000 -> 0003)
[   17.121480] sata_sil 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.121523] sata_sil 0000:03:00.0: cache line size not set.  Driver may not function
[   17.121531] sata_sil 0000:03:00.0: setting latency timer to 64
[   17.132105] scsi2 : sata_sil
[   17.137639] scsi3 : sata_sil
[   17.137773] ata3: SATA max UDMA/100 mmio m512@0x48000000 tf 0x48000080 irq 11
[   17.137779] ata4: SATA max UDMA/100 mmio m512@0x48000000 tf 0x480000c0 irq 11
[   17.460132] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   17.872165] ata3.00: NODEV after polling detection
[   17.880071] intel8x0_measure_ac97_clock: measured 55068 usecs (2653 samples)
[   17.880077] intel8x0: clocking to 48000
[   18.192055] ata4: SATA link down (SStatus 0 SControl 310)


2) unplugged drive
[  162.712883] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0xe frozen
[  162.712892] ata3: SError: { PHYRdyChg 10B8B }
[  162.712911] ata3: hard resetting link
[  163.436064] ata3: SATA link down (SStatus 0 SControl 310)
[  163.436087] ata3: EH complete


3) drive plugged back in 

[  213.614010] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[  213.614020] ata3: SError: { PHYRdyChg }
[  213.614039] ata3: hard resetting link
[  214.336078] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  214.352620] ata3.00: ATA-8: Hitachi HDS721010CLA332, JP4OA3EA, max UDMA/133
[  214.352625] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[  214.352658] ata3.00: Drive reports diagnostics failure. This may indicate a drive
[  214.352661] ata3.00: fault or invalid emulation. Contact drive vendor for information.
[  214.368609] ata3.00: configured for UDMA/100
[  214.368624] ata3: EH complete
[  214.368780] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[  214.370640] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  214.388295] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  214.388356] sd 2:0:0:0: [sdb] Write Protect is off
[  214.388361] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  214.388391] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  214.389511]  sdb: sdb1
[  214.402144] sd 2:0:0:0: [sdb] Attached SCSI disk

---

### Post by lplo on 2010-08-01
For completeness:

The solution, or better a crude work around was:

1) Compiling the kernel (2.6.32 - ubuntu 10.04 lucid lynx) with the following changes:
 - compile module siimage (depricated driver  silicon image sata chips)
 - enable deprecated sata support
     (device-drivers -ata/atapi/mfl/support ,deprecated, conflicts with libata)
 
2) "blacklist sata-sil" in /etc/modprobe.d/blacklist.conf

---

