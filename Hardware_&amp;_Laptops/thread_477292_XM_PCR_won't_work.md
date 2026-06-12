---
title: "XM PCR won't work"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by timcredible on 2007-06-18
It works on other distros.  Can someone tell me what's happening here?  i'm using 7.04, feisty.  thanks.

I get this in dmesg when plugging it in:

[ 2873.304513] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 2873.483557] usb 2-1: configuration #1 chosen from 1 choice
[ 2873.486525] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 2873.486532] drivers/usb/serial/ftdi_sio.c: Detected FT8U232AM
[ 2873.486657] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB6
[ 2877.135775] usb 2-1: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
[ 2877.139290] ftdi_sio ttyUSB6: FTDI USB Serial Device converter now disconnected from ttyUSB6
[ 2877.139308] ftdi_sio 2-1:1.0: device disconnected

---

### Post by timcredible on 2007-06-18
well, this was odd - i checked that brltty program (something about braille), and uninstalled it, and now the xmpcr works.

---

### Post by icsfsedod on 2007-11-23
What are you using in Ubuntu to run the XMPCR?  Decided to try to get mine connected and seems everyone uses the OpenXM library, but it's nowhere to be found.

Thanks

---

