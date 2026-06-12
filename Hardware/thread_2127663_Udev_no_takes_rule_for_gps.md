---
title: "Udev: no takes rule for gps"
date: 2013-03-20
forum: Hardware
---

### Post by themaxxx on 2013-03-20
I'm trying to create a udev rule for a GPS. I tried several ways but can not get the device to be captured by the rule:

lsusb:

Bus 002 Device 007: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port


```
TTRS{urbnum}=="20"
    ATTRS{idVendor}=="067b"
    ATTRS{idProduct}=="2303"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="7"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Prolific Technology Inc."
    ATTRS{product}=="USB-Serial Controller"

  looking at parent device '/devices/pci0000:00/0000:00:10.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="157"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-34-generic-pae uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:10.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:10.0':
    KERNELS=="0000:00:10.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x3038"
    ATTRS{subsystem_vendor}=="0x1106"
    ATTRS{subsystem_device}=="0x3038"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00001106d00003038sv00001106sd00003038bc0Csc03i00"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS=="
```

i tried with these rules, i tried With These rules, but none works:

```
#DRIVERS=="sierra",SUBSYSTEMS=="usb",ATTRS{bInterfaceNumber}=="03",SYMLINK="ttyACM10"
#DRIVERS=="pl2303",SUBSYSTEMS=="usb-serial",ATTRS{idVendor}=="067b",ATTRS{idProduct}=="2303",ATTRS{bInterfaceNumber}=="00",SYMLINK="ttyGPS"
#DRIVERS=="pl2303",SUBSYSTEMS=="usb-serial",ATTRS{idVendor}=="067b",ATTRS{idProduct}=="2303",ATTRS{manufacturer}=="Prolific Technology Inc.",ATTRS{port_number}=="0",SYMLINK="ttyGPS"
#DRIVERS=="pl2303",SUBSYSTEM == "usb-serial", ATTRS{serial}=="0000:00:10.0", SYMLINK="ttyAGSP"
#DRIVERS=="pl2303",SUBSYSTEM=="tty"ATTRS{idVendor}=="067b",ATTRS{idProduct}=="2303",ATTRS{serial}=="0000:00:10.0",SYMLINK="ttyGPS"
```

the system ever generate the following symlink:

```
[ 4516.789581] pl2303 2-1:1.0: pl2303 converter detected
[ 4516.803239] usb 2-1: pl2303 converter now attached to ttyUSB0
```

Any fix to it?

Thanks in advance!

---

