---
title: "Connected second scanner, now unable to scan"
date: 2012-04-08
forum: Hardware
---

### Post by JonathonO on 2012-04-08
I have been using an HP 2100c flatbed scanner without issue for some time on Ubuntu 10.04. I recently connected an HP Deskjet F4180, and Ubuntu saw both devices without issue and installed them. The problem is that now Simple Scan is not able to connect to any scanner. Sane is able to see both scanners or just the HP when connected. The error give in the GUI is "No scanners available. Please connect a scanner." I am sometimes able to get it to work by selecting the scanner after attempting to first scan, but now there is no scanner listed in the drop down menu.
The output when I run the program from the command line is:
```
** (simple-scan:30982): WARNING **: No scan device available
```

```
/dev/bus/usb$ sane-find-scanner
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0505 [HP ScanJet 2100C]) at libusb:008:002
found USB scanner (vendor=0x03f0 [HP], product=0x7e04 [Deskjet F4100 series]) at libusb:005:005
```

How can I remove the HP? I wanted it for a color printer but will settle for just getting the scanner working again. Where is the configuration file for Simple-Scan? I installed xsane but that program just hangs at "scanning for devices" when loading and then outputs "no devices available". After I unplug the printer:
```
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0505 [HP ScanJet 2100C]) at libusb:008:002

```
I just get the original scanner. Why is Simple Scan unable to see it?

---

### Post by JonathonO on 2012-04-09
I opened Synaptic and selected Simple-Scan, XSane, and Sane for complete removal, applied and then reinstalled the packages. It is working again.

---

### Post by JonathonO on 2012-04-09
> **JonathonO said:**
> I opened Synaptic and selected Simple-Scan, XSane, and Sane for complete removal, applied and then reinstalled the packages. It is working again.

Spoke too soon. Simple-scan hung on exit and went back to being unable to detect the scanner.

---

