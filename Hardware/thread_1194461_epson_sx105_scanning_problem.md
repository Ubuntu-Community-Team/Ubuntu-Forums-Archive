---
title: "epson sx105 scanning problem"
date: 2009-06-22
forum: Hardware
---

### Post by skris on 2009-06-22
I have a multi-function Epson Stylus sx105 printer-scanner-copier. I have tried to install the official drivers found in avasys.jp website.
I have followed many of the advices found on forums and other places (Yes I can google:) E.g.: [http://ohioloco.ubuntuforums.org/showthread.php?t=1021989](http://ohioloco.ubuntuforums.org/showthread.php?t=1021989) 

Printer works, but I can not scan.

I have tried it with Ubuntu 8.10 - no success.
Now I have upgraded to 9.04 - no success

I have installed following driver: sudo dpkg --install ./iscan_2.20.0-6.ltdl7_i386.deb

sane-find-scanner output:
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [SEIKO EPSON], product=0x0841 [USB MFP]) at libusb:005:003
found USB scanner (vendor=0x08ff, product=0x2580 [Fingerprint Sensor]) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

(The other device is a fingerprint reader)

scanimage -L:
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

iscan frontend does not find the scanner
Xsane does not find the scanner

This is really strange, because everybody reported that this driver works fine with Ubuntu 8.10 and 9.04

Hardware: Lenovo 3000 N200

Anyone a guess?

---

### Post by gemma.laming on 2009-08-25
Hi everyone :(,

I had fondly imagined ALL epson scanners to be Linux friendly.

So far I am extremely disappointed.  Am I to buy another scanner?  With the floods of answers to this problem, it seems this is my only course of action.  

I feel badly let down.  I bought the Epson SX105 especially because I heard that the scanner would work with Linux - but it seems it will not?  

I need a scanner for graphics that I use in my business.  

Yours, sadly, Gem

---

