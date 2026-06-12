---
title: "Unable to turn bluetooth on"
date: 2017-12-07
forum: Hardware
---

### Post by fanialivio on 2017-12-07
I received today a Zienstar mini keyboard with bluetooth connection, but I realized that I cannot activate bluetooth in settings (grayed button).

I tried : 

[COLOR=#000000][FONT=&amp]bluetoothctl

[/FONT][/COLOR]Output :

Waiting to connect to bluetoothd...

I tried :

sudo rfkill unblock bluetooth

Same issue.

Does anybody know how to solve it please ?

Thank you very much

---

### Post by Yellow Pasque on 2017-12-08
What bluetooth adapter are you using? Check lsusb (assuming adapter is an internal or external USB device).

---

### Post by fanialivio on 2017-12-10
Bus 003 Device 003: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard

---

### Post by fanialivio on 2017-12-10
Sorry, I double checked and I discovered that what I wrote was my usb keyboard (not the bluetooth one), the real output for lsusb is :

Bus 003 Device 006: ID 248a:8367

---

### Post by fanialivio on 2017-12-10
lsusb -v 

Bus 003 Device 008: ID 248a:8367  
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x248a 
  idProduct          0x8367 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     142
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

---

### Post by fanialivio on 2017-12-10
Actually. The device problem was solved by installing bluetooth and blueman packages from repositories. In the settings the bluetooth button is still (and always) switched off, which I don't understand, but the keyboard is finally working.

Thank you

---

