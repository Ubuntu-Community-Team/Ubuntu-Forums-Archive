---
title: "UPS Mustek 600 howto"
date: 2009-11-29
forum: Hardware
---

### Post by LimCore on 2009-11-29
Hi, I have an UPS Mustek 600 

I attach it via USB cable (this model has 2 connections, USB and serial).

The USB is seen as (dmesg)
usb 5-2: new low speed USB device using uhci_hcd and address 5
usb 5-2: configuration #1 chosen from 1 choice

input: Cypress Semiconductor USB to Serial as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input14

generic-usb 0003:0665:5161.000A: input,hidraw3: USB HID v1.00 Gamepad [Cypress Semiconductor USB to Serial] on usb-0000:00:1a.2-2/input0

$lsusb
[...]
Bus 005 Device 005: ID 0665:5161
[...]

How to get it working?

I do not see any /dev/tty for it... how to make one?

I tried following:
modprobe usbserial vendor=0x0665 product=0x5161
dmesg
  usbcore: registered new interface driver usbserial_generic
  usbserial: USB Serial Driver core 
but it does not seem to work?
for i in `seq 1 16` ; do mknod /dev/ttyUSB$i c 188 $i ; done
for i in `seq 1 16` ; do cat /dev/ttyUSB$i ; done
cat: /dev/ttyUSB1: No such device
[...]
cat: /dev/ttyUSB16: No such device

---

### Post by Alex22 on 2009-12-28
That's ok, your machine sees the UPS.

Now you need the program to control it. **Upsd** is the one for serial interface. To be found in repo. 

As for USB, i know **apcupsd**, but it's for UPS-es mady by APC company.

There is also a **NUT** project, but as i read, it hasn't got a big support for USB neither: 
```
apt-cache search ups|grep -i nut
```
[http://www.networkupstools.org/](http://www.networkupstools.org/)

General doc:
[http://tldp.org/HOWTO/UPS-HOWTO/index.html](http://tldp.org/HOWTO/UPS-HOWTO/index.html)

Good Luck

---

