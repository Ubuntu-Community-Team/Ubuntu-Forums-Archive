---
title: "Installing HP Scanjet 7400c as network scanner"
date: 2016-01-08
forum: Hardware
---

### Post by hollywoodpete on 2016-01-08
I am trying to install an HP ScanJet 7400c scaner as a network scanner. It is supposed to be plug and play on Ubuntu 14.04 but I cant seen to get it recognized. Any help would be appreciated.

lsusb
Bus 001 Device 002: ID 04b8:0030 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:0801 Hewlett-Packard ScanJet 7400c
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo sane-find-scanner
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

---

