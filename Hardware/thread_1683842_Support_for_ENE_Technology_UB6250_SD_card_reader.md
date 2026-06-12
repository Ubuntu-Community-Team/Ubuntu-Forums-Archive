---
title: "Support for ENE Technology UB6250 SD card reader"
date: 2011-02-08
forum: Hardware
---

### Post by pracrichard on 2011-02-08
I have an MSI CR620 bought from Novatech (UK) It has an ENE Technology UB6250 SD card reader which I cannot get to work. (everything else about the machine is great.) The card is identified by lsusb as:

Bus 001 Device 004: ID 0cf2:6250 ENE Technology, Inc

Looking on older posts (at lease 8 months old)  I find this card was not supported at that time. it seems there is code available but at that time nobody had compiled it into a driver that newbies to linux like me can install. 

How can I find such a driver once someone has compiled it. Has this now been done?

Here is a link to the raw code which I think came from ENE via MSI

[https://lists.one-eyed-alien.net/pipermail/usb-storage/2010-April/005198.html](https://lists.one-eyed-alien.net/pipermail/usb-storage/2010-April/005198.html)

I will be very grateful to receive this and will publicise our success.

---

### Post by misanthropist on 2011-02-11
A fix has been released for 11.4 according to [ Bug #530277 ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277"). So you should be able to wait a couple of months for the next release or hopefully some kernel backports will be made available.

In the meantime on the odd occasions I need to access flash cards I'm using an XP image in virtualbox. Not really a convenient solution but better than nothing.

The webcam on the MSI CR620 also seems to be problematic but I use webcams that even less often than flash cards so it isn't much of an annoyance to me.

---

### Post by pracrichard on 2011-02-12
Hi Misanthropist,

Many thanks for this good news I will wait for Ubuntu 11. Meantime I will have to continue plugging my camera lead into a USB port. I can use the camera as a card reader even if the file came from elsewhere. :smile:

As far as the webcam is concerned it works - sometimes - I seem to have to boot with it turned on but as there is no light until I have booted this is a bit hit and miss :(.

Richard

---

