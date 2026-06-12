---
title: "automount hotswap sata drive at startup"
date: 2012-07-23
forum: Hardware
---

### Post by spowel4 on 2012-07-23
I have a hot-swap sata drive bay, trayless, that accepts 2.5 inch hard drives which are mounted inside an enclosure that inserts & connects into the bay.  Currently, if the system reboots, the hard drive that's inserted into the drive bay is not recognized by the system until it's ejected & re-inserted, at which point it mounts to /dev/sdc1. I'd like to get the system to recognize & mount the drive automagically upon system restart but I don't know if a udev rule would handle that or if there might be some other way.
The output of udevadm info -a -p /sys/block/sdc is as follows:
```

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/host4/target4:0:0/4:0:0:0/block/sdc':
    KERNEL=="sdc"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="1465149168"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="52"
    ATTR{stat}=="      54       75      450      208        0        0        0        0        0      176      208"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/host4/target4:0:0/4:0:0:0':
    KERNELS=="4:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="WDC WD7500BPVT-0"
    ATTRS{rev}=="01.0"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x5b"
    ATTRS{iodone_cnt}=="0x5b"
    ATTRS{ioerr_cnt}=="0x9"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{unload_heads}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/host4/target4:0:0':
    KERNELS=="target4:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/host4':
    KERNELS=="host4"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0':
    KERNELS=="0000:03:01.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="sata_inic162x"
    ATTRS{vendor}=="0x1101"
    ATTRS{device}=="0x1622"
    ATTRS{subsystem_vendor}=="0x1101"
    ATTRS{subsystem_device}=="0x1622"
    ATTRS{class}=="0x010600"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00001101d00001622sv00001101sd00001622bc01sc06i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0':
    KERNELS=="0000:00:1e.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x244e"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060401"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

Can anyone offer some suggestions/tips?

---

