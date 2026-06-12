---
title: "Ubuntu and HP Officejet Pro 9025"
date: 2019-04-26
forum: Hardware
---

### Post by farrinux on 2019-04-26
Hello Community

Need a new all in one printer.  Was wondering if anyone in the community has the new HP Officjet Pro 9025.  If so is it working.  Right now I use Ubuntu 16.04 and HPLIP version 3.18.3

---

### Post by Autodave on 2019-04-26
I do NOT have that unit, but I have 3 different printers: 2 inkjets and one laser and they all work fine.  HP printers usually work right out of the box.

---

### Post by brian_p on 2019-04-26
Setting up printing would be no problem at all and very easy. See

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

However, the device itself is not yet supported officially by HPLIP. See

[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

This would make setting up scanning a tad more challenging (but not impossible with advice).

---

### Post by brian_p on 2019-04-26
> **brian_p said:**
> Setting up printing would be no problem at all and very easy. See

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

Scrub that. You are on Ubuntu 16.0; at least 18.04 would be needed for driverless printing. But it is still possible with a traditional queue.

> However, the device itself is not yet supported officially by HPLIP. See

[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

This would make setting up scanning a tad more challenging (but not impossible with advice).

A bit more than a "tad"! :(

---

