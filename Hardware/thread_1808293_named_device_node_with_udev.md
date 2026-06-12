---
title: "named device node with udev"
date: 2011-07-20
forum: Hardware
---

### Post by zukro on 2011-07-20
Hi there, I have a USB modem and I want to name its device node to certain name(i.e:m1306b), because the USB Modem will be used by a program (gammu), that required device node to be fixed. i have try to do this by adding udev rules files, but device node name still the same.

Step by step, what i've done=  

1. i create rules file by entering rules.d directory

$cd /etc/udev/rules.d/

2.create file named 10-local.rules

$sudo gedit 10-local.rules

3. finding sysfs device path using:
$dmesg
result:
[  937.022187] usb 7-2: pl2303 converter now attached to ttyUSB0

$udevadm info -q path -n /dev/ttyUSB0
result:
/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/ttyUSB0/tty/ttyUSB0

$udevadm info -a -p
/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/ttyUSB0/tty/ttyUSB0
result:

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

 looking at device
'/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/ttyUSB0/tty/ttyUSB0':
   KERNEL=="ttyUSB0"
   SUBSYSTEM=="tty"
   DRIVER==""

 looking at parent device
'/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/ttyUSB0':
   KERNELS=="ttyUSB0"
   SUBSYSTEMS=="usb-serial"
   DRIVERS=="pl2303"
   ATTRS{port_number}=="0"

 looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0':
   KERNELS=="7-2:1.0"
   SUBSYSTEMS=="usb"
   DRIVERS=="pl2303"
   ATTRS{bInterfaceNumber}=="00"
   ATTRS{bAlternateSetting}==" 0"
   ATTRS{bNumEndpoints}=="03"
   ATTRS{bInterfaceClass}=="ff"
   ATTRS{bInterfaceSubClass}=="00"
   ATTRS{bInterfaceProtocol}=="00"
   ATTRS{supports_autosuspend}=="1"

 looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb7/7-2':
   KERNELS=="7-2"
   SUBSYSTEMS=="usb"
   DRIVERS=="usb"
   ATTRS{configuration}==""
   ATTRS{bNumInterfaces}==" 1"
   ATTRS{bConfigurationValue}=="1"
   ATTRS{bmAttributes}=="a0"
   ATTRS{bMaxPower}=="100mA"
   ATTRS{urbnum}=="20"
   ATTRS{idVendor}=="067b"
   ATTRS{idProduct}=="2303"
   ATTRS{bcdDevice}=="0300"
   ATTRS{bDeviceClass}=="00"
   ATTRS{bDeviceSubClass}=="00"
   ATTRS{bDeviceProtocol}=="00"
   ATTRS{bNumConfigurations}=="1"
   ATTRS{bMaxPacketSize0}=="64"
   ATTRS{speed}=="12"
   ATTRS{busnum}=="7"
   ATTRS{devnum}=="3"
   ATTRS{devpath}=="2"
   ATTRS{version}==" 1.10"
   ATTRS{maxchild}=="0"
   ATTRS{quirks}=="0x0"
   ATTRS{avoid_reset_quirk}=="0"
   ATTRS{authorized}=="1"
   ATTRS{manufacturer}=="Prolific Technology Inc."
   ATTRS{product}=="USB-Serial Controller"

 looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb7':
   KERNELS=="usb7"
   SUBSYSTEMS=="usb"
   DRIVERS=="usb"
   ATTRS{configuration}==""
   ATTRS{bNumInterfaces}==" 1"
   ATTRS{bConfigurationValue}=="1"
   ATTRS{bmAttributes}=="e0"
   ATTRS{bMaxPower}=="  0mA"
   ATTRS{urbnum}=="60"
   ATTRS{idVendor}=="1d6b"
   ATTRS{idProduct}=="0001"
   ATTRS{bcdDevice}=="0206"
   ATTRS{bDeviceClass}=="09"
   ATTRS{bDeviceSubClass}=="00"
   ATTRS{bDeviceProtocol}=="00"
   ATTRS{bNumConfigurations}=="1"
   ATTRS{bMaxPacketSize0}=="64"
   ATTRS{speed}=="12"
   ATTRS{busnum}=="7"
   ATTRS{devnum}=="1"
   ATTRS{devpath}=="0"
   ATTRS{version}==" 1.10"
   ATTRS{maxchild}=="2"
   ATTRS{quirks}=="0x0"
   ATTRS{avoid_reset_quirk}=="0"
   ATTRS{authorized}=="1"
   ATTRS{manufacturer}=="Linux 2.6.38-8-generic uhci_hcd"
   ATTRS{product}=="UHCI Host Controller"
   ATTRS{serial}=="0000:00:1d.2"
   ATTRS{authorized_default}=="1"

 looking at parent device '/devices/pci0000:00/0000:00:1d.2':
   KERNELS=="0000:00:1d.2"
   SUBSYSTEMS=="pci"
   DRIVERS=="uhci_hcd"
   ATTRS{vendor}=="0x8086"
   ATTRS{device}=="0x2832"
   ATTRS{subsystem_vendor}=="0x1025"
   ATTRS{subsystem_device}=="0x011d"
   ATTRS{class}=="0x0c0300"
   ATTRS{irq}=="18"
   ATTRS{local_cpus}=="ff"
   ATTRS{local_cpulist}=="0-7"
   ATTRS{dma_mask_bits}=="32"
   ATTRS{consistent_dma_mask_bits}=="32"
   ATTRS{broken_parity_status}=="0"
   ATTRS{msi_bus}==""

 looking at parent device '/devices/pci0000:00':
   KERNELS=="pci0000:00"
   SUBSYSTEMS==""
   DRIVERS==""

4.using that information above i create rule files, e.g:

SUBSYSTEM=="tty", ATTRS{manufacturer}=="Prolific Technology Inc.",
DRIVERS=="pl2303", NAME="m1306b"

5.and then trigger udev:

$ sudo service udev start 

6. when i check with $dmesg, device node still the same. 

anyone can show me what i miss here?

---

### Post by gzarkadas on 2011-07-21
You use fields from more than one from the parent entries. This does not work; you are only allowed to use fields from the device entry (the top-most block of `udevadm info -a -p ...') and one (and only one) of the parent blocks.  See [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) for more information.  Also, it is usually better to add a symlink to the device instead of changing its name. So your rule could be the following:

```

KERNEL=="ttyUSB0",ATTRS{idVendor}=="067b",ATTRS{idProduct}=="2303",ATTRS{bcdDevice}=="0300",ATTRS{manufacturer}=="Prolific Technology Inc.",ATTRS{product}=="USB-Serial Controller",SYMLINK+="m1306b"

```Try it; if it does not work, read the above link and tweak accordingly.

---

### Post by sisco311 on 2011-07-21
udev also creates symliks by default to some of the devices:
```
find /dev -lname '*ttyUSB0'
```

---

