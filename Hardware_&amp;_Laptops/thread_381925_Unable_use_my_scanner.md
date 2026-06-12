---
title: "Unable use my scanner"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by brazz43 on 2007-03-11
Hi,
I have an old Microtek ScanMaker X6 USB and under Mandriva it works fine.
I am unable to use xsane because the scanner is not detected by sane.
Here are the facts:
--------------------------------------------------------------------------------------------------
when I tap
# ls -la /proc/bus/usb/001/004

I have
crw-rw-r-- 1 root scanner 189, 3 2007-03-11 15:07 /proc/bus/usb/001/004

and when I tap
# lsusb

I have
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 05da:0099 Microtek International, Inc. ScanMaker X6/X6U
Bus 001 Device 003: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 001 Device 001: ID 0000:0000 

so, I think the system detect the scanner
--------------------------------------------------------------------------------------------------
when I tap
# sane-find-scanner

I have
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI scanner " Scanner 636A4 1.40" at /dev/sg1
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

found USB scanner (vendor=0x05da, product=0x0099) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

this is OK
--------------------------------------------------------------------------------------------------
but if I tap
# scanimage -L

I have
device `v4l:/dev/video0' is a Noname BT848A video ( *** UNKNOWN/GENE virtual device

and its my TV card ...
--------------------------------------------------------------------------------------------------
And, unfortunatly, if I run xsane, it runs with my TV card too !!! 

Have you some idea ???

---

### Post by apjone on 2007-03-13
have a look at [http://ubuntuforums.org/showthread.php?p=2120055](http://ubuntuforums.org/showthread.php?p=2120055) it may help you

---

