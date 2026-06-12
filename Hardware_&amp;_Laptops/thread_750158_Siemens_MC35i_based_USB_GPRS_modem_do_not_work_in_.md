---
title: "Siemens MC35i based USB GPRS modem do not work in Kubuntu 7.04 / 7.10"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by Heavy Rail on 2008-04-09
Hello world! I've got Siemens MC35i based USB GPRS modem

When I plugged it in the following have been appeared at dmesg output
```

[  414.841090] usb 2-1: new full speed USB device using uhci_hcd and address 4
[  415.009668] usb 2-1: configuration #1 chosen from 1 choice

```

lsusb output is as follows
```

Bus 002 Device 004: ID 10c4:8341 Cygnal Integrated Products, Inc.

```

Having seen that, I did
```

sudo modprobe cp2101

```

and got dmesg output such as
```

[  760.886297] usbcore: registered new interface driver usbserial
[  760.886314] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  760.975784] usbcore: registered new interface driver usbserial_generic
[  760.975792] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  760.984934] drivers/usb/serial/usb-serial.c: USB Serial support registered for cp2101
[  760.984973] usbcore: registered new interface driver cp2101
[  760.984976] drivers/usb/serial/cp2101.c: Silicon Labs CP2101/CP2102 RS232 serial adaptor driver v0.07

```
But from that output I wasn't able to realize what COM port does that USB-Serial adapter (bulit in the modem) have bounded to?
For sake of comparison, I've tried the simple standalone USB-Serial cable based on Prolific PL2303.
It has been detected instantly and even without any modprobes and so on - I just have it plugged in and got
```

[  903.202441] usb 2-2: new full speed USB device using uhci_hcd and address 6
[  903.357271] usb 2-2: configuration #1 chosen from 1 choice
[  903.418442] drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[  903.418700] pl2303 2-2:1.0: pl2303 converter detected
[  903.419082] usb 2-2: pl2303 converter now attached to ttyUSB0
[  903.419214] usbcore: registered new interface driver pl2303
[  903.419217] drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver

```
As one can see from this output, the PL2303 based cable has bound to /dev/ttyUSB0 instantly while the modem's USB-Serial adapted has not even after manual modprobe.
Please tell me how to attach such a device to my PC?

---

### Post by nemroot on 2008-07-21
recently I forced this modem to work by adding it's support in kernel.
it's easy.
cd /usr/src/linux/drivers/usb/serial
nano cp2101.c    find there a place with usb product and vendor id's and add string with your device numbers
{USB_DEVICE(0x10c4, 0x8341)}, /* siemens mc35pu gprs modem*/ 
Then recompile the kernel and reboot. Find new/dev/ttyUSB0 file :)

Norayr
---
norayr.livejournal.com

---

### Post by nemroot on 2008-07-21
recently I forced this modem to work by adding it's support in kernel.
it's easy.
cd /usr/src/linux/drivers/usb/serial
nano cp2101.c find there a place with usb product and vendor id's and add string with your device numbers
{USB_DEVICE(0x10c4, 0x8341)}, /* siemens mc35pu gprs modem*/ 
Then recompile the kernel and reboot. Find new/dev/ttyUSB0 file 

Norayr
---
norayr.livejournal.com

---

### Post by Heavy Rail on 2008-07-24
Thank you, Norayr!
It would be fine to include this patch in the official kernel.
What is the best way to post it to developers?

---

