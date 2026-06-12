---
title: "HP2050 - banging head against the wall"
date: 2010-12-21
forum: Hardware
---

### Post by sleepingdragon on 2010-12-21
I've seen a few similar threads about the HP2050 MFP. It's a nice printer, shame it can't scan.

I've tried everything with the 3.10.6 and 3.10.9 versions of hplip, including building my own .deb files for installs - all for nothing.

The most annoying bit so far? sane-find-scanner can actually see the scanner, but nothing else does!
> 
$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x8711 [Deskjet 2050 J510 series]) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


---

### Post by sleepingdragon on 2011-08-03
Solved with HP driver 3.11.1

---

### Post by buskerika on 2012-03-16
I've got the same problem with exactly the same All-in-one printer but your solution upgrading to hplip 3.11.1 doesn't work for me 'cus I'm using Ubuntu Lucid 10.04.
Running sane-find-scanner give me the same output as you.

Have you seen any alternative solutions since your last comment?

Anyone else out there who can help me?

---

### Post by buskerika on 2012-03-17
I've got the answer on:
[http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html") where you get all the solutions to problems with HP-printers and scanners.
It-s working perfectly now!!

---

