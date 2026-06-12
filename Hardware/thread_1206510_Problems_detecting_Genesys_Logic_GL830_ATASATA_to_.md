---
title: "Problems detecting Genesys Logic GL830 ATA/SATA to USB adapter"
date: 2009-07-07
forum: Hardware
---

### Post by timofonic on 2009-07-07
Hello.

I'm using Ubuntu 9.04 right now and it runs flawlessly. I installed in few time while browing the internet by the LiveCD, no boring waits and such like in other OSes.

I have a problem with a USB device. I bought some time ago a few cheap ATA/SATA to USB adaptors using the GL830 chip from Genesys Logic. I have no problems at all using them on different hardware, they get recognized easily.

Sadly, this is not the case of Ubuntu 9.04. The following error appears on dmesg:

> 
[ 1516.500060] usb 2-1: new full speed USB device using ohci_hcd and address 2
[ 1516.680064] usb 2-1: device descriptor read/64, error -62
[ 1516.964065] usb 2-1: device descriptor read/64, error -62
[ 1517.244068] usb 2-1: new full speed USB device using ohci_hcd and address 3
[ 1517.424060] usb 2-1: device descriptor read/64, error -62
[ 1517.708058] usb 2-1: device descriptor read/64, error -62
[ 1517.988069] usb 2-1: new full speed USB device using ohci_hcd and address 4
[ 1518.396039] usb 2-1: device not accepting address 4, error -62
[ 1518.572063] usb 2-1: new full speed USB device using ohci_hcd and address 5
[ 1523.592932] usb 2-1: device descriptor read/8, error -110
[ 1528.712148] usb 2-1: device descriptor read/8, error -110
[ 1528.816068] hub 2-0:1.0: unable to enumerate USB device on port 1

This is weird, as this chip is reported as Linux supported by the chip manufacturer (Genesys Logic).

[http://www.genesyslogic.com/_en/product_01_1.php?id=18](http://www.genesyslogic.com/_en/product_01_1.php?id=18)

Please, can anyone help me with this problem? If my economy allows it, I can buy one adapter from some online shop and put the shipping address of some interested developer.

Regards.

---

### Post by shatterblast on 2009-07-07
I don't know if this is the case with your hardware, but sometimes USB adapters rely on a Windows driver to get the 2.0 (or higher) compliance for speed.  Otherwise, it reverts to the 1.1 standard.  On occasion, I have heard or read that it could also be an issue with a main board or processor type.  Specifically, I think of AMD, but that's dependant on the Linux kernel itself maybe.

In that regard, it could help to just try the device on different USB ports.

---

