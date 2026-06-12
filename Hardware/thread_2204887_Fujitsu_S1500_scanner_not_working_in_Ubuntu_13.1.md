---
title: "Fujitsu S1500 scanner not working in Ubuntu 13.1"
date: 2014-02-10
forum: Hardware
---

### Post by James_Drummond on 2014-02-10
Just moving over to Ubuntu and unable to get my S1500 scanner to work.  Read a lot of stuff about SANE and how to get it to work, but not been successful.

SYSTEM:
jim@jimHPUbuntu1:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

TESTING:
jim@jimHPUbuntu1:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 009: ID 04c5:11a2 Fujitsu, Ltd 
Bus 003 Device 002: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 003 Device 006: ID 0a5c:21f1 Broadcom Corp. HP Portable Bumble Bee
Bus 003 Device 005: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

CONCLUSION:  Scanner is connected

TESTING:
sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x8000 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x8008 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc52b at 003:003: Access denied (insufficient permissions)
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not open USB device 0x046d/0x082d at 003:002: Access denied (insufficient permissions)
could not open USB device 0x0a5c/0x21f1 at 003:006: Access denied (insufficient permissions)
could not open USB device 0x0bda/0x0184 at 003:005: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

CONCLUSION: Could be a permissions problem, but note that Bus 003 Device 009: is missing from the Access Denied errors

TESTING:
im@jimHPUbuntu1:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x0a5c [Broadcom Corp], product=0x21f1 [BCM20702A0]) at libusb:003:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


CONCLUSION:  The Broadcom is not a scanner - Fujitsu is still missing.
FURTHER:  If I unplug the scanner the Pipe errors go away
I have got the fujitsu,conf file and it does have the S1500 scanner with the right Id uncommented.

Any help appreciated.

---

### Post by chorca on 2014-04-11
I'm having the same issue with my S1500 with 13.04. I get the "pipe error" when trying to get the scanner to detect and it does not seem to appear in any software, although dmesg sees it as the device it is.

I installed xsane and it seemed to detect it and work with that, so maybe give it a shot (and if permissions problems, run as root or change permissions to the scanner)

---

