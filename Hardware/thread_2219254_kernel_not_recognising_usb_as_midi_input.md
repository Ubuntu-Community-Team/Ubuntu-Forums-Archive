---
title: "kernel not recognising usb as midi input"
date: 2014-04-23
forum: Hardware
---

### Post by Richard_Hainsworth on 2014-04-23
I bought a Dream Cheeky USB Piano keyboard.
Before buying articles on MIDI devices over USB state that ALSA recognises USB Midi devices without extra drivers.
Plugged in keyboard, no reaction.
I have jackd running with qsynth. Got them working with Rosegarden.
Response from lsusb is:
lsusb
Bus 001 Device 012: ID 13d3:3375 IMC Networks Atheros AR3012 Bluetooth 4.0 Adapter
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 004: ID 064e:f300 Suyin Corp. UVC 0.3M Webcam
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 011: ID 1941:8021 Dream Link WH1080 Weather Station / USB Missile Launcher
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Response from acconnect is:
aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 131: 'rosegarden' [type=user]
    1 'sync out        '
    2 'external controller'
    3 'out 1 - MIDI input system device'

No Midi device is recognised.

The relevant bit from lsusb -v is
Bus 002 Device 011: ID 1941:8021 Dream Link WH1080 Weather Station / USB Missile Launcher
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1941 Dream Link
  idProduct          0x8021 WH1080 Weather Station / USB Missile Launcher
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
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
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
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
Device Status:     0x0000
  (Bus Powered)


Dream Cheeky also manufacture the usb controlled launcher and weather station. I have also found a link where a driver is given for the missile launcher. However, if the usb midi driver is so commonplace, is there a way to tell the kernel that this usb device is a midi one? At least for me.

I saw some lines about udev rules when I googled 1941:8021
I dont understand the rules or how to tell the kernel that the device is generating MIDI events.

---

