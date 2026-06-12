---
title: "Ubuntu Live cd error"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by subslug on 2006-02-06
I've been trying to run either Ubuntu 5.10 live or Kubuntu 5.10 live to see whether I should wipe out a nice Debian install on my main pc. The problem is I can't even get the live cd to run so I'm not sure how much luck I'll have with the install cd?

I boot up and get to this point "ata(0): applying bridge limits" and that's it. It just stares at me. I've tried most cheat codes although none of them seem to apply to my specific hardware.

ICH5 SATA controller and a SATA hard drive and an PATA dvd drive, I'm assuming this controller is what's tricking up Ubuntu??
It's weird because I'm able to install almost every 2.6 kernel Linux I've ever tried on this machine without a single problem but Ubuntu refuses. I really dig Ubuntu too, it works great on my laptop.
Anywho.......someone know something I could try?

```
lspci
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub
 Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (re
v 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI
Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI
Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCIController #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCIController #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:
```

---

