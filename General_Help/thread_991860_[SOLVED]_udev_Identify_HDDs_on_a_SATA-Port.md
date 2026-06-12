---
title: "[SOLVED] udev: Identify HDDs on a SATA-Port"
date: 2008-11-24
forum: General Help
---

### Post by pred2k on 2008-11-24
I want to idenfiy the Hard Disc Drives that i but in my Removable Harddisk Drawer about the SATA-Port where it is connected to.

When i put a HDD in the Drawer /var/log/messages shows this:
```
Nov 22 16:03:50 ubunas kernel: [ 3848.355633] ata6: hard resetting link
Nov 22 16:03:56 ubunas kernel: [ 3854.440056] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 22 16:03:56 ubunas kernel: [ 3854.443311] ata6.00: ATA-7: SAMSUNG SP2504C, VT100-50, max UDMA7
Nov 22 16:03:56 ubunas kernel: [ 3854.443316] ata6.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Nov 22 16:03:56 ubunas kernel: [ 3854.463114] ata6.00: configured for UDMA/133
Nov 22 16:03:56 ubunas kernel: [ 3854.463124] ata6: EH complete
Nov 22 16:03:56 ubunas kernel: [ 3854.463217] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
Nov 22 16:03:56 ubunas kernel: [ 3854.464396] sd 5:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 22 16:03:56 ubunas kernel: [ 3854.464418] sd 5:0:0:0: [sdf] Write Protect is off
Nov 22 16:03:56 ubunas kernel: [ 3854.464448] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 16:03:56 ubunas kernel: [ 3854.464536] sd 5:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 22 16:03:56 ubunas kernel: [ 3854.464551] sd 5:0:0:0: [sdf] Write Protect is off
Nov 22 16:03:56 ubunas kernel: [ 3854.464582] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 16:03:56 ubunas kernel: [ 3854.464585]  sdf: unknown partition table
Nov 22 16:03:56 ubunas kernel: [ 3854.470876] sd 5:0:0:0: [sdf] Attached SCSI disk
Nov 22 16:03:56 ubunas kernel: [ 3854.470990] sd 5:0:0:0: Attached scsi generic sg5 type 0
```
Looks like sd 5 and 5:0:0:0 is the name of the SATA-Port

udevinfo for the inserted HDD:
```
looking at device '/devices/pci0000:00/0000:00:1f.2/host5/target5:0:0/5:0:0:0/block/sdf':
    KERNEL=="sdf"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="488397168"
    ATTR{capability}=="12"
    ATTR{stat}=="      17       70      696       40        0        0        0        0        0       40       40"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host5/target5:0:0/5:0:0:0/block':
    KERNELS=="block"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host5/target5:0:0/5:0:0:0':
    KERNELS=="5:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="SAMSUNG SP2504C "
    ATTRS{rev}=="VT10"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x20"
    ATTRS{iodone_cnt}=="0x20"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="31"
    ATTRS{queue_type}=="simple"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host5/target5:0:0':
    KERNELS=="target5:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/host5':
    KERNELS=="host5"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2':
    KERNELS=="0000:00:1f.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ahci"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2922"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{subsystem_device}=="0xb005"
    ATTRS{class}=="0x010601"
    ATTRS{irq}=="2300"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00008086d00002922sv00001458sd0000B005bc01sc06i01"
    ATTRS{numa_node}=="0"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```
again: occurrence of the number "5".

The Removable Harddisk Drawer is connected to the 6th SATA-Port. I think Linux starts the counting of the Ports with zero.

I dont know about which attribute i should idenfy the Harddrives.
```
SUBSYSTEMS=="scsi", KERNEL=="sd?", SYMLINK+="Drawer"
```

KERNELS=="5:0:0:0" or KERNELS=="target5:0:0" or KERNELS=="host5" ? What is possible? There are no Infos about this in the documentation.

---

### Post by bapoumba on 2008-11-24
Moved to General Help, and bumped :)

---

### Post by pred2k on 2008-11-27
i used this rules now:
```
SUBSYSTEMS=="scsi", KERNELS=="host5", SYMLINK+="Drawer"
```
 ... and everthing look fine. \\:D/

---

