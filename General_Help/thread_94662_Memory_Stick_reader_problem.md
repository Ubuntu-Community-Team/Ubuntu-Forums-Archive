---
title: "Memory Stick reader problem"
date: 2005-11-24
forum: General Help
---

### Post by vyruss on 2005-11-24
I've got a **SanDisk MobileMate MS+ **memory stick reader, with a **FAT-formatted** **128mb Sony Memory Stick** which works perfectly in Windows XP (including under VMWare) and KNOPPIX 4.0.2 with no tweaks/drivers/whatsoever but stubbornly refuses to work with Ubuntu Breezy. It is not automounted, no icon pops up on the desktop, and I cannot mount it using either the msdos filesystem or vfat.

Before you ask, **no**, I cannot reformat it and frankly I shouldn't have to, because it works perfectly fine under other operating systems, including KNOPPIX Linux.

When I insert it, */dev/sda* gets created but no */dev/sda**X***.

I get this in **/var/log/syslog**:```

Nov 24 22:16:07 localhost kernel: [4456079.992000] usb 4-6: new high speed USB device using ehci_hcd and address 10
Nov 24 22:16:08 localhost kernel: [4456080.183000] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 24 22:16:08 localhost kernel: [4456080.205000] usb-storage: device found at 10
Nov 24 22:16:08 localhost kernel: [4456080.205000] usb-storage: waiting for device to settle before scanning
Nov 24 22:16:08 localhost usb.agent[15358]:      usb-storage: already loaded
Nov 24 22:16:08 localhost usb.agent[15440]:      usb-storage: already loaded
Nov 24 22:16:13 localhost kernel: [4456085.266000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
Nov 24 22:16:13 localhost kernel: [4456085.266000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Nov 24 22:16:16 localhost kernel: [4456088.416000] SCSI device sda: 253888 512-byte hdwr sectors (130 MB)
Nov 24 22:16:16 localhost kernel: [4456088.417000] sda: Write Protect is off
Nov 24 22:16:16 localhost kernel: [4456088.417000] sda: Mode Sense: 02 00 00 00
Nov 24 22:16:16 localhost kernel: [4456088.417000] sda: assuming drive cache: write through
Nov 24 22:16:16 localhost kernel: [4456088.436000] SCSI device sda: 253888 512-byte hdwr sectors (130 MB)
Nov 24 22:16:16 localhost kernel: [4456088.437000] sda: Write Protect is off
Nov 24 22:16:16 localhost kernel: [4456088.437000] sda: Mode Sense: 02 00 00 00
Nov 24 22:16:16 localhost kernel: [4456088.437000] sda: assuming drive cache: write through
Nov 24 22:16:23 localhost scsi.agent[15526]: Attribute /sys/devices/pci0000:00/0000:00:10.3/usb4/4-6/4-6:1.0/host2/target2:0:0/2:0:0:0/type does not exist
Nov 24 22:16:26 localhost scsi.agent[15567]: Attribute /sys/devices/pci0000:00/0000:00:10.3/usb4/4-6/4-6:1.0/host2/target2:0:0/2:0:0:0/type does not exist
Nov 24 22:18:16 localhost kernel: [4456088.437000]  /dev/scsi/host2/bus0/target0/lun0:<6>scsi: Device offlined - not ready after error recovery: host 2 channel 0 id 0 lun 0
Nov 24 22:18:16 localhost kernel: [4456208.643000] SCSI error : <2 0 0 0> return code = 0x50000
Nov 24 22:18:16 localhost kernel: [4456208.643000] end_request: I/O error, dev sda, sector 0
Nov 24 22:18:16 localhost kernel: [4456208.643000] Buffer I/O error on device sda, logical block 0
Nov 24 22:18:16 localhost kernel: [4456208.643000] usb 4-6: USB disconnect, address 10
Nov 24 22:18:16 localhost kernel: [4456208.643000] scsi2 (0:0): rejecting I/O to offline device
Nov 24 22:18:16 localhost kernel: [4456208.643000] Buffer I/O error on device sda, logical block 0
Nov 24 22:18:16 localhost kernel: [4456208.643000]  unable to read partition table
Nov 24 22:18:16 localhost kernel: [4456208.643000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Nov 24 22:18:16 localhost kernel: [4456208.666000] usb-storage: device scan complete
```
When I try pmount it (to /media/stick which I've created), I get a long wait and then:```
vyruss@gremlin:~$ pmount /dev/sda stick
mount: /dev/sda is not a valid block device
mount: /dev/sda is not a valid block device
```
**Other USB sticks **work perfectly on my machine with Breezy. What is the matter with these Sandisk card readers? I greatly suspect that this has something to do with it:```
Nov 24 22:16:23 localhost scsi.agent[15526]: Attribute /sys/devices/pci0000:00/0000:00:10.3/usb4/4-6/4-6:1.0/host2/target2:0:0/2:0:0:0/type does not exist
Nov 24 22:16:26 localhost scsi.agent[15567]: Attribute /sys/devices/pci0000:00/0000:00:10.3/usb4/4-6/4-6:1.0/host2/target2:0:0/2:0:0:0/type does not exist
```

Many thanks for taking the time to read this!

---

### Post by mlomker on 2005-11-24
I'm not sure of the answer, but I'm curious what **sudo fdisk -l** gives you when it is inserted.

---

### Post by vyruss on 2005-11-24
[QUOTE=mlomker]I'm not sure of the answer, but I'm curious what **sudo fdisk -l** gives you when it is inserted.[/QUOTE]

A long wait, then nothing!```
vyruss@gremlin:~$ sudo fdisk -l /dev/sda
Password:
vyruss@gremlin:~$
```

---

### Post by vyruss on 2005-11-29
Maybe this will help somebody figure out what's going on?```
vyruss@gremlin:/media$ udevinfo -a -p /sys/block/sda

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

device '/sys/block/sda' has major:minor 8:0
  looking at class device '/sys/block/sda':
    KERNEL=="sda"
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:0"
    SYSFS{range}=="16"
    SYSFS{removable}=="1"
    SYSFS{size}=="253888"
    SYSFS{stat}=="       0        0        8        0        0        0        0        0        1    68090    68090"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0/host5/target5:0:0/5:0:0:0':
    BUS==""
    ID=="5:0:0:0"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0/host5/target5:0:0':
    BUS==""
    ID=="target5:0:0"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0/host5':
    BUS==""
    ID=="host5"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0':
    BUS=="usb"
    ID=="4-5:1.0"
    DRIVER=="usb-storage"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="08"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="50"
    SYSFS{bInterfaceSubClass}=="06"
    SYSFS{bNumEndpoints}=="02"
    SYSFS{modalias}=="usb:v0781pA7A7d9144dc00dsc00dp00ic08isc06ip50"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.3/usb4/4-5':
    BUS=="usb"
    ID=="4-5"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPower}=="500mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="9144"
    SYSFS{bmAttributes}=="80"
    SYSFS{configuration}==""
    SYSFS{devnum}=="8"
    SYSFS{idProduct}=="a7a7"
    SYSFS{idVendor}=="0781"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="MobileMate MS+"
    SYSFS{serial}=="51662"
    SYSFS{speed}=="480"
    SYSFS{version}==" 2.00"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.3/usb4':
    BUS=="usb"
    ID=="usb4"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bDeviceProtocol}=="01"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0206"
    SYSFS{bmAttributes}=="e0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="1"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{manufacturer}=="Linux 2.6.12-10-k7 ehci_hcd"
    SYSFS{maxchild}=="6"
    SYSFS{product}=="VIA Technologies_ Inc. USB 2.0"
    SYSFS{serial}=="0000:00:10.3"
    SYSFS{speed}=="480"
    SYSFS{version}==" 2.00"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:10.3':
    BUS=="pci"
    ID=="0000:00:10.3"
    DRIVER=="ehci_hcd"
    SYSFS{class}=="0x0c0320"
    SYSFS{device}=="0x3104"
    SYSFS{irq}=="21"
    SYSFS{local_cpus}=="1"
    SYSFS{modalias}=="pci:v00001106d00003104sv000017F2sd00003104bc0Csc03i20"
    SYSFS{subsystem_device}=="0x3104"
    SYSFS{subsystem_vendor}=="0x17f2"
    SYSFS{vendor}=="0x1106"

  looking at the device chain at '/sys/devices/pci0000:00':
    BUS==""
    ID=="pci0000:00"
    DRIVER=="unknown"
```

---

### Post by mlomker on 2005-11-30
I think you should file a ticket on Bugzilla.  The output should be helpful to a programmer, but most of us on here are end-users as well.

---

