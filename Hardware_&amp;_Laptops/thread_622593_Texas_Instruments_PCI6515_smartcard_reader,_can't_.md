---
title: "Texas Instruments PCI6515 smartcard reader, can't find a driver anywhere."
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by Phoenix on 2007-11-24
If you have a Dell Latitude D610 (or many others from the Dell Latitude series) you may have a smartcard reader on your laptop. If so you probably have a Texas Instruments PCI 6515 smartcard reader which appears like this when "lspci" is entered into the terminal
```
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller

```

I'm wonderinf ig anyone here has managed to get that card running? After googling it for a while I realized that I don't see a driver for this card anywhere, despite it being a relatively widespread piece of equipment apparently. Does anybody have more information on this?

Thanks,
Phoenix

---

### Post by Luna.jp on 2008-04-23
I am going to bump this thread.

The D610 is great and many sections of the DoD used it and are now selling it. Mostly DoD personnel purchase them. I snagged a few up and I have been trying for awhile to get the SmartCard reader so I can hook it up to the DoD network with Ubuntu.

Here is a reference that I tired: [http://ubuntuforums.org/showthread.php?t=457084](http://ubuntuforums.org/showthread.php?t=457084)

And I have also read here: [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

But nothing about the **PCI6515** has come up.
Anyone else have any luck or can point me ( us ) in the right direction?

```
luna@dellnix:~$ pcsc_scan
PC/SC device scanner
V 1.4.9 (c) 2001-2006, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.2
Scanning present readers
Waiting for the first reader...
```

---

