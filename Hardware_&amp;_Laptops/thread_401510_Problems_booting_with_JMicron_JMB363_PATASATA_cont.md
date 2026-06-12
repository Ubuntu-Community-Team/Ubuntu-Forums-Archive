---
title: "Problems booting with JMicron JMB363 PATA/SATA controller"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by davidbrucehughes on 2007-04-04
I am having difficulty booting Feisty Fawn 7.04 beta on a machine with a JMicron JMB363 PATA and SATA controller on an ASUS P5-VM motherboard with 2 GB RAM. If I turn off quiet I get a screenful of text that goes by **really** fast, then a display with some blue text and checkmarks next to several items. The File System check never comes on, and the boot hangs. 

I've tried posting this on some other support forums, but did not get any useful answers. Could it be the SATA controller is incompatible?

thanks,
DBH

---

### Post by davidbrucehughes on 2007-04-04
The last messages on the boot console are:

drivers/usb/input/hid-core.c: v.2.6:USB HID core driver
end_request: I/O error, dev fd0, sector0

---

### Post by robenroute on 2007-04-04
> **davidbrucehughes said:**
> ..... Could it be the SATA controller is incompatible?

thanks,
DBH

There have been numerous problems with JMicron's PATA/IDE controller. According to their website, they've released new microcode that's supposed to be integrated into the BIOS code of the respective motherboard. I know a few motherboard manufacturers have already released updated BIOS code; you might want to check yours and flash the latest BIOS available.

---

### Post by davidbrucehughes on 2007-04-04
Hmmm. Already burned the latest BIOS code when I set up the board. I've tried several different distros and get similar errors. The only fix I've found is to install a PATA (IDE) drive and run the thing in compatibility mode. (It's not gonna happen. I love the performance too much to give it up.)

---

