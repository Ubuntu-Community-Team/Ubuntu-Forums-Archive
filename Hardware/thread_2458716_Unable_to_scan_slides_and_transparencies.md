---
title: "Unable to scan slides and transparencies"
date: 2021-03-03
forum: Hardware
---

### Post by Randyman99 on 2021-03-03
I have an HP ScanJet 4890 flatbed scanner from 2006. It's been supplanted for normal scans by all-in-one-printers several times since then, but I still have it around because it also has a secondary lamp in the lid, and has film trays for 35 mm film strips, 35 mm slides, medium format film strips, and even 4x5 film. Scanning transparencies necessitates an overhead lamp to shine through the transparency to the scan head. I have both 35 film film negatives and 4x5 transparencies that I would now like to scan.

Unfortunately, SANE and the other software I've tried for Ubuntu can recognize it and scan opaque documents and images, but not transparencies. The Windows software that came with the scanner is no longer functional because it depended on third party software which is obsolete, so I couldn't even use it in a Windows system (I have an old computer with XP on it just for such contingencies). HP makes a product HPLIP (HP Linux Imaging and Printing), but I think this is just a backend for interfacing with SANE, so I don't know that that will solve my problem. I ran hp-setup, but it wasn't able to recognize the USB scanner, even when I input the USB bus:device numbers manually, which does show up when I run:

```
$lsusb
Bus 002 Device 004: ID 03f0:1b05 HP, Inc ScanJet 4850C/4890C
```

There are two third-party (for cost) software applications I'm aware of. SilverFast doesn't have a Linux version, but I downloaded the Windows 7 demo version, and installed it and ran it in Wine. Although I downloaded it specifically for my HP 4890 scanner, it doesn't recognize the scanner on the USB bus. I'm stuck on this one.

The second third-party software is Vuescan, which does make a Linux version. I downloaded and installed the demo version, and ran it. It recognized my scanner as a 4850 rather than a 4890. It turned the transparency lamp on, but wouldn't scan. Well, that's something. I have been in communication with the company, and they made some beta versions for me, and we've gotten the application to recognize the scanner as a 4890 and move the transparency lamp with the scanning head, but the image is washed out, and we can't seem to solve that problem for two weeks now.

I'm wondering if anyone else has had any experience scanning transparencies in Ubuntu, with this or any other scanner, and how they've done it.

---

### Post by TheFu on 2021-03-04
I have a $99 usb negative-slide scanner. It came with winxp drivers only. The quality is what you'd expect from a $99 scanner fro 2007.

Sane doesn't know what to do with it, but v4l2 does.  There is a /dev/video0 device. **giuvcview** opens it and shows the output. Taking a snapshot works fine.  The negatives need processing to positive. I use imagemagick for that.

Before the dedicated slide/negative scanner, had an epson flatscreen. Never got it working with slides even with Windows.  For normal scanning, I use an all-in-one with a sheet feeder. It is only used to scan and fax, never print.

---

