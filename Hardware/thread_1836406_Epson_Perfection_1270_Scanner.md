---
title: "Epson Perfection 1270 Scanner"
date: 2011-08-31
forum: Hardware
---

### Post by Lexus45 on 2011-08-31
Hello all.
I tried a plenty of advice and this scanenr still doesn't work.

What I understood, in a nutshell:
- this scanner uses sane-snapscan backend (/etc/sane.d/snapscan.conf)
- I must use the Esfw3e.bin file from a Windows-driver
- I must add "# perfection 1270 \ usb 0x04b8 0x0120" to the /etc/sane.d/snapscan.conf

In fact, this is the same what is recommended to do here: [https://wiki.archlinux.org/index.php/USB_Scanner_Support#Epson_Perfection_1270](https://wiki.archlinux.org/index.php/USB_Scanner_Support#Epson_Perfection_1270)

I took the Esfw3e.bin from a Win-driver. I added the "firmware ..." line and "# perfection 1270 \ usb 0x04b8 0x0120" to the /etc/sane.d/snapscan.conf.
I played with permissions/chmod of Esfw3e.bin and of /dev/bus/usb/001/00X - the scanner device. Nothing helped.

I tried starting xsane and simple-scan from sudo and without it. Sometimes the output of simple-scan was that "scanenr is warming up, wait 23 seconds ... " and then - 
```
(simple-scan:3302): WARNING **: Unable to start device: Error during device I/O
```But the scanner still doesn't work.

Xsane shows the warning that the are no devices available.


I tried to set the scanner up for 3 hours yesterday and 3 hours today, but all in vain.


One more interesting detail, is that here - [http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON) - we see the Perfection 1270 scanner, and they say it uses snapscan backend.

When we follow the link of snapscan - [http://www.sane-project.org/man/sane-snapscan.5.html](http://www.sane-project.org/man/sane-snapscan.5.html) - we DO NOT see the Perfection 1270 among supported devices.

The distribution is Ubuntu 10.10
sane   1.0.14-9
sane-utils   1.0.21-2ubuntu2

I don't know what to do and how to make it work.

Best regards, Lexus45

---

### Post by Lexus45 on 2011-08-31
The clients bought Mustek BearPaw 2400 CU Plus II.

Works fine :-)

The thred may be deleted.

---

