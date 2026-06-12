---
title: "FAQ adding rules in udev for my usb 8G to autorun rsync"
date: 2011-11-13
forum: Hardware
---

### Post by jao_madn on 2011-11-13
Hi,

I would like to ask if someone knows and show/point me or simple help me how udev rules work in lucyd, upon my quest and search all the tuts i used is based on old udev since something i read the udev change in lucyd version.. I want to accomplised when i plug my usb 8Gb device and automount kicks in mounted the usb in /media/sony storage and predefined rsync script must run. Im having problems udev function works for me..

Here some of my available info
> # udevadm info -a -p /block/sdc

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/host14/target14:0:0/14:0:0:0/block/sdc':
    KERNEL=="sdc"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="1"
    ATTR{ro}=="0"
    ATTR{size}=="15663104"
    ATTR{alignment_offset}=="0"
    ATTR{capability}=="53"
    ATTR{stat}=="     638    15675    44660     2284        4        4        8     1040        0     1876     3324"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/host14/target14:0:0/14:0:0:0':
    KERNELS=="14:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="0"
    ATTRS{vendor}=="Sony    "
    ATTRS{model}=="Storage Media   "
    ATTRS{rev}=="0100"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x5d0"
    ATTRS{iodone_cnt}=="0x5d0"
    ATTRS{ioerr_cnt}=="0x2"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/host14/target14:0:0':
    KERNELS=="target14:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/host14':
    KERNELS=="host14"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0':
    KERNELS=="2-1.4:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v054Cp0243d0100dc00dsc00dp00ic08isc06ip50"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4':
    KERNELS=="2-1.4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="200mA"
    ATTRS{urbnum}=="5005"
    ATTRS{idVendor}=="054c"
    ATTRS{idProduct}=="0243"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="7"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sony"
    ATTRS{product}=="Storage Media"
    ATTRS{serial}=="5A10101105904"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1':
    KERNELS=="2-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="126"
    ATTRS{idVendor}=="8087"
    ATTRS{idProduct}=="0020"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="25"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-36-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3b34"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x1c77"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00003B34sv00001043sd00001C77bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
> #lsusb
Bus 002 Device 010: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 002 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 003: ID 0461:4d0f Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 13d3:5120 IMC Networks 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
> # udevadm info -q all -n /dev/sdc1
P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/host14/target14:0:0/14:0:0:0/block/sdc/sdc1
N: sdc1
W: 67
S: block/8:33
S: disk/by-id/usb-Sony_Storage_Media_5A10101105904-0:0-part1
S: disk/by-path/pci-0000:00:1d.0-usb-0:1.4:1.0-scsi-0:0:0:0-part1
S: disk/by-uuid/D9F5-A516
S: disk/by-label/Sony\x208Gb
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/host14/target14:0:0/14:0:0:0/block/sdc/sdc1
E: MAJOR=8
E: MINOR=33
E: DEVNAME=/dev/sdc1
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_VENDOR=Sony
E: ID_VENDOR_ENC=Sony\x20\x20\x20\x20
E: ID_VENDOR_ID=054c
E: ID_MODEL=Storage_Media
E: ID_MODEL_ENC=Storage\x20Media\x20\x20\x20
E: ID_MODEL_ID=0243
E: ID_REVISION=0100
E: ID_SERIAL=Sony_Storage_Media_5A10101105904-0:0
E: ID_SERIAL_SHORT=5A10101105904
E: ID_TYPE=disk
E: ID_INSTANCE=0:0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usb-storage
E: ID_PATH=pci-0000:00:1d.0-usb-0:1.4:1.0-scsi-0:0:0:0
E: ID_PART_TABLE_TYPE=dos
E: ID_FS_LABEL=Sony_8Gb
E: ID_FS_LABEL_ENC=Sony\x208Gb
E: ID_FS_UUID=D9F5-A516
E: ID_FS_UUID_ENC=D9F5-A516
E: ID_FS_VERSION=FAT32
E: ID_FS_TYPE=vfat
E: ID_FS_USAGE=filesystem
E: UDISKS_PRESENTATION_NOPOLICY=0
E: UDISKS_PARTITION=1
E: UDISKS_PARTITION_SCHEME=mbr
E: UDISKS_PARTITION_NUMBER=1
E: UDISKS_PARTITION_TYPE=0x0b
E: UDISKS_PARTITION_SIZE=8011390464
E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/host14/target14:0:0/14:0:0:0/block/sdc
E: UDISKS_PARTITION_OFFSET=32256
E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
E: DEVLINKS=/dev/block/8:33 /dev/disk/by-id/usb-Sony_Storage_Media_5A10101105904-0:0-part1 /dev/disk/by-path/pci-0000:00:1d.0-usb-0:1.4:1.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/D9F5-A516 /dev/disk/by-label/Sony\x208Gb
MY RULES
> KERNEL=="sd[b-g]", SUBSYSTEMS=="scsi", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0243", RUN+="/home/magellan/myscripts/udev/my-book-udev.sh"
KERNEL=="sd[b-g]", SUBSYSTEMS=="usb", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0243", RUN+="/home/magellan/myscripts/udev/my-book-udev.sh"
#SUBSYSTEMS=="usb", ACTION=="add", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0243", RUN+="/home/magellan/myscripts/udev/my-book-udev.sh"
#SUBSYSTEMS=="block", ACTION=="add", ID_VENDOR=="Sony", ID_MODEL=="Storage_Media" , RUN+="/home/magellan/myscripts/udev/my-book-udev.sh"
#KERNEL=="sd[b-g], SUBSYSTEMS=="usb", ATTRS{Hope someone has valuable input they can share..

Thanks in advance..

---

