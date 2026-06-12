---
title: "Scanning with Lexmark x1150"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by narehart on 2007-09-25
I'm almost positive that this isn't possible but I thought I'd ask anyway. Does anyone know of a way to get the scanner working on the Lexmark x1150 in Ubuntu Feisty Fawn?

I've gotten my printer to work by extracting the driver from the z600 Red Hat file on Lexmark's site but I don't think that contained a driver for the scanner.

Any help would be greatly appreciated. Thanks!

---

### Post by linuxwizard on 2007-09-25
According to this it will work but not very well. Need to install Sane.
[http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK](http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK)

minimal means that the device is detected and scans at least in one mode. But the quality is bad or important features won't work.

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by narehart on 2007-09-26
Ah, I'm such an idiot.  I didn't even try xsane image scanner or should I say I didn't realize it was there. Thanks for your response.

---

### Post by ishwar on 2007-10-24
hi.. i hope u cld suggest me sth!!

did u try xsane.. what was the result.. i have xsane and lexmark x1270 all in one printer.. well with a scanner.. i made the printer work, in the same way how u managed to get the rpm etc... so now i found that xsane is not detecting my drives..or wat so ever .. i dont know exactly whats the problem!! 

i have pasted few outputs of mine cld u pls have a luk .. i have no idea how to work in xsane backend.. or wat ever!! sorry for many wat evers!! i m frustrated .. 

$lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 006: ID 043d:00ff Lexmark International, Inc.
Bus 002 Device 005: ID 043d:007d Lexmark International, Inc.
Bus 002 Device 004: ID 043d:007a Lexmark International, Inc.
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
$ scanimage -d test -T
scanimage: scanning image of size 157x196 pixels at 8 bits/pixel
scanimage: acquiring gray frame, 8 bits/sample
scanimage: reading one scanline, 157 bytes...   PASS
scanimage: reading one byte...          PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...    PASS
scanimage: stepped read, 32 bytes...    PASS
scanimage: stepped read, 64 bytes...    PASS
scanimage: stepped read, 128 bytes...   PASS
scanimage: stepped read, 256 bytes...   PASS
scanimage: stepped read, 255 bytes...   PASS
scanimage: stepped read, 127 bytes...   PASS
scanimage: stepped read, 63 bytes...    PASS
scanimage: stepped read, 31 bytes...    PASS
scanimage: stepped read, 15 bytes...    PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS

$sudo sane-find-scanner

 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x043d, product=0x007d, chip=rts8858c) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

