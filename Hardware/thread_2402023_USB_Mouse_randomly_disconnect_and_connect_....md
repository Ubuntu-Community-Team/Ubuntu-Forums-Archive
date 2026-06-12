---
title: "USB Mouse randomly disconnect and connect ..."
date: 2018-09-25
forum: Hardware
---

### Post by LeXav on 2018-09-25
Hi !

My new usb mouse randomly connect and disconnect.
I tried some workaround ( usbcore.autosuspend=-1 and usbhid.quirks=0x0000:0x0538:0x00000400 ) but nothing worked.

Here the first lines of dmesg, regarding kernel option :

```

[    0.000000] microcode: microcode updated early to revision 0xa0b, date = 2010-09-28
[    0.000000] Linux version 4.15.0-35-generic (buildd@lcy01-amd64-024) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #38-Ubuntu SMP Wed Sep 12 10:38:24 UTC 2018 (Ubuntu 4.15.0-35.38-generic 4.15.18)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-35-generic root=UUID=27c3d96f-e891-4172-80c2-146b840bdffb ro quiet splash net.ifnames=0 usbcore.autosuspend=-1 usbhid.quirks=0x0000:0x0538:0x00000400
```

Here, lines from syslog when the mouse disconnect and connect again 

```
Sep 25 15:02:22 xav-serveur kernel: [  883.776095] usb 5-2: USB disconnect, device number 8
Sep 25 15:02:22 xav-serveur upowerd[3002]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/0003:0000:0538.0008
Sep 25 15:02:22 xav-serveur upowerd[3002]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0
Sep 25 15:02:22 xav-serveur upowerd[3002]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2
Sep 25 15:02:22 xav-serveur gnome-shell[2995]: g_array_unref: assertion 'array' failed
Sep 25 15:02:23 xav-serveur kernel: [  884.232025] usb 5-2: new low-speed USB device number 9 using uhci_hcd
Sep 25 15:02:23 xav-serveur kernel: [  884.417331] usb 5-2: New USB device found, idVendor=0000, idProduct=0538
Sep 25 15:02:23 xav-serveur kernel: [  884.417334] usb 5-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Sep 25 15:02:23 xav-serveur kernel: [  884.417337] usb 5-2: Product:  USB OPTICAL MOUSE
Sep 25 15:02:23 xav-serveur kernel: [  884.435927] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/0003:0000:0538.0009/input/input20
Sep 25 15:02:23 xav-serveur kernel: [  884.436166] hid-generic 0003:0000:0538.0009: input,hidraw2: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1a.2-2/input0
Sep 25 15:02:23 xav-serveur upowerd[3002]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/0003:0000:0538.0009
Sep 25 15:02:23 xav-serveur upowerd[3002]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0
Sep 25 15:02:23 xav-serveur upowerd[3002]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2
```

Here lsusb 

```
Bus 002 Device 002: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 004: ID 0cc2:d702 Timex Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 013: ID 0000:0538  
Bus 005 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. Keyboard (Labtec Ultra Flat Keyboard)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:0605 Hewlett-Packard ScanJet 2200c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lsusb -v ( only mouse )

```
Bus 005 Device 013: ID 0000:0538  
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0000 
  idProduct          0x0538 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
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
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      66
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
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval              10

```

Thanks for your help !
Xavier.

---

### Post by Autodave on 2018-09-25
Simple question: have you tried moving the receiver into a different port?  I am assuming that it is NOT plugged into a USB hub: that can cause problems especially if it is a non-powered hub.

---

### Post by LeXav on 2018-09-25
Yep, I've tried that and it is not plugged into a USB hub.... :(

---

