---
title: "ov518_decomp ?"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by IdoMcFly on 2005-05-02
I'm trying to get my webcam working and in gnomemeeting when I hit detect hardware button I got in dmesg :

Linux video capture interface: v1.00
drivers/usb/media/ov511.c: USB OV518 video device found
drivers/usb/media/ov511.c: Device revision 9
drivers/usb/media/ov511.c: Compression required with OV518...enabling
drivers/usb/media/ov511.c: Sensor is an OV6630
drivers/usb/media/ov511.c: Device at usb-0000:00:02.0-9 registered to minor 0
usbcore: registered new driver ov511
drivers/usb/media/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
drivers/usb/media/ov511.c: No decompressor available

I've read on the net something about ov518_decomp module to load but sudo modprobe ov518_decomp said it does not exist.

What else to try ?

---

### Post by IdoMcFly on 2005-05-03
I've installed ov511-src, how to compile it ?

---

### Post by foolsh on 2005-11-13
[http://home.insightbb.com/~foolsh/]("http://home.insightbb.com/~foolsh/")

---

### Post by IdoMcFly on 2005-11-21
I'll try this, thank you!

---

