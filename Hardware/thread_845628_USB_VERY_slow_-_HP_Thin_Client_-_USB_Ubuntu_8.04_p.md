---
title: "USB VERY slow - HP Thin Client - USB Ubuntu 8.04 persistent install"
date: 2008-06-30
forum: Hardware
---

### Post by oscarFrance on 2008-06-30
Hi, I've searched many way to resolve my problem without success...
I hope someone will give me a clue.

I'm using a HP Thin client T5725 (fanless computer).
I wanted to use Ubuntu instead of the old default debian installed on the internal flash (512MO).

I followed this tutorial:
[http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd](http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd)

with a 16 GO Usb stick.

Now, I can launch Ubuntu, but it's VERRRRY SLOOOWWWW!
The same USB Stick on another computer launch with no problem and is fast enough.

So I think that the USB controller of the T5725 is not correctly recognized by Ubuntu but I don't know what to do.

I've seen many websites. They all say that the T5725 has a USB 2.0 controller; so It should be fast enough.

a lspci gives me 3 controllers:
00:03.0 Silicon Integrated Systems [SiS] USB 1.1 controller
00:03.1 Silicon Integrated Systems [SiS] USB 1.1 controller
00:03.2 Silicon Integrated Systems [SiS] USB 2.0 controller

What can I do to know which one is in use and how to activate the third one?


Thank you very much in advance for your help.

Best regards,
Oscar FRANCOIS

---

