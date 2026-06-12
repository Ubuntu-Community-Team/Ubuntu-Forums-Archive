---
title: "Initiating any webcam software leads to system freeze"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by Koobi on 2006-02-23
if i ever start up any webcam realated software such as camorama or even test the webcam via GnomeMeeting, the entire system freezes and the only thing i can do is to restart my PC manually via the power button.


i'm trying to get my Intel Easy PC Camera CS110 webcam working on skype...i hope V4L has support for it.


maybe this will help:
> 
koobi@koobi:~ $ dmesg | grep USB
[4294669.341000] PCI0 PCIH  USB AC97 KEYB PS2M COM1
[4294675.558000] USB Universal Host Controller Interface driver v2.2
[4294675.559000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801AA USB
[4294675.621000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294675.621000] hub 1-0:1.0: USB hub found
[4294675.796000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294737.781000] drivers/usb/media/spca5xx/spca5xx-core.c: USB SPCA5XX camera found. Type Intel Easy PC Camera CS110 (SPCA508+PB100)




help, anyone?
thanks for your time

---

### Post by az on 2006-02-23
This is a known bug with the spca5xx driver.  You can work around it by compiling a newer version from source:

[https://wiki.ubuntu.com/Spca5xx](https://wiki.ubuntu.com/Spca5xx)

Scroll down and use the alternative howto.  You can become root, as mentioned but you can also just use sudo, like everybody else...

---

