---
title: "Being driven insane trying to install new sane backends"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by mikemain on 2006-01-23
I've been trying to get my LiDE 60 scanner to work for some time now and SANE has  just started to include it in their new backend.  As a Linux neophyte I have some dumb questions:

What directory am I supposed to extract the file to?
The instructions from SANE are: 

Quick install:
==============

./configure
make
make install

man sane

What does this mean?  Typing these things at the command line don't help me, except for man sane but the information contained in that is even more confusing.

The scanner is detected with sane-find-scanner but not scanimage -L so it is just a backend problem.  This is seriously driving me bananas.

---

### Post by tico on 2006-03-25
I'm trying to get my Lide 50 to work. If I type sane-find-scanner, I get:

> # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04a9 [Canon], product=0x2213 [CanoScan], chip=GL841) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

If I type scanimage -L, I get:

> No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

I've already followed the instructions to install the newer backend (1.0.17). What's going on? Does anybody know how to fix this?

TIA

---

### Post by bluetoad on 2006-04-03
I have posted an answer to Tico's problem  in 

[http://www.ubuntuforums.org/showthread.php?p=887161](http://www.ubuntuforums.org/showthread.php?p=887161)

---

