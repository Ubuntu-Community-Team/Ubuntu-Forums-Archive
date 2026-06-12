---
title: "3+ Smargo cardreader udev rule"
date: 2009-10-12
forum: Hardware
---

### Post by Termi11 on 2009-10-12
Hello,
i have 3 (soon 5) Smargo card reader on my Linux server (ubuntu 8.10)

> [   13.462082] usbcore: registered new interface driver usbserial
[   13.462140] usbserial: USB Serial support registered for generic
[   13.462228] usbcore: registered new interface driver usbserial_generic
[   13.462233] usbserial: USB Serial Driver core
[   13.547759] usbserial: USB Serial support registered for FTDI USB Serial Device
[   13.547829] ftdi_sio 4-3.2:1.0: FTDI USB Serial Device converter detected
[   13.547895] ftdi_sio: Detected FT232BM
[   13.548334] usb 4-3.2: FTDI USB Serial Device converter now attached to ttyUSB0
[   13.548369] ftdi_sio 2-2.2:1.0: FTDI USB Serial Device converter detected
[   13.548435] ftdi_sio: Detected FT232BM
[   13.548766] usb 2-2.2: FTDI USB Serial Device converter now attached to ttyUSB1
[   13.548795] ftdi_sio 2-2.3:1.0: FTDI USB Serial Device converter detected
[   13.548861] ftdi_sio: Detected FT232BM
[   13.549141] usb 2-2.3: FTDI USB Serial Device converter now attached to ttyUSB2
[   13.549176] usbcore: registered new interface driver ftdi_sio
[   13.549181] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver


Sometimes, when i reboot the server, the card readers are detected in a different order, so that the card in reader1 gets different parameters than needed.

Is there a way to specifiy the /dev/ttyUSBx to a port/USB device:

> root@server:/home/xxx# lsusb
Bus 004 Device 006: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 008: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 007: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:c30a Logitech, Inc. iTouch Composite
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I know how to address the device using the vendor, but as the vendor and product is always the same, i can't use only those parms.

Thanks

---

### Post by lswb on 2009-10-12
If the devices have some kind of unique serial number available to hal/udev, a udev rule can be written. There are some good tutorials on the web that explain how to do so better than I can. There is an art to getting it right and it usually takes some trial and error.

If your card readers are used to mount a card as disk or mass storage device, perhaps an easier solution is to mount them from /etc/fstab using either a uuid or a volume label. Then it won't matter which usb bus ID they get at boot.

---

### Post by Termi11 on 2009-10-12
The device does not have a unique serial number :-(

I have seen somewhere a parameter PLACE for udev.
> PLACE
    Match the topological position on bus, like physical port of USB device 

Can't i use this parm to place the /dev/ttyUSBx device

As it's a USB2serial adapter, mounting not possible ;-)

Thanks!
> root@server:/usr/bin# udevinfo -a -p $(udevinfo -q path -n /dev/ttyUSB0)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:10.4/usb4/4-3/4-3.2/4-3.2:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:10.4/usb4/4-3/4-3.2/4-3.2:1.0/ttyUSB0/tty':
    KERNELS=="tty"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:10.4/usb4/4-3/4-3.2/4-3.2:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="ftdi_sio"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:10.4/usb4/4-3/4-3.2/4-3.2:1.0':
    KERNELS=="4-3.2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ftdi_sio"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{modalias}=="usb:v0403p6001d0400dc00dsc00dp00icFFiscFFipFF"
    ATTRS{interface}=="USB smartcard server"

  looking at parent device '/devices/pci0000:00/0000:00:10.4/usb4/4-3/4-3.2':
    KERNELS=="4-3.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="935877"
    ATTRS{idVendor}=="0403"
    ATTRS{idProduct}=="6001"
    ATTRS{bcdDevice}=="0400"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="6"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:10.4/usb4/4-3':
    KERNELS=="4-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="29"
    ATTRS{idVendor}=="05e3"
    ATTRS{idProduct}=="0608"
    ATTRS{bcdDevice}=="0901"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="4"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{product}=="USB2.0 Hub"

  looking at parent device '/devices/pci0000:00/0000:00:10.4/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized_default}=="1"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="58"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.27-7-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:10.4"

  looking at parent device '/devices/pci0000:00/0000:00:10.4':
    KERNELS=="0000:00:10.4"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x3104"
    ATTRS{subsystem_vendor}=="0x1106"
    ATTRS{subsystem_device}=="0x3104"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="22"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00001106d00003104sv00001106sd00003104bc0Csc03i20"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

root@server:/usr/bin#


---

### Post by Termi11 on 2009-10-13
All 3 cardreaders are exactly the same! Only the Bus and Device changes.
So is it possible to tell udev to create the /dev/ttyUSBx device for each Bus:Device ?
Thanks !


Bus 004 Device 006: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0x6001 FT232 USB-Serial (UART) IC
  bcdDevice            4.00
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 USB smartcard server
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 01 01 01
      ** UNRECOGNIZED:  04 24 02 07
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
root@server:/etc/udev/rules.d#

---

