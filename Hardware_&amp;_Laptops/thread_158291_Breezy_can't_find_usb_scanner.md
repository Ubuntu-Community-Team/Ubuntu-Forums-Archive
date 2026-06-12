---
title: "Breezy can't find usb scanner"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by Mark_in_Hollywood on 2006-04-10
Xsane in Sane and I'm not sane, but:

mark@lexington:~$ lsusb
Bus 001 Device 005: ID 03f0:0105 Hewlett-Packard ScanJet 4200c

 sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the result is different from what you expected, first make sure your scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that you have loaded a SCSI driver for your SCSI adapter. Also you need support for SCSI Generic (sg) in your operating system.

  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x03f0, product=0x0105) at libusb:001:005

  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

mark@lexington:~$  scanimage -L

No scanners were identified. If you were expecting something different, check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool 

From [http://www.xsane.org/](http://www.xsane.org/)

Backend: hp4200 (1.0-2, NEW!)

Link(s): [http://hp4200-backend.sourceforge.net](http://hp4200-backend.sourceforge.net)
Manual page: sane-hp4200
Manufacturer 	Model 	Interface 	Status 	Comment
Hewlett-Packard
ScanJet 4200C 	USB 	basic 	8bpp color, 75/150/300/600 dpi only
ScanJet 4200Cxi 	USB 	basic 	8bpp color, 75/150/300/600 dpi only
ScanJet 4200Cse 	USB 	basic 	8bpp color, 75/150/300/600 dpi only

So the backend is up-to-date.

[http://alioth.debian.org/project/shownotes.php?release_id=660](http://alioth.debian.org/project/shownotes.php?release_id=660)

Shows backends, but I am too newbee to know what to do. When I tried to download the:

sane-backends-1.0.17.tar.gz

FF download manager asked if I wanted "open with archive manager". I don't know if that's correct or not. 

Anybody have a clue?

---

### Post by Mark_in_Hollywood on 2006-04-11
Please ignore the previous post. By having Synaptic show me the installed libraries, etc., Synaptic found there were newer versions, downloaded and installed them.

VOILA

I'm no longer in Sane/Xsane, I'm SANE, I'm a real gone daddy.

---

