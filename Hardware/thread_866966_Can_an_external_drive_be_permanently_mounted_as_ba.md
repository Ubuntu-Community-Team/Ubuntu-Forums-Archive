---
title: "Can an external drive be permanently mounted as /backup?"
date: 2008-07-22
forum: Hardware
---

### Post by qwert231 on 2008-07-22
I just bought a USB 2.0 / eSATA External Hard Drive. 
([http://www.newegg.com/Product/Product.aspx?Item=N82E16822216041](http://www.newegg.com/Product/Product.aspx?Item=N82E16822216041))

I was able to format it as ext3.

Currently, until I get the eSATA cable I need, it is connected as USB.

This drive will be connected permanently, and I'd like it to be mounted as /backup at all times.

Where do I configure this? (Command prompt configuration is great if possible.)

---

### Post by Potatoj316 on 2008-07-22
Im quite certain that you have to edit the fstab to have drives auto-mount.

---

### Post by qwert231 on 2008-07-22
Ok, yes, that get's me in the right direction. But need more help.

Don't know if this helps:
root@linux800:/etc/udev/rules.d# udevinfo -a -p $(udevinfo -q path -n /dev/sdd1)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sdd/sdd1':
    KERNEL=="sdd1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{stat}=="    2698     5396 15463179 30926358"
    ATTR{size}=="1953520002"
    ATTR{start}=="63"
    ATTR{dev}=="8:49"

  looking at parent device '/block/sdd':
    KERNELS=="sdd"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{capability}=="12"
    ATTRS{stat}=="     296     3056     8677    10340   142851 15320325 30926414 1969224064        0 14293044 1969235064"
    ATTRS{size}=="1953525168"
    ATTRS{removable}=="0"
    ATTRS{range}=="16"
    ATTRS{dev}=="8:48"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/host6/target6:0:0/6:0:0:0':
    KERNELS=="6:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{iodone_cnt}=="0x22f32"
    ATTRS{iorequest_cnt}=="0x22f32"
    ATTRS{iocounterbits}=="32"
    ATTRS{timeout}=="30"
    ATTRS{state}=="running"
    ATTRS{rev}=="    "
    ATTRS{model}=="EACS-00ZJB0     "
    ATTRS{vendor}=="WDC WD10"
    ATTRS{scsi_level}=="3"
    ATTRS{type}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{queue_depth}=="1"
    ATTRS{device_blocked}=="0"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/host6/target6:0:0':
    KERNELS=="target6:0:0"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/host6':
    KERNELS=="host6"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{interface}=="Bulk Only Interface"
    ATTRS{modalias}=="usb:v0C0BpB159d0103dc00dsc00dp00ic08isc06ip50"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="00DE3752"
    ATTRS{product}=="External HDD"
    ATTRS{manufacturer}=="DMI"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="4"
    ATTRS{busnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0103"
    ATTRS{idProduct}=="b159"
    ATTRS{idVendor}=="0c0b"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}=="Bulk Only Configuration"
    ATTRS{dev}=="189:3"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:1f.2"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-15-generic uhci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:0"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2':
    KERNELS=="0000:00:1f.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{enable}=="1"
    ATTRS{modalias}=="pci:v00008086d00002442sv000010B7sd00000058bc0Csc03i00"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="3"
    ATTRS{class}=="0x0c0300"
    ATTRS{subsystem_device}=="0x0058"
    ATTRS{subsystem_vendor}=="0x10b7"
    ATTRS{device}=="0x2442"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

---

### Post by vanadium on 2008-07-22
An external drive will always mount automatically as soon as it is connected and powered. No need to use /etc/fstab. You may just let the automatic mounting do its job and create a symlink "/backup" to access the drive if you wish to access the drive this way.

---

### Post by qwert231 on 2008-07-22
NM, I did figure it out. I put the UUID info into fstab as well as /backup as my mount point, and though it didn't work the first time, (may have already been mounted) it works now.

---

### Post by vanadium on 2008-07-22
```
I put the UUID info into fstab as well as /backup as my mount point
```

Not the best solution for a removable drive.

---

