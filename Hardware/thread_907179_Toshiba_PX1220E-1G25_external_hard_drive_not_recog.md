---
title: "Toshiba PX1220E-1G25 external hard drive not recognized"
date: 2008-09-01
forum: Hardware
---

### Post by eldar40k on 2008-09-01
Hi, I've just bought the above hard drive, and it is not recognized under linux (Ubuntu 8.04). It works fine under Windows XP.
Is there any way to get it work?

Symptoms:

    * The following message is visible in dmesg: usb 5-8: new high speed USB device using ehci_hcd and address 4

This message is repeated from time to time using different address number.

    * The disk does not show up under the lsusb and fdisk -l commands.


According to its manual, this hdd does not have a built-in password application, so this should not be a problem.

Any ideas?

---

### Post by egynew on 2009-07-12
Hi, I have have just run into this problem but with a different model. Thanks to an advice on [http://www.danielschneller.com/2007/04/something-to-know-about-toshiba.html](http://www.danielschneller.com/2007/04/something-to-know-about-toshiba.html) I looked at the manual and sure enough on page 5 it says that sometimes you will need to plug in the 2 connectors in the USB cable into the computer. It is now detected and I think is working properly. Good luck and if my solution does not apply to you then start by reading the manual.

---

