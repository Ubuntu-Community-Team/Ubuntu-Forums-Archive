---
title: "scanner hp 2003c"
date: 2006-05-03
forum: Hardware &amp; Laptops
---

### Post by EarlGrey on 2006-05-03
Hello,

I am a beginner in Linux (month and a bit) and the only piece of hardware can't cope with is my scanner. Some sites say it should be supported, some that it shouldn't and I am getting lost.

Do you have any advice? How to implement it, if it is supported?

Tanks alot,
EarlGrey

---

### Post by Zimmer on 2006-05-03
A google search for your hp 2003c did not turn up any scanners, other than the  2300c.  Was that a typo on your part?
If your scanner is a 2300c then according to SANE it is supported.
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=2300c&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=2300c&bus=any&v=&p=)
So plug it in and go to Applications >Graphics>XSane Image Scanning program
and see what happens....

---

### Post by EarlGrey on 2006-05-03
Yes, sorry, my fault, it is 2300c not 2003c. However, If I run Xsane image scanning program, no scanner is found.

When i run sane-find-scanner, it returns

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0901 [hp scanjet scanner], chip=GL646) at libusb:002:002
#Your USB scanner was (probably) detected. It may or may not be supported by
#SANE. Try scanimage -L and read the backend's manpage.

---

### Post by Metthyn on 2006-05-03
i have hp2300c too and the same problem. 

'lsusb' gives me that:
> 
metin@mettdev:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 03f0:0901 Hewlett-Packard ScanJet 2300c
Bus 001 Device 001: ID 0000:0000


and 'sane-find-scanner' as root:
> 
root@mettdev:/home/metin# sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x046d, product=0x0850 [Camera]) at libusb:002:002
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0901 [hp scanjet scanner], chip=GL646_HP) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


but when i want to choose my scanner, kooka or xsane just list my logitech webcam. 
any idea?

---

### Post by Zimmer on 2006-05-03
It would appear, through following the links on the SANE site to the backend for this scanner that it has been included since version 1.0.16 and Ubuntu 5.10 is currently using 1.0.15. So that might explain the problem. How you get the backend in the meantime is something I cannot help you with at present..sorry. Unless, of course , it is contained in the current libsane-extras package on Synaptic. Worth a shot...

---

### Post by Simon Bridge on 2006-06-11
You have to get the source offa the sane website or one of the mirrors - then compile it. Works nice - only it seems to get erased if you upgrade everything.

Which one does dapper come with?

You should be aware that it dosn't work very well - the scan head keeps hitting then end and sticking, especially when scanning anything in color. Havn't figured a workaround yet.

---

