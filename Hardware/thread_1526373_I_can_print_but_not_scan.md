---
title: "I can print but not scan"
date: 2010-07-07
forum: Hardware
---

### Post by malfindin on 2010-07-07
Ubuntu 10.04 i386

I have a HP 1200 Laserjet Printer/Scanner and it prints fine, but when you try to scan using Xsane or Simple Scan. It says "scanner not detected".

It did however scan and print the day I set it up. I believe the issue occurred after one of the many kernel updates.

I have no idea how to diagnose or fix this kind of issue, could someone please help?

~malfindin

---

### Post by acidbits on 2010-07-08
Same thing happens to me with an HP 3030. I used it a lot for scanning (gscan2pdf, xsane, scanimage, ...) Now scanner doesn't works. Scanimage says:


```
acid@home:~$ sudo scanimage -L
device `hpaio:/usb/hp_LaserJet_3030?serial=00CNBF110672' is a Hewlett-Packard hp_LaserJet_3030 all-in-one

acid@home:~$ sudo scanimage -x 210 -y 297 --mode Gray --resolution 200 >sheet1.pnm
scanimage: open of device hpaio:/usb/hp_LaserJet_3030?serial=00CNBF110672 failed: Error during device I/O
joan@diable:~$
```

IMHO, some sort of update broke it.

Somebody can help?

a.

---

### Post by lidex on 2010-07-08
Is that the PSC 1200? Have a look here:
[http://www.openprinting.org/printer/HP/HP-PSC_1200]("http://www.openprinting.org/printer/HP/HP-PSC_1200")
Or select different printer here:
[http://www.openprinting.org/printers/]("http://www.openprinting.org/printers/")

---

