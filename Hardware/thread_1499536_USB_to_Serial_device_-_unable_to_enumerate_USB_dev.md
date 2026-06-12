---
title: "USB to Serial device - unable to enumerate USB device"
date: 2010-06-02
forum: Hardware
---

### Post by stignz on 2010-06-02
Hey there,

Slightly new to ubuntu. 

Anyway, I've purchased a 'USB to Serial Port' cable that ubuntu can't seem to detect properly. Using this for minicom and debugging as i'm doing some embedded development.

The device is chinese made, its labeled HL-2303. but i think on ebay they call it HL-340. I'm not sure if they're exactly the same thing. Anyway.

The dmesg im getting:


[ 6855.428125] usb 3-1: device descriptor read/64, error -71
[ 6855.652135] usb 3-1: device descriptor read/64, error -71
[ 6855.868139] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 6855.988132] usb 3-1: device descriptor read/64, error -71
[ 6856.212124] usb 3-1: device descriptor read/64, error -71
[ 6856.428126] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 6856.836112] usb 3-1: device not accepting address 4, error -71
[ 6856.948139] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 6857.356106] usb 3-1: device not accepting address 5, error -71
[ 6857.356141] hub 3-0:1.0: unable to enumerate USB device on port 1

lsusb doesnt show any changes when i plug or unplug the device. 

I've searched all over for a solution but came up with nothing so I'm hopping someone can please lend me a hand here

Cheers guys

---

### Post by schrauberfuchs on 2011-06-21
Exactly the same issue: minicom + b?**dy-China:twisted: USB-RS232 Converter.
Using Ubuntu 10.04.2

syslog gives:
Jun 21 11:53:05 x-laptop kernel: [ 3976.984134] usb 2-2: new full speed USB device using uhci_hcd and address 9
Jun 21 11:53:05 x-laptop kernel: [ 3977.392051] usb 2-2: device not accepting address 9, error -71

lsusb gives:
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

No listing of the connected device. An other USB-RS232-converter-device (different modell) works fine...
May God prevent me from buying chinese so called "quality"[-o< ...
cheers!

---

