---
title: "usb error -71... drive dead?"
date: 2008-12-30
forum: Hardware
---

### Post by allspiritseve on 2008-12-30
Hi all...

I have a Western Digital passport external hard drive. Earlier today, the drive disappeared suddenly and I was not able to get it to mount again. I tried the drive in windows on my girlfriend's laptop, and it said the drive had malfunctioned. Is there something I can do to get Ubuntu to recognize the drive?  It still spins up, but doesn't get mounted and doesn't show up in fdisk -l or lsusb.

Dmesg contains this:
> [  356.124087] usb 2-1: device descriptor read/64, error -71
[  356.340092] usb 2-1: new full speed USB device using uhci_hcd and address 12
[  356.748093] usb 2-1: device not accepting address 12, error -71
[  356.860086] usb 2-1: new full speed USB device using uhci_hcd and address 13
[  357.268083] usb 2-1: device not accepting address 13, error -71
[  357.268486] hub 2-0:1.0: unable to enumerate USB device on port 1

Any help would be much appreciated.

---

### Post by cariboo on 2008-12-30
WD has a three yerar warranty on their drive, at least here in Canada. Go [here]("http://websupport.wdc.com/warranty/serialinput.asp?aspsid=339697458&custtype=end&requesttype=warranty&lang=en"), to see if your drive is still under warranty, if it is get an RMA and get a replacement.

Jim

---

### Post by allspiritseve on 2008-12-30
Yeah, I've done that for internal drives before... you think its for sure dead though?

---

### Post by -=-+ w1r1zu +-=- on 2008-12-30
If have those Error messages too after booting and on shutting down.

THe only things that are connect to my USB HUB are Bluetooth and HP 1280 printer.

---

