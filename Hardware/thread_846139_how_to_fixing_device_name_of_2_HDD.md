---
title: "how to fixing device name of 2 HDD?"
date: 2008-07-01
forum: Hardware
---

### Post by frankxue on 2008-07-01
I have 2 Hitachi SATA HDD installed on my laptop, the OS is ubuntu 8.04.
I noticed the device name /dev/sda and /dev/sdb often point to different physics disk.
sometimes the device name of the 1st disk is /dev/sda, and sometime is /dev/sdb.
I wanna make the 1st disk device name to be /dev/sda and the 2nd disk device name to be /dev/sdb. But i don't know how to write udev rules to do it? Anybody can help me to do that? i will appreciate.

more details about my HDD:
------------------------------
**[COLOR="Red"]# udevinfo -a -p $(udevinfo -q path -n /dev/sda)[/COLOR]**
looking at device '/block/sda':
KERNEL=="sda"
SUBSYSTEM=="block"
DRIVER==""
ATTR{dev}=="8:0"
ATTR{range}=="16"
ATTR{removable}=="0"
ATTR{size}=="234441648"
ATTR{stat}==" 23792 21139 1412657 258864 13020 47176 482512 1108816 0 131040 1370616"
ATTR{capability}=="12"

looking at parent device '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0':
KERNELS=="0:0:0:0"
SUBSYSTEMS=="scsi"
DRIVERS=="sd"
ATTRS{device_blocked}=="0"
ATTRS{type}=="0"
ATTRS{scsi_level}=="6"
ATTRS{vendor}=="ATA "
**[COLOR="DarkGreen"]ATTRS{model}=="Hitachi HTS54251"[/COLOR]**
ATTRS{rev}=="BB2O"
ATTRS{state}=="running"
ATTRS{timeout}=="30"
ATTRS{iocounterbits}=="32"
ATTRS{iorequest_cnt}=="0x8fdc"
ATTRS{iodone_cnt}=="0x8fdc"
ATTRS{ioerr_cnt}=="0x0"
ATTRS{modalias}=="scsi:t-0x00"
ATTRS{evt_media_change}=="0"
ATTRS{queue_depth}=="31"
ATTRS{queue_type}=="simple"

looking at parent device '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0':
KERNELS=="target0:0:0"
SUBSYSTEMS==""
DRIVERS==""

looking at parent device '/devices/pci0000:00/0000:00:1f.2/host0':
KERNELS=="host0"
SUBSYSTEMS==""
DRIVERS==""

looking at parent device '/devices/pci0000:00/0000:00:1f.2':
KERNELS=="0000:00:1f.2"
SUBSYSTEMS=="pci"
DRIVERS=="ahci"
ATTRS{vendor}=="0x8086"
ATTRS{device}=="0x2829"
ATTRS{subsystem_vendor}=="0x17aa"
ATTRS{subsystem_device}=="0x20a7"
ATTRS{class}=="0x010601"
ATTRS{irq}=="218"
ATTRS{local_cpus}=="ff"
ATTRS{modalias}=="pci:v00008086d00002829sv000017AAsd000020A7bc01sc06i01"
ATTRS{enable}=="1"
ATTRS{broken_parity_status}=="0"
ATTRS{msi_bus}==""

looking at parent device '/devices/pci0000:00':
KERNELS=="pci0000:00"
SUBSYSTEMS==""
DRIVERS==""

[B][COLOR="Red"]
# udevinfo -a -p $(udevinfo -q path -n /dev/sdb)[/COLOR][/B]
looking at device '/block/sdb':
KERNEL=="sdb"
SUBSYSTEM=="block"
DRIVER==""
ATTR{dev}=="8:16"
ATTR{range}=="16"
ATTR{removable}=="0"
ATTR{size}=="234441648"
ATTR{stat}==" 727 14929 18557 5760 29 315 2752 64 0 3868 5824"
ATTR{capability}=="12"

looking at parent device '/devices/pci0000:00/0000:00:1f.1/host3/target3:0:0/3:0:0:0':
KERNELS=="3:0:0:0"
SUBSYSTEMS=="scsi"
DRIVERS=="sd"
ATTRS{device_blocked}=="0"
ATTRS{type}=="0"
ATTRS{scsi_level}=="6"
ATTRS{vendor}=="ATA "
**[COLOR="DarkGreen"]ATTRS{model}=="HITACHI HTS54161"[/COLOR]**
ATTRS{rev}=="SB3I"
ATTRS{state}=="running"
ATTRS{timeout}=="30"
ATTRS{iocounterbits}=="32"
ATTRS{iorequest_cnt}=="0x304"
ATTRS{iodone_cnt}=="0x304"
ATTRS{ioerr_cnt}=="0x0"
ATTRS{modalias}=="scsi:t-0x00"
ATTRS{evt_media_change}=="0"
ATTRS{queue_depth}=="1"
ATTRS{queue_type}=="none"

looking at parent device '/devices/pci0000:00/0000:00:1f.1/host3/target3:0:0':
KERNELS=="target3:0:0"
SUBSYSTEMS==""
DRIVERS==""

looking at parent device '/devices/pci0000:00/0000:00:1f.1/host3':
KERNELS=="host3"
SUBSYSTEMS==""
DRIVERS==""

looking at parent device '/devices/pci0000:00/0000:00:1f.1':
KERNELS=="0000:00:1f.1"
SUBSYSTEMS=="pci"
DRIVERS=="ata_piix"
ATTRS{vendor}=="0x8086"
ATTRS{device}=="0x2850"
ATTRS{subsystem_vendor}=="0x17aa"
ATTRS{subsystem_device}=="0x20a6"
ATTRS{class}=="0x01018a"
ATTRS{irq}=="20"
ATTRS{local_cpus}=="ff"
ATTRS{modalias}=="pci:v00008086d00002850sv000017AAsd000020A6bc01sc01i8a"
ATTRS{enable}=="1"
ATTRS{broken_parity_status}=="0"
ATTRS{msi_bus}==""

looking at parent device '/devices/pci0000:00':
KERNELS=="pci0000:00"
SUBSYSTEMS==""
DRIVERS==""

---

### Post by frankxue on 2008-07-04
ok, i solved this problem myself. mount partitions by UUID

#blkid
/dev/sda1: UUID="def36252-3c73-48f5-a773-a7a247105e31" TYPE="ext3" 
/dev/sda5: UUID="38F055B2F055775A" TYPE="ntfs" 
/dev/sda6: UUID="065C7AFD5C7AE739" TYPE="ntfs" 
/dev/sdb1: UUID="207F-9BB8" TYPE="vfat" 
/dev/sdb5: UUID="F4D82E47D82E0906" TYPE="ntfs" 
/dev/sdb6: UUID="C67C35B27C359DDD" TYPE="ntfs" 
/dev/sda2: UUID="db888983-1e19-4892-bca3-e6b8a42e7058" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="e69e5f87-1764-433d-bdf3-c097e3b9045c" 


#vi /etc/fstab
UUID=F4D82E47D82E0906           /media/diskd    ntfs-3g     user,iocharset=utf-8        0   0
UUID=C67C35B27C359DDD           /media/diske    ntfs-3g     user,iocharset=utf-8        0   0

UUID=38F055B2F055775A           /media/diskf    ntfs-3g     user,iocharset=utf-8        0   0
UUID=065C7AFD5C7AE739           /media/diskg    ntfs-3g     user,iocharset=utf-8        0   0

---

