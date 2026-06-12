---
title: "usb scanner worked in dapper, not edgy"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by monkotronic on 2006-10-27
my stylus cx7800 all-in-one worked under dapper just fine.  under edgy, i cant get the scanner to work.  i have installed the sane-backends and sane-backends-extras packages.  sane-find-scanner locates it as such:

found USB scanner (vendor=0x04b8 [EPSON], product=0x081f [USB2.0 MFP(Hi-Speed)]) at libusb:004:002

i think the driver is supposed to be epkowa.drc.   whenever i start xsane, it defaults to my haupage tv card as the input.  scanimage -L only lists the hauppage as well and not my scanner.

so:

1. what could i copy over from my dapper install that might get the thing working in edgy?


2.  if that wont work, what is another idea?](*,)


SOLVED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

i copied the /etc/sane.d/epkowa.conf file over  and it works now.  for those who dont have one, mine is provided below:

# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004  Olaf Meeuwissen
#
# See sane-epkowa(5), sane-scsi(5) and sane-usb(5) for details.

# SCSI scanners can be configured simply by listing the path to the
# device.  For example, if your system claims to have a /dev/scanner
# SCSI device, all you have to do is uncomment the following line:
#
#/dev/scanner
#
# In the interest of maintainability, most installations would have
# /dev/scanner sym-linked to the real SCSI scanner device node.
#
# An alternative way that works for many operating systems and is a
# little bit more generic, is to have the backend probe for your SCSI
# scanner with the following configuration command:
#
scsi EPSON

# On systems with libusb, the following line is sufficient to get the
# backend to recognise your USB scanners.  It presumes, however, that
# the scanner---more precisely, it's USB product ID---is known to the
# backend.
# For all USB scanners that are officially supported by this backend,
# this presumption is true.  A list of such scanners can be found in
# sane-epkowa(5).
#
usb

# For any USB scanner not known to the backend (yet), you may, at your
# own peril(!!), force the backend to recognise and use it via libusb.
# You can do so by the following configuration command:
# 
#   usb <USB vendor ID> <USB product ID>
#
# SEIKO EPSON's USB vendor ID is '0x04b8' (without quotes).  In order
# to find the USB product ID, use lsusb(1) or, on Linux systems, peek
# at the information in /proc/bus/usb/devices.
# A sample configuration for the Perfection 1650 (GT-8200), which has
# a product ID of 0x0110, would look as follows:
#
usb 0x04b8 0x081f

# When not accessing your USB scanner via libusb, you may need to use
# one of the configuration commands below or commands that are almost
# the same.  These commands typically access the scanner via a kernel
# scanner module.
#
#usb /dev/usb/scanner0
#usb /dev/usbscanner0
#usb /dev/uscanner0
#
# Linux had a scanner module until version 2.6.2.  As of version 2.6.3
# libusb is your only option.  Linux' scanner module can be loaded via
# the modprobe(8) command like so:
#
#   modprobe scanner vendor=<USB vendor ID> product=<USB product ID>
#
# If the scanner module already knows the vendor and product IDs, you
# do not have to specify them.  If you want to have this done automa-
# tically every time you boot, you can add the above line, except for
# the modprobe command itself, to your /etc/modules file.

# Although not tested with this backend, parallel port scanners should
# be usable.  You can configure them as shown below, but I do not know
# much about the details.  Information is welcome.
#
#pio 0x278
#pio 0x378
#pio 0x3BC

---

### Post by FastZ on 2006-10-31
What about trying to get an HP DeskJet F340 all-in-one printer/scanner/copier to scan under Edgy?    Mine seems to print just fine, it will make copies just fine (by using the scanner on the printer and pressing the Make Copy button on the printer itself) but I cant get it to scan an image.  XSane errors out with the following error when I open it up.

```
Failed to open device 'hpaio:/usb/Deskjet_F300_series?serial=CN65PFF08H04KH': Error during device I/O.
```

---

### Post by mattman on 2006-12-05
I'm having the same problem as FastZ but with an HP 5300. Has anybody found a way to fix this. My scanner worked well in Dapper but not in Edgy. Although I downloaded a trial version of Vuescan and that works but I would rather not pay $40 just to use my scanner occasionally.

---

### Post by therrmann on 2007-01-10
I have the same problem with my Epson cx5200;  it worked wonderfully in Dapper but not in Edgy.  The fix by editing /etc/sane.d/epson.conf,  putting in things like  usb 0x4b8 0x0801 (which is what  sane-find-scanner gave)  does not help.     Tom

---

### Post by dolphinsonar on 2007-01-15
My "Epson CX5400 Printer Scanner" has the same issue, it printed and  scanned in Dapper, but now it prints and does NOT scan in Edgy.  It connects via USB.

---

### Post by UbunT00L on 2007-01-21
monkotronic's suggestion sort of worked for me, here's what I did.

First I had to make sure I had libsane, libsane-extras, and sane-utils installed.  Then I typed "sane-find-scanner" into a terminal to get the following output:

```
home@home:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x046d, product=0x08f0) at libusb:002:002
found USB scanner (vendor=0x04b8 [EPSON], product=0x0808 [USB MFP]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
home@home:~$

```

Looking at the output, I found that the vender code was "0x04b8" and the product code was "0x0808".  I used these codes in place of the ones that monkotronic supplied in his epkowa.conf file, and copied this file to /etc/sane.d/epkowa.conf.  Then I had to add the line "epkowa" to the file /etc/sane.d/dll.conf.  After that, everything worked for me.  Hope this helps someone.

---

### Post by teaker1s on 2007-01-21
for the epson scanner **iscan** from epson

---

### Post by wuxxin on 2007-02-11
I have the same problem, also a multifunction device (printer/scanner) and it looks like an old problem i've had one or two years ago on debian, usblp takes over control of the usbinterface of the device, and other backends like sane cant use it 

Dmesg output when trying this is
```

usb 2-1: usbfs: interface 1 claimed by usblp while 'scanimage' sets config #1

```

The quickfix hack back then was to blacklist usblp for this device, but i think there should be a better way.

---

### Post by lyskerrys on 2007-02-11
It's this kind of fiddling around that you need to do with Linux that has 99.9% decided me to get an iMac next time round.  I changed to Ubuntu because SuSE didn't recognise my hardware, now Ubuntu is doing the same.

IT ISN'T GOOD ENOUGH, GUYS!  Linux will never take off on the desktop if you can't sort this stuff out. :-(

---

