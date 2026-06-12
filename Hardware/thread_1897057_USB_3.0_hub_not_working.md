---
title: "USB 3.0 hub not working"
date: 2011-12-18
forum: Hardware
---

### Post by Blinkiz on 2011-12-18
I got a new no name USB 3.0 hub that I have connected to my new Asus UX31 laptop. The hub is recognized in Ubuntu, but I can not get any devices to work with this hub.

```
root@lapasus:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 019: ID 2109:3431  
Bus 001 Device 003: ID 064e:f300 Suyin Corp. 
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 13d3:3375 IMC Networks 
```2109:3431 is the hub.
```
root@lapasus:~# lsusb -D /dev/bus/usb/002/023 
Device: ID 2109:3431  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x2109 
  idProduct          0x3431 
  bcdDevice            2.76
  iManufacturer           0 
  iProduct                1 USB2.0 Hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x00e9
    Per-port power switching
    Per-port overcurrent protection
    TT think time 32 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```I do not know why it does not show up as a USB 3.0 hub. If I boot into Windows 7 on the same computer, the hub is detected as 3.0 and the speed is great.

Please advice.
Ubuntu Desktop 11.10 64 bit, gnome-shell.

---

