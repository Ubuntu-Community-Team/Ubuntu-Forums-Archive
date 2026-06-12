---
title: "Nikon Coolscan 4000 ED, 10.10, udev..."
date: 2010-11-02
forum: Hardware
---

### Post by effraie on 2010-11-02
Hello,

Fervent ubuntu user and digital photographer, i scan 35mm films on Ubuntu, using Nikon Coolscan LS-4000 ED, and Vuescan.

I experienced no problem with 9.10 and 10.4, but since 10.10, neither Vuescan nor Sane would detect my coolscan, until i start them with sudo, or i chmod 777 /dev/sg2

I think the problem could easyly be solved by editing an udev file, but udev is a mess to me, so if somebody could help me...

here are some datas : 

```

19:01 mathieu@vian ~% lsscsi -g     
[0:0:0:0]    disk    ATA      TOSHIBA MK1637GS DL04  /dev/sda  /dev/sg0
[1:0:0:0]    cd/dvd  TSSTcorp DVD+-RW TS-L632D DE04  /dev/sr0  /dev/sg1
[4:0:0:0]    scanner Nikon    LS-4000 ED       1.06  -         /dev/sg2

```

```

19:00 mathieu@vian ~% udevadm info -a -p /sys/class/scsi_generic/sg2

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/fw1/fw1.0/host4/target4:0:0/4:0:0:0/scsi_generic/sg2':
    KERNEL=="sg2"
    SUBSYSTEM=="scsi_generic"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/fw1/fw1.0/host4/target4:0:0/4:0:0:0':
    KERNELS=="4:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="6"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="Nikon   "
    ATTRS{model}=="LS-4000 ED      "
    ATTRS{rev}=="1.06"
    ATTRS{state}=="running"
    ATTRS{timeout}=="0"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x12b"
    ATTRS{iodone_cnt}=="0x12b"
    ATTRS{ioerr_cnt}=="0x30"
    ATTRS{modalias}=="scsi:t-0x06"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{ieee1394_id}=="0090b54001ffffff:00042c:0000"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/fw1/fw1.0/host4/target4:0:0':
    KERNELS=="target4:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/fw1/fw1.0/host4':
    KERNELS=="host4"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/fw1/fw1.0':
    KERNELS=="fw1.0"
    SUBSYSTEMS=="firewire"
    DRIVERS=="sbp2"
    ATTRS{modalias}=="ieee1394:ven000090B5mo00004001sp0000609Ever00010483"
    ATTRS{rom_index}=="11"
    ATTRS{specifier_id}=="0x00609e"
    ATTRS{version}=="0x010483"
    ATTRS{model}=="0x004001"
    ATTRS{model_name}=="LS-4000 ED"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/fw1':
    KERNELS=="fw1"
    SUBSYSTEMS=="firewire"
    DRIVERS==""
    ATTRS{guid}=="0x0090b54001ffffff"
    ATTRS{units}=="0x00609e:0x010483"
    ATTRS{vendor}=="0x0090b5"
    ATTRS{hardware_version}=="0x00500a"
    ATTRS{vendor_name}=="Nikon"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:03:01.0':
    KERNELS=="0000:03:01.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="firewire_ohci"
    ATTRS{vendor}=="0x1180"
    ATTRS{device}=="0x0832"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x01bd"
    ATTRS{class}=="0x0c0010"
    ATTRS{irq}=="19"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00001180d00000832sv00001028sd000001BDbc0Csc00i10"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0':
    KERNELS=="0000:00:1e.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2448"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x01bd"
    ATTRS{class}=="0x060401"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00008086d00002448sv00001028sd000001BDbc06sc04i01"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by chideock on 2010-11-02
Read this
[http://jhansonxi.blogspot.com/2009/08/writing-udev-rules-to-get-scsi-scanner.html](http://jhansonxi.blogspot.com/2009/08/writing-udev-rules-to-get-scsi-scanner.html)

also google "Howto: UDEV/SCSI Scanner Configuration" this is an Ubuntu doc in Tutorials & Tips

I got mine to work but I don't like the XSane interface

I suppose you have checked the driver in /etc/sane.d/dll.conf
check cat /proc/scsi/scsi
check blkid
also read udev manual
[http://ubuntuforums.org/showthread.php?t=168221&highlight=nikon](http://ubuntuforums.org/showthread.php?t=168221&highlight=nikon)

---

### Post by effraie on 2010-11-05
i just tried this rule :

```
0:02 mathieu@vian ~% cat /etc/udev/rules.d/45-scsi-scanner.rules 

Datassions for Nikon 4000 ED scanner
SUBSYSTEM=="scsi_generic",ATTRS{vendor}=="Nikon   ",ATTRS{model}=="LS-4000 ED      ", NAME="%k", SYMLINK="scanner%n", MODE="0660", GROUP="scanner"

```

but it still does not work...

---

### Post by chideock on 2010-11-05
Two points.
Do you have the scanner driver selected in the dll.conf file (I hope that's the right file)? Check the sane.d manual pages. I'm not at the same place as my info on this.
If you have Epson scanners or HP scanners loaded into your OS then you will not get the Nikon to work. Not compatible to be loaded on the same system.

---

