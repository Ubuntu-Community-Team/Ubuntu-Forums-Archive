---
title: "How do I get an HP SCSI scanner to work?"
date: 2008-06-14
forum: Hardware
---

### Post by bwallum on 2008-06-14
I'm nearly bald with this one!

I have an HP 5110C SCSI scanner. Quite an old model but works very nicely in XP. However I am trying to get it to work in Ubuntu 8.04 with the 2.6.24-18 kernel. GolemXIV has very kindly steered me through setting up the SCSI side of things. I am now down to the vagaries of xsane and the inner workings of Ubuntu. I am not an IT wizard.

This is what I get from:```
sudo sane-find-scanner
```(Interestingly without the sudo I get a blank report.) With sudo:-

>  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI processor "HP C5110A 3701" at /dev/sg4
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

This what I get from ```
scanimage -L
```> device `v4l:/dev/video0' is a Noname DEF-299A Camera virtual deviceThis is of course, my web cam.```
lsscsi
```yields > [0:0:4:0]    process HP       C5110A           3701  -       
[1:0:0:0]    disk    Generic  USB SD Reader    1.00  /dev/sda
[1:0:0:1]    disk    Generic  USB CF Reader    1.01  /dev/sdb
[1:0:0:2]    disk    Generic  USB SM Reader    1.02  /dev/sdc
[1:0:0:3]    disk    Generic  USB MS Reader    1.03  /dev/sdd
[2:0:0:0]    disk    ATA      WDC WD800JB-00JJ 05.0  /dev/sde
[3:0:0:0]    cd/dvd  JLMS     XJ-HD163         GH5Y  /dev/scd0

I have a usb hub and a hard drive and a cdrom drive, no surprises there, but why is the scanner only seen as a process?```
cat /etc/sane.d/hp.conf
```gives> scsi HP
# Uncomment the following if you have "Error during device I/O" on SCSI
#   option dumb-read
#
# The usual place for a SCSI-scanner on Linux
/dev/scanner
#
# USB-scanners supported by the hp-backend
# HP ScanJet 4100C
usb 0x03f0 0x0101
# HP ScanJet 5200C
usb 0x03f0 0x0401
# HP ScanJet 62X0C
usb 0x03f0 0x0201
# HP ScanJet 63X0C
usb 0x03f0 0x0601
#
# Uncomment the following if your scanner is connected by USB,
# but you are not using libusb
# /dev/usb/scanner0
#   option connect-device

So how do I get Ubuntu to see the scanner? It needs some sort of glue to pull it together. Any ideas?

Kind Regards 
Bob

---

### Post by bwallum on 2008-06-15
Please go to:

[http://ubuntuforums.org/showthread.php?t=826722](http://ubuntuforums.org/showthread.php?t=826722)

---

