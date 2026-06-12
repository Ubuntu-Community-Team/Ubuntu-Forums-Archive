---
title: "Sane is not finding my scanner"
date: 2009-05-02
forum: Hardware
---

### Post by mousestalker on 2009-05-02
I have a Hp Officejet 6500. I prefer to use it as a scanner only as I have a very nice laser printer. It is connected via USB directly to my computer.

My OS is 64 bit Jaunty.

lsusb returns the following:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:4512 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 06a3:0728 Saitek PLC 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c041 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sane-find-scanner returns the following:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x4512 [Officejet 6500 E709n]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

scanimage -L returns the following:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

hp-check shows me this (redacted):

INSTALLED CUPS PRINTER QUEUES

Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: usb://HP/Officejet%206500%20E709n?serial=MY9272185S056Q
PPD: /etc/cups/ppd/Officejet-6500-E709n.ppd
PPD Description: HP Officejet 6500 e709n hpijs, 3.9.2
Printer status: printer Officejet-6500-E709n is idle.  enabled since Sat 02 May 2009 09:26:59 PM EDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

What does all that mean, and is there anyway for me to resume scanning?


**Problem solved** by a brute force approach. I removed HPLIP. I then downloaded the latest and greatest version from HP. The release notes showed added support for my printer (Officejet 6500). After crashing several times, I added the complete set of Python-devel apps to my computer. One of them must have been what HPLIP wanted as it installed flawlessly after that. With the latest  version of HPLIP installed, Ubuntu found my printer/scanner and I am now up and running again.

I hope that this helps anyone else with this problem.

---

