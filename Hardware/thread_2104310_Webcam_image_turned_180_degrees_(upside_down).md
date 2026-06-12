---
title: "Webcam image turned 180 degrees (upside down)"
date: 2013-01-12
forum: Hardware
---

### Post by Carmageddon on 2013-01-12
This is a repost from thread [http://ubuntuforums.org/showthread.php?p=12451696](http://ubuntuforums.org/showthread.php?p=12451696) which was locked as being absolete.

I have someone with similar issue where the webcam output is flipped upside down, and even the windows drivers didn't always work.
The model is Asus K52F.

I have Ubuntu 12.04LTS installed.

This is the output of the new udevinfo(today it is udevadm info):

```
sasa@sasa-K52F:~/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;$ udevadm info --query=all --name=/dev/video0 --attribute-walk

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="USB 2.0 Camera"
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0':
    KERNELS=="1-1.2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="uvcvideo"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="0e"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{iad_bFirstInterface}=="00"
    ATTRS{iad_bInterfaceCount}=="02"
    ATTRS{iad_bFunctionClass}=="0e"
    ATTRS{iad_bFunctionSubClass}=="03"
    ATTRS{iad_bFunctionProtocol}=="00"
    ATTRS{interface}=="USB Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2':
    KERNELS=="1-1.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="957134"
    ATTRS{idVendor}=="13d3"
    ATTRS{idProduct}=="5130"
    ATTRS{bcdDevice}=="1211"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="4"
    ATTRS{devpath}=="1.2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sonix Technology Co., Ltd."
    ATTRS{product}=="USB 2.0 Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="249"
    ATTRS{idVendor}=="8087"
    ATTRS{idProduct}=="0020"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="128"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-29-generic-pae ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1a.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0':
    KERNELS=="0000:00:1a.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3b3c"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x1f27"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""
    ATTRS{uframe_periodic_max}=="100"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""

```

---

